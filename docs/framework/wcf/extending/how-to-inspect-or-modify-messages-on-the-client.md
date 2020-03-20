---
title: HOW TO：檢查或修改用戶端上的訊息
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185531"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="fc07a-102">HOW TO：檢查或修改用戶端上的訊息</span><span class="sxs-lookup"><span data-stu-id="fc07a-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="fc07a-103">您可以通過實現 並將 傳入<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>或傳出消息插入到用戶端運行時，檢查或修改 WCF 用戶端的傳入或傳出消息。</span><span class="sxs-lookup"><span data-stu-id="fc07a-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="fc07a-104">有關詳細資訊，請參閱[擴展用戶端](extending-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="fc07a-104">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="fc07a-105">服務上對等的功能為 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fc07a-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc07a-106">有關完整的代碼示例，請參閱[消息檢查器](../samples/message-inspectors.md)示例。</span><span class="sxs-lookup"><span data-stu-id="fc07a-106">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="fc07a-107">檢查或修改訊息</span><span class="sxs-lookup"><span data-stu-id="fc07a-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="fc07a-108">實作 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="fc07a-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="fc07a-109">根據您要插入用戶端訊息偵測器的範圍，實作 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fc07a-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="fc07a-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>允許您更改終結點級別的行為。</span><span class="sxs-lookup"><span data-stu-id="fc07a-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="fc07a-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>允許您更改合同級別的行為。</span><span class="sxs-lookup"><span data-stu-id="fc07a-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="fc07a-112">在 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 方法前，請先插入行為。</span><span class="sxs-lookup"><span data-stu-id="fc07a-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc07a-113">有關詳細資訊，請參閱[使用行為配置和擴展運行時](configuring-and-extending-the-runtime-with-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="fc07a-113">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc07a-114">範例</span><span class="sxs-lookup"><span data-stu-id="fc07a-114">Example</span></span>  
 <span data-ttu-id="fc07a-115">下列程式碼範例會依序顯示：</span><span class="sxs-lookup"><span data-stu-id="fc07a-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="fc07a-116">用戶端偵測器實作。</span><span class="sxs-lookup"><span data-stu-id="fc07a-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="fc07a-117">插入偵測器的端點行為。</span><span class="sxs-lookup"><span data-stu-id="fc07a-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="fc07a-118"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 衍生類別，允許您在組態檔中加入行為。</span><span class="sxs-lookup"><span data-stu-id="fc07a-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="fc07a-119">加入端點行為的組態檔，這個行為會將用戶端訊息偵測器插入用戶端執行階段中。</span><span class="sxs-lookup"><span data-stu-id="fc07a-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc07a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc07a-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="fc07a-121">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="fc07a-121">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
