---
title: 訊息偵測器
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: c9d2c47a816e7fd8c5d219009128ed530564b81b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334948"
---
# <a name="message-inspectors"></a>訊息偵測器
這個範例會示範如何實作與設定用戶端和服務訊息偵測器。  
  
 訊息偵測器是一種可在服務模型的用戶端執行階段中使用的擴充性物件，並以程式設計方式或透過組態分派執行階段，因此可在接收訊息之後或傳送訊息之前偵測及變更訊息。  
  
 這個範例會實作基本用戶端和服務的訊息驗證機制，而這個驗證機制會對一組可設定的 XML 結構描述文件驗證傳入的訊息。 請注意，這個範例不會對每個作業驗證訊息。 這個作用則是針對簡化而設計。  
  
## <a name="message-inspector"></a>訊息偵測器  
 用戶端訊息偵測器會實作 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 介面，而服務訊息偵測器會實作 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 介面。 該實作可以從用於兩端的訊息偵測器結合至單一類別。 這個範例就會實作這類結合的訊息偵測器。 對已驗證之傳入和傳出訊息傳遞一組結構描述而建構偵測器，該偵測器並可讓開發人員指定是否要驗證傳入或傳出訊息，以及偵測器是否處於分派或用戶端模式，而這都會影響本主題之後會討論的錯誤處理方式。  
  
```  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 任何服務 (發送器) 偵測器都必須實作兩個 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 方法 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 和 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>。  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 會叫用由發送器當訊息接收、 處理由通道堆疊並指派給服務，但再還原序列化並分派至作業。 如果已加密傳入訊息，在訊息抵達訊息偵測器時就會進行解密。 方法會取得當做參考屬性傳遞的 `request` 訊息，而此參考屬性可讓您根據需要檢查訊息、管理或取代訊息。 傳回值可以是服務將回覆傳回現行訊息時，當做傳遞至 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> 之相互關聯狀態物件使用的任何物件。 在此範例中，<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 會將訊息檢查 (驗證) 委派給私用的本機方法 `ValidateMessageBody`，而且不會傳回任何相互關聯狀態物件。 這個方法會確定不會有無效的訊息傳遞至服務。  
  
```  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> 每當回覆時就會傳送給用戶端，或如果是單向的訊息，在處理內送訊息時，會叫用。 這樣可不管 MEP，都將延伸項目當做已對稱地呼叫。 搭配 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 使用時，會當做參考參數傳遞訊息，並且可檢查、修改或取代訊息。 在此範例中執行的訊息驗證會再次委派給 `ValidMessageBody` 方法，在這裡的驗證錯誤處理方式稍有不同。  
  
 如果是在服務上發生驗證錯誤，`ValidateMessageBody` 方法會擲回 <xref:System.ServiceModel.FaultException> 衍生的例外狀況。 在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 中，這些例外狀況可以放入服務模型基礎結構，在這裡會自動將例外狀況轉換為 SOAP 錯誤，並轉送至用戶端。 在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> 中，例外狀況不可放置在基礎結構中，因為服務擲回的錯誤例外狀況轉換會在呼叫訊息偵測器之前即發生。 因此，下列實作可以攔截已知的 `ReplyValidationFault` 例外狀況，並以明確的錯誤訊息取代回覆訊息。 這個方法可確定服務實作不會傳回無效的訊息。  
  
```  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 用戶端訊息偵測器的運作方法也很類似。 必須從 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 實作的這兩個方法為 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> 和 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>。  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> 當用戶端應用程式或作業格式器編寫訊息時，會叫用。 搭配使用發送器訊息偵測器時，就可以只檢查或完全取代訊息。 在此範例中，偵測器會分派至相同的本機 `ValidateMessageBody` Helper 方法，而這個方法也會用於委派訊息偵測器。  
  
 用戶端和服務驗證 (如建構函式中指定) 之間的行為差異，主要是在用戶端驗證擲回的本機例外狀況會放置在使用者程式碼中，其原因為這些例外狀況是在本機產生，而不是因為服務錯誤所產生。 一般來說，規則為服務發送器偵測器會擲回錯誤，而用戶端偵測器則是擲回例外狀況。  
  
 這個 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> 實作可確定不會將無效的訊息傳送至服務。  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 `AfterReceiveReply` 實作可確定從服務接收的無效訊息不會轉送至用戶端使用者程式碼。  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 此特殊訊息偵測器的中心則為 `ValidateMessageBody` 方法。 若要執行其工作，會包裝驗證的 <xref:System.Xml.XmlReader> 與所傳遞訊息的本文內容子樹狀結構。 將以一組訊息偵測器持有的結構描述來填入讀取器，而且驗證回呼會設定為代理人，也就是與此方法一起定義的 `InspectionValidationHandler`。 若要執行驗證，接著便需要讀取訊息，並多工緩衝處理至以記憶體資料流為基礎的 <xref:System.Xml.XmlDictionaryWriter>。 如果在處理序期間發生驗證錯誤或警告，就會叫用回呼方法。  
  
 如果沒有任何錯誤，就會建構從原始訊息複製屬性和標頭的新訊息，並在記憶體資料流中使用現在驗證的 Infoset (由 <xref:System.Xml.XmlDictionaryReader> 包裝並新增至取代訊息)。  
  
```  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 每次發生結構描述驗證錯誤或警告時，驗證的 `InspectionValidationHandler` 就會呼叫 <xref:System.Xml.XmlReader> 方法。 下列實作只能處理錯誤，而忽略所有警告。  
  
 在第一個考量上，可能可以將驗證 <xref:System.Xml.XmlReader> 插入具有訊息偵測器的訊息，並在處理訊息時進行驗證，而不緩衝處理訊息。 因此，這表示偵測到無效的 XML 節點時，此回呼會在服務模型基礎結構的某個位置或使用者程式碼中擲回驗證例外狀況，因而導致無法預期的行為。 緩衝處理方法會完全保護使用者程式碼不受無效訊息的影響。  
  
 如前所討論，處理常式擲回的例外狀況和用戶端與服務擲回的例外狀況不同。 在服務上，例外狀況是衍生自 <xref:System.ServiceModel.FaultException>，而在用戶端上，例外狀況則是一般自訂例外狀況。  
  
```  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>行為  
 訊息偵測器為用戶端執行階段或分派執行階段的延伸項目。 此類擴充功能會設定為使用*行為*。 行為就是類別，而這個類別會透過變更預設組態或新增延伸項目 (例如訊息偵測器)，來變更服務模型執行階段的行為。  
  
 下列 `SchemaValidationBehavior` 類別是用來將此範例的訊息偵測器新增至用戶端或分派執行階段的行為。 在這兩個例子中，實作都相當基本。 在 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> 和 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> 中，會建立訊息偵測器並新增至相對之執行階段的 <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> 集合中。  
  
```  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
>  此特定行為不會兼做屬性，因此無法以宣告方式新增至服務類型的合約類型。 這是根據設計所做的決策，因為結構描述集合無法載入屬性宣告，而參考至此屬性中額外的組態位置 (例如，應用程式設定) 則表示所建立的組態項目，會與其他服務模型組態不一致。 因此，您只能以命令方式，透過程式碼和服務模型組態延伸項目新增此行為。  
  
## <a name="adding-the-message-inspector-through-configuration"></a>透過組態新增訊息偵測器  
 如需在應用程式組態檔中的端點上設定自訂行為，服務模型會需要實作器建立組態*延伸模組項目*衍生自的類別所代表<xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。 針對如本節所討論之下列延伸項目所示的延伸項目，此延伸項目必須新增至服務模型的組態區段。  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 延伸項目可以新增至應用程式或 ASP.NET 組態檔 (最常見的方式)，或新增至電腦組態檔。  
  
 當延伸項目新增至組態範圍時，可以將行為新增至行為組態，如下列程式碼所示。 行為組態為可重複使用的項目，也可依需求套用至多個端點。 由於在此處要設定的特定行為會實作 <xref:System.ServiceModel.Description.IEndpointBehavior>，因此只能在組態檔中相對的組態區段中使用。  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 設定訊息偵測器的 `<schemaValidator>` 項目是由 `SchemaValidationBehaviorExtensionElement` 類別所支援。 類別會公開兩個名稱為 `ValidateRequest` 和 `ValidateReply` 的布林公用屬性。 這兩個屬性都會使用 <xref:System.Configuration.ConfigurationPropertyAttribute> 來標示。 這個屬性 (Attribute) 會組成程式碼屬性 (Properties) 和 XML 屬性 (Attribute) 之間的連結，而您可以在之前的 XML 組態項目中看到此連結。 類別也擁有額外以 `Schemas` 標示，而且型別為 <xref:System.Configuration.ConfigurationCollectionAttribute> 的 `SchemaCollection` 屬性，此型別也是範例的一部分，但是為了簡潔起見在這份文件中省略不提。 這個屬性會與集合一起使用，而集合項目類別 `SchemaConfigElement` 支援先前組態程式碼片段中的 `<schemas>` 項目，並允許將結構描述集合新增至驗證組。  
  
 當執行階段在建置用戶端或端點的同時評估組態資料時，覆寫的 `CreateBehavior` 方法便會將組態資料轉換為行為物件。  
  
```  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>以命令方式新增訊息偵測器  
 除了使用屬性 (由於先前所提的原因，在此範例中不支援) 和組態，也可以使用命令式程式碼輕鬆地將行為新增至用戶端和服務執行階段。 在此範例中，會在用戶端應用程式中完成此動作，以測試用戶端訊息偵測器。 `GenericClient` 類別衍生自 <xref:System.ServiceModel.ClientBase%601>，而這會對使用者程式碼公開端點組態。 在隱含地開啟用戶端之前，您可以變更端點組態，例如像下列程式碼所示地新增行為。 在服務上新增行為幾乎等同於此處顯示的用戶端技術，並必須在開啟服務主機之前即已執行新增動作。  
  
```  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
