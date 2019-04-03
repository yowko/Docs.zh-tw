---
title: 按本文項目分派
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 376dfc0dcca3c3278ee4d4afefbe4756dd631212
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817054"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="7285d-102">按本文項目分派</span><span class="sxs-lookup"><span data-stu-id="7285d-102">Dispatch by Body Element</span></span>
<span data-ttu-id="7285d-103">這個範例會示範如何實作將傳入訊息指派至作業的替代演算法。</span><span class="sxs-lookup"><span data-stu-id="7285d-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="7285d-104">根據預設，伺服器模型發送器會根據訊息的 WS-Addressing "Action" 標頭或 HTTP SOAP 要求的相同資訊，對傳入訊息選取適當的處理方法。</span><span class="sxs-lookup"><span data-stu-id="7285d-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="7285d-105">有些未遵循 WS-I Basic Profile 1.1 方針的 SOAP 1.1 Web 服務堆疊，不會根據 Action URI 分派訊息，而是根據 SOAP 本文內之第一個項目的 XML 限定名稱來分派。</span><span class="sxs-lookup"><span data-stu-id="7285d-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="7285d-106">同樣地，這些堆疊的用戶端可能會傳送具有空白或 SOAP 1.1 規格允許之任意 HTTP SoapAction 標頭的訊息。</span><span class="sxs-lookup"><span data-stu-id="7285d-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="7285d-107">若要變更訊息分派至方法的方法，範例會在 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 上實作 `DispatchByBodyElementOperationSelector` 擴充性介面。</span><span class="sxs-lookup"><span data-stu-id="7285d-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="7285d-108">這個類別會根據訊息本文的第一個項目選取作業。</span><span class="sxs-lookup"><span data-stu-id="7285d-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="7285d-109">類別建構函式預期會以 `XmlQualifiedName` 和字串組填入字典，因此限定名稱表示 SOAP 本文之第一個子系的名稱，而字串表示相符的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="7285d-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="7285d-110">`defaultOperationName` 是作業的名稱，而此作業會接收不符合此字典的所有訊息：</span><span class="sxs-lookup"><span data-stu-id="7285d-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="7285d-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 實作的建置上則非常簡單，因為在介面上只有一個方法：<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>。</span><span class="sxs-lookup"><span data-stu-id="7285d-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="7285d-112">此方法的工作為檢查傳入的訊息，並針對目前的端點，傳回等於服務合約之方法名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="7285d-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="7285d-113">在此範例中，作業選取器會使用 <xref:System.Xml.XmlDictionaryReader>，取得傳入訊息本文的 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>。</span><span class="sxs-lookup"><span data-stu-id="7285d-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="7285d-114">這個方法已經將讀取器放置在訊息本文的第一個子系上，因此便可取得目前項目的名稱和命名空間 URI，並將這些項目結合至 `XmlQualifiedName`，然後使用結合項目查閱作業選取器持有之字典的對應作業。</span><span class="sxs-lookup"><span data-stu-id="7285d-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="7285d-115">使用 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 或其他可存取訊息本文內容的方法來存取訊息本文時，會導致訊息標示為「已讀取」，這表示無法對該訊息進行進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="7285d-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="7285d-116">因此，作業選取器會使用下列程式碼中顯示的方法，建立傳入訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="7285d-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="7285d-117">由於讀取器的位置在檢查期間並未變更，新建立的訊息便可用它來參考也複製的訊息屬性和訊息標頭，因此會對原始訊息進行完整複製：</span><span class="sxs-lookup"><span data-stu-id="7285d-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="7285d-118">將作業選取器新增至服務</span><span class="sxs-lookup"><span data-stu-id="7285d-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="7285d-119">服務分派作業選取器是 Windows Communication Foundation (WCF) 發送器擴充功能。</span><span class="sxs-lookup"><span data-stu-id="7285d-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="7285d-120">若要選取雙工合約之回呼通道上的方法，也會使用用戶端作業選取器，其運作相當類似於此處描述的分派作業選取器，不過並沒有明確涵蓋在本範例中。</span><span class="sxs-lookup"><span data-stu-id="7285d-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="7285d-121">和大多數服務模型延伸項目一樣，分派作業選取器也會使用行為新增至發送器。</span><span class="sxs-lookup"><span data-stu-id="7285d-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="7285d-122">A*行為*是組態物件，其中一或多個延伸模組會新增至分派執行階段 （或用戶端執行階段），或變更其設定。</span><span class="sxs-lookup"><span data-stu-id="7285d-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="7285d-123">由於作業選取器具有合約範圍，在這裡可適當實作的行為則是 <xref:System.ServiceModel.Description.IContractBehavior>。</span><span class="sxs-lookup"><span data-stu-id="7285d-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="7285d-124">由於會在 <xref:System.Attribute> 衍生類別上實作介面 (如下列程式碼所示)，可以透過宣告方式將行為新增至服務合約。</span><span class="sxs-lookup"><span data-stu-id="7285d-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="7285d-125">每次開啟 <xref:System.ServiceModel.ServiceHost> 以及建置分派執行階段時，所有找到的行為便會做為合約上的屬性、作業和服務實作或者服務組態中的項目，接著自動新增這些行為並要求它們做為延伸項目或修改預設組態。</span><span class="sxs-lookup"><span data-stu-id="7285d-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="7285d-126">為達到簡潔性，下列程式碼摘錄只會顯示方法 <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 的實作，而這個方法會影響此範例中發送器的組態變更。</span><span class="sxs-lookup"><span data-stu-id="7285d-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="7285d-127">不會顯示其他方法，因為這些方法會傳回呼叫者而不會進行任何運作。</span><span class="sxs-lookup"><span data-stu-id="7285d-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="7285d-128">首先，<xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 實作會藉由反覆查看服務端點之 <xref:System.ServiceModel.Description.OperationDescription> 的 <xref:System.ServiceModel.Description.ContractDescription> 項目，而設定作業選取器的查閱字典。</span><span class="sxs-lookup"><span data-stu-id="7285d-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="7285d-129">接著，檢查每個作業描述以確定是否有 `DispatchBodyElementAttribute` 行為，在這個範例中也會定義 <xref:System.ServiceModel.Description.IOperationBehavior> 實作。</span><span class="sxs-lookup"><span data-stu-id="7285d-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="7285d-130">當這個類別也是行為時，則為被動類別，而且不會主動對分派執行階段提供組態變更。</span><span class="sxs-lookup"><span data-stu-id="7285d-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="7285d-131">所有方法會傳回呼叫者，而不會採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7285d-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="7285d-132">只會有作業行為，因此新分派機制需要的中繼資料 (也就是選取其作業項目上之本文項目的限定名稱) 可以和相對的作業產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7285d-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="7285d-133">如果找到這類行為，就會從 XML 限定名稱 (`QName` 屬性) 建立值組，並且將作業名稱 (`Name` 屬性) 新增至字典。</span><span class="sxs-lookup"><span data-stu-id="7285d-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="7285d-134">填入字典之後，就會以此資訊建構新的 `DispatchByBodyElementOperationSelector`，並設定為分派執行階段的作業選取器：</span><span class="sxs-lookup"><span data-stu-id="7285d-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="7285d-135">實作服務</span><span class="sxs-lookup"><span data-stu-id="7285d-135">Implementing the Service</span></span>  
 <span data-ttu-id="7285d-136">在此範例中實作的行為會直接影響解譯和分派網路訊息的方式，也就是服務合約的函式。</span><span class="sxs-lookup"><span data-stu-id="7285d-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="7285d-137">最後，應該在選擇要使用該行為的服務實作中，於服務合約層級宣告行為。</span><span class="sxs-lookup"><span data-stu-id="7285d-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="7285d-138">範例專案服務會套用`DispatchByBodyElementBehaviorAttribute`合約行為`IDispatchedByBody`服務合約和標籤每兩個作業`OperationForBodyA()`並`OperationForBodyB()`使用`DispatchBodyElementAttribute`作業行為。</span><span class="sxs-lookup"><span data-stu-id="7285d-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="7285d-139">已開啟實作此合約之服務的服務主機時，發送器產生器 (Builder) 會如前所述挑選此中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7285d-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="7285d-140">由於作業選取器只會根據訊息本文項目進行分派，而忽略 "Action"，因此需要告知執行階段不要在傳回的回覆上檢查 "Action" 標頭，方法是將萬用字元 "\*" 指派給 `ReplyAction` 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="7285d-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="7285d-141">此外，它才可讓預設作業具有"Action"屬性設定為萬用字元"\*」。</span><span class="sxs-lookup"><span data-stu-id="7285d-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="7285d-142">預設作業會接收無法分派也沒有 `DispatchBodyElementAttribute` 的所有訊息：</span><span class="sxs-lookup"><span data-stu-id="7285d-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="7285d-143">範例服務實作十分簡單。</span><span class="sxs-lookup"><span data-stu-id="7285d-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="7285d-144">每個方法都會將接收的訊息包裝至回覆訊息，並回應至用戶端。</span><span class="sxs-lookup"><span data-stu-id="7285d-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="7285d-145">執行建置範例</span><span class="sxs-lookup"><span data-stu-id="7285d-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="7285d-146">執行範例時，作業回應的本文內容會顯示在用戶端主控台視窗中，類似下列 (格式化) 輸出。</span><span class="sxs-lookup"><span data-stu-id="7285d-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="7285d-147">用戶端會分別將三個訊息傳送至其本文內容項目名稱為 `bodyA`、`bodyB` 和 `bodyX` 的服務。</span><span class="sxs-lookup"><span data-stu-id="7285d-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="7285d-148">如前所述以及顯示的服務合約看來，具有 `bodyA` 項目的傳入訊息會分派至 `OperationForBodyA()` 方法。</span><span class="sxs-lookup"><span data-stu-id="7285d-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="7285d-149">由於具有 `bodyX` 本文項目的訊息並沒有明確的分派目標，便會將訊息分派至 `DefaultOperation()`。</span><span class="sxs-lookup"><span data-stu-id="7285d-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="7285d-150">每個服務作業都會將接收的訊息本文包裝至方法特定的項目並傳回，這樣便可清楚對此範例相互關聯輸入和輸出訊息：</span><span class="sxs-lookup"><span data-stu-id="7285d-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7285d-151">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="7285d-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7285d-152">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7285d-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7285d-153">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7285d-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7285d-154">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7285d-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7285d-155">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7285d-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7285d-156">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7285d-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7285d-157">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="7285d-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7285d-158">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7285d-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
