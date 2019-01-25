---
title: 按本文項目分派
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 43f429a0111198bce17f750b855d8e5588b947b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547903"
---
# <a name="dispatch-by-body-element"></a>按本文項目分派
這個範例會示範如何實作將傳入訊息指派至作業的替代演算法。  
  
 根據預設，伺服器模型發送器會根據訊息的 WS-Addressing "Action" 標頭或 HTTP SOAP 要求的相同資訊，對傳入訊息選取適當的處理方法。  
  
 有些未遵循 WS-I Basic Profile 1.1 方針的 SOAP 1.1 Web 服務堆疊，不會根據 Action URI 分派訊息，而是根據 SOAP 本文內之第一個項目的 XML 限定名稱來分派。 同樣地，這些堆疊的用戶端可能會傳送具有空白或 SOAP 1.1 規格允許之任意 HTTP SoapAction 標頭的訊息。  
  
 若要變更訊息分派至方法的方法，範例會在 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 上實作 `DispatchByBodyElementOperationSelector` 擴充性介面。 這個類別會根據訊息本文的第一個項目選取作業。  
  
 類別建構函式預期會以 `XmlQualifiedName` 和字串組填入字典，因此限定名稱表示 SOAP 本文之第一個子系的名稱，而字串表示相符的作業名稱。 `defaultOperationName` 是作業的名稱，而此作業會接收不符合此字典的所有訊息：  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 實作的建置上則非常簡單，因為在介面上只有一個方法：<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>。 此方法的工作為檢查傳入的訊息，並針對目前的端點，傳回等於服務合約之方法名稱的字串。  
  
 在此範例中，作業選取器會使用 <xref:System.Xml.XmlDictionaryReader>，取得傳入訊息本文的 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>。 這個方法已經將讀取器放置在訊息本文的第一個子系上，因此便可取得目前項目的名稱和命名空間 URI，並將這些項目結合至 `XmlQualifiedName`，然後使用結合項目查閱作業選取器持有之字典的對應作業。  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 使用 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 或其他可存取訊息本文內容的方法來存取訊息本文時，會導致訊息標示為「已讀取」，這表示無法對該訊息進行進一步的處理。 因此，作業選取器會使用下列程式碼中顯示的方法，建立傳入訊息的複本。 由於讀取器的位置在檢查期間並未變更，新建立的訊息便可用它來參考也複製的訊息屬性和訊息標頭，因此會對原始訊息進行完整複製：  
  
```csharp
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>將作業選取器新增至服務  
 服務分派作業選取器是 Windows Communication Foundation (WCF) 發送器擴充功能。 若要選取雙工合約之回呼通道上的方法，也會使用用戶端作業選取器，其運作相當類似於此處描述的分派作業選取器，不過並沒有明確涵蓋在本範例中。  
  
 和大多數服務模型延伸項目一樣，分派作業選取器也會使用行為新增至發送器。 A*行為*是組態物件，其中一或多個延伸模組會新增至分派執行階段 （或用戶端執行階段），或變更其設定。  
  
 由於作業選取器具有合約範圍，在這裡可適當實作的行為則是 <xref:System.ServiceModel.Description.IContractBehavior>。 由於會在 <xref:System.Attribute> 衍生類別上實作介面 (如下列程式碼所示)，可以透過宣告方式將行為新增至服務合約。 每次開啟 <xref:System.ServiceModel.ServiceHost> 以及建置分派執行階段時，所有找到的行為便會做為合約上的屬性、作業和服務實作或者服務組態中的項目，接著自動新增這些行為並要求它們做為延伸項目或修改預設組態。  
  
 為達到簡潔性，下列程式碼摘錄只會顯示方法 <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 的實作，而這個方法會影響此範例中發送器的組態變更。 不會顯示其他方法，因為這些方法會傳回呼叫者而不會進行任何運作。  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 首先，<xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 實作會藉由反覆查看服務端點之 <xref:System.ServiceModel.Description.OperationDescription> 的 <xref:System.ServiceModel.Description.ContractDescription> 項目，而設定作業選取器的查閱字典。 接著，檢查每個作業描述以確定是否有 `DispatchBodyElementAttribute` 行為，在這個範例中也會定義 <xref:System.ServiceModel.Description.IOperationBehavior> 實作。 當這個類別也是行為時，則為被動類別，而且不會主動對分派執行階段提供組態變更。 所有方法會傳回呼叫者，而不會採取任何動作。 只會有作業行為，因此新分派機制需要的中繼資料 (也就是選取其作業項目上之本文項目的限定名稱) 可以和相對的作業產生關聯。  
  
 如果找到這類行為，就會從 XML 限定名稱 (`QName` 屬性) 建立值組，並且將作業名稱 (`Name` 屬性) 新增至字典。  
  
 填入字典之後，就會以此資訊建構新的 `DispatchByBodyElementOperationSelector`，並設定為分派執行階段的作業選取器：  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>實作服務  
 在此範例中實作的行為會直接影響解譯和分派網路訊息的方式，也就是服務合約的函式。 最後，應該在選擇要使用該行為的服務實作中，於服務合約層級宣告行為。  
  
 範例專案服務會套用`DispatchByBodyElementBehaviorAttribute`合約行為`IDispatchedByBody`服務合約和標籤每兩個作業`OperationForBodyA()`並`OperationForBodyB()`使用`DispatchBodyElementAttribute`作業行為。 已開啟實作此合約之服務的服務主機時，發送器產生器 (Builder) 會如前所述挑選此中繼資料。  
  
 由於作業選取器只會根據訊息本文項目進行分派，而忽略 "Action"，因此需要告知執行階段不要在傳回的回覆上檢查 "Action" 標頭，方法是將萬用字元 "*" 指派給 `ReplyAction` 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性即可。 此外，它才可讓預設作業具有"Action"屬性設定為萬用字元"\*」。 預設作業會接收無法分派也沒有 `DispatchBodyElementAttribute` 的所有訊息：  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 範例服務實作十分簡單。 每個方法都會將接收的訊息包裝至回覆訊息，並回應至用戶端。  
  
## <a name="running-and-building-the-sample"></a>執行建置範例  
 執行範例時，作業回應的本文內容會顯示在用戶端主控台視窗中，類似下列 (格式化) 輸出。  
  
 用戶端會分別將三個訊息傳送至其本文內容項目名稱為 `bodyA`、`bodyB` 和 `bodyX` 的服務。 如前所述以及顯示的服務合約看來，具有 `bodyA` 項目的傳入訊息會分派至 `OperationForBodyA()` 方法。 由於具有 `bodyX` 本文項目的訊息並沒有明確的分派目標，便會將訊息分派至 `DefaultOperation()`。 每個服務作業都會將接收的訊息本文包裝至方法特定的項目並傳回，這樣便可清楚對此範例相互關聯輸入和輸出訊息：  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>另請參閱
