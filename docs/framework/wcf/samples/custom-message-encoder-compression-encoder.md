---
title: 自訂訊息編碼器：壓縮編碼器
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696782"
---
# <a name="custom-message-encoder-compression-encoder"></a>自訂訊息編碼器：壓縮編碼器
此範例示範如何實作自訂編碼器，使用 Windows Communication Foundation (WCF) 平台。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>範例詳細資料  
 這個範例中包括用戶端主控台程式 (.exe)、自我裝載的服務主控台程式 (.exe) 和壓縮訊息編碼器程式庫 (.dll)。 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `ISampleServer` 介面所定義，而該介面會公開基本字串回應作業 (`Echo` 和 `BigEcho`)。 用戶端會對指定的作業提出同步要求，而服務則會透過重複訊息回覆至用戶端。 主控台視窗上可同時看見用戶端和服務活動。 此範例的目的為顯示如何撰寫自訂編碼器，並示範在網路上壓縮訊息的影響。 您可以將檢測新增至壓縮訊息編碼器，以計算訊息大小、處理時間或同時計算這兩者。  
  
> [!NOTE]
>  在.NET Framework 4 中，自動解壓縮已啟用 WCF 用戶端上如果伺服器傳送壓縮的回應 （使用 GZip 或 Deflate 之類的演算法建立）。 如果服務在 Internet Information Server (IIS) 中是以 Web 裝載的，則可以為服務將 IIS 設定為傳送壓縮回應。 如果需要同時在用戶端和服務上執行壓縮和解壓縮，或者如果服務是自我裝載的，則可以使用此範例。  
  
 此範例示範如何建置和整合的 WCF 應用程式的自訂訊息編碼器。 將同時使用用戶端和服務來部署程式庫 GZipEncoder.dll。 這個範例也會顯示壓縮訊息所造成的影響。 GZipEncoder.dll 中的程式碼會示範下列各項：  
  
-   建置自訂編碼器和編碼器處理站。  
  
-   針對自訂編碼器開發繫結項目。  
  
-   使用自訂繫結組態以整合自訂繫結項目。  
  
-   開發自訂組態處理常式，以允許自訂繫結項目的檔案組態。  
  
 如前所述，在自訂編碼器中會實作多個層級。 為了更清楚說明這些層級之間的關係，下列清單中會提供啟動服務的簡化事件順序：  
  
1.  啟動伺服器。  
  
2.  讀取組態資訊。  
  
    1.  服務組態註冊自訂組態處理常式。  
  
    2.  建立及開啟服務主機。  
  
    3.  自訂組態項目建立及傳回自訂繫結項目。  
  
    4.  自訂繫結項目會建立及傳回訊息編碼器處理站。  
  
3.  收到訊息。  
  
4.  訊息編碼器處理站傳回訊息編碼器，以在訊息中閱讀及寫出回應。  
  
5.  編碼器層會實作為類別處理站。 只需要對自訂編碼器對大眾公開編碼器累別處理站。 建立 <xref:System.ServiceModel.ServiceHost> 或 <xref:System.ServiceModel.ChannelFactory%601> 物件時，繫結項目會傳回處理站物件。 您可以在緩衝處理或資料流處理模式中操作訊息編碼器。 這個範例會同時示範緩衝處理模式和資料流處理模式。  
  
 在每個模式中，抽象 `ReadMessage` 類別上會伴隨 `WriteMessage` 和 `MessageEncoder` 方法。 主要的編碼工作都會透過這些方法進行。 此範例會包裝現有的文字和二進位訊息編碼器。 這樣可讓範例將訊息之網路表示的讀取和撰寫委派給內部編碼器，並讓壓縮編碼器可壓縮或解壓縮結果。 因為沒有任何管線的訊息編碼，這是在 WCF 中使用多個編碼器的唯一模型。 一旦解壓縮訊息，產生的訊息就會傳遞至堆疊上層，以供通道堆疊處理。 在壓縮期間，產生的已壓縮訊息會直接寫入提供的資料流。  
  
 這個範例會使用 Helper 方法 (`CompressBuffer` 和 `DecompressBuffer`)，將緩衝區轉換為資料流以使用 `GZipStream` 類別。  
  
 緩衝處理的 `ReadMessage` 和 `WriteMessage` 類別則會使用 `BufferManager` 類別。 您只能透過編碼器處理站來存取編碼器。 抽象 `MessageEncoderFactory` 類別會提供名稱為 `Encoder` 的屬性以讓您存取目前的編碼器，並提供名稱為 `CreateSessionEncoder` 的方法，讓您可建立支援工作階段的編碼器。 您可以在通道支援工作階段的案例中，依序且可靠地使用這類編碼器。 此案例在資料寫入至網路的每個工作階段中，都能達到最佳的效果。 如果不需要這樣做，則不應該多載基底方法。 `Encoder` 屬性提供的機制可讓您存取無工作階段的編碼器，並讓 `CreateSessionEncoder` 方法的預設實作可傳回屬性的值。 由於範例會包裝現有的編碼器以提供壓縮功能，`MessageEncoderFactory` 實作便會接受表示內部編碼器處理站的 `MessageEncoderFactory`。  
  
 現在，定義編碼器和編碼器處理站，它們可以搭配 WCF 用戶端和服務。 不過，您必須將這些編碼器新增至通道堆疊。 您可以從 <xref:System.ServiceModel.ServiceHost> 和 <xref:System.ServiceModel.ChannelFactory%601> 類別衍生類別，並覆寫 `OnInitialize` 方法以手動新增此編碼器處理站。 您也可以透過自訂繫結項目來公開編碼器處理站。  
  
 若要建立新的自訂繫結項目，請從 <xref:System.ServiceModel.Channels.BindingElement> 類別衍生類別。 會有幾種類型的繫結項目。 若要確定自訂繫結項目已辨識為訊息編碼繫結項目，您也必須實作 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 會公開方法以建立新的訊息編碼器處理站 (`CreateMessageEncoderFactory`)，您會實作此訊息編碼器處理站以傳回相符之訊息編碼器處理站的執行個體。 此外，<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 具有可指出定址版本的屬性。 由於這個範例會包裝現有的編碼器，範例實作也會包裝現有的編碼器繫結項目，並採用內部編碼器繫結項目做為建構函式的參數，並經由屬性來公開此建構函式。 下列範例程式碼會顯示 `GZipMessageEncodingBindingElement` 類別的實作。  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 請注意，`GZipMessageEncodingBindingElement` 類別會實作 `IPolicyExportExtension` 介面，因此此繫結項目便可公開為中繼資料中的原則，如下列範例所示。  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `GZipMessageEncodingBindingElementImporter` 類別會實作 `IPolicyImportExtension` 介面，而且會匯入 `GZipMessageEncodingBindingElement` 的原則。 您可以使用 Svcutil.exe 工具將原則匯入組態檔以處理 `GZipMessageEncodingBindingElement`，並應該將下列項目新增至 Svcutil.exe.config。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 現在已有用於壓縮編碼器的相符繫結項目，透過建構新的自訂繫結物件並在其中新增自訂繫結項目，便可經由程式設計的方式將相符的繫結項目連結至服務或用戶端，如下列範例程式碼所示。  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 雖然這樣做對大多數使用者案例來說已足夠，但在 Web 裝載服務的情況下，支援檔案組態仍然相當重要。 若要支援 Web 裝載的案例，您必須開發自訂組態處理常式，讓自訂繫結項目可在檔案中進行設定。  
  
 您可以在 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 提供的組態系統最上方，建立用於繫結項目的組態處理常式。 繫結項目的組態處理常式必須衍生自 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 類別。 您可以使用 `BindingElementType` 屬性，對組態系統通知要對此區段建立的繫結項目型別。 `BindingElement` 中可以設定的所有項目，都應該公開為 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 衍生類別中的屬性。 您可以使用 <xref:System.Configuration.ConfigurationPropertyAttribute>，在遺失屬性 (Attribute) 的情況下，幫助將組態項目屬性 (Attribute) 對應至屬性 (Properties) 並設定預設值。 載入來自組態的值並將這些值套用至屬性時，就會呼叫 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> 方法，而這個方法會將屬性轉換為繫結項目的具象執行個體。 您可以使用 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> 方法，將 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 衍生類別上的屬性轉換為要在新建立之繫結元素上設定的值。  
  
 下列範例程式碼會顯示 `GZipMessageEncodingElement` 實作。  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 這個組態處理常式會在服務或用戶端的 App.config 或 Web.config 中對應至下列表示。  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 若要使用這個組態處理常式，則必須註冊內[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，如下列範例組態所示。  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 當您執行伺服器時，作業要求和回應會顯示在主控台視窗中。 在每一個視窗中按 ENTER 鍵，關閉伺服器。  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 當您執行用戶端時，作業要求和回應會顯示在主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0：  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>另請參閱
