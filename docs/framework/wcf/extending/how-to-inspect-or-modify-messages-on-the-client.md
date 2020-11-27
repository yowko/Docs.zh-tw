---
title: 作法：檢查或修改用戶端上的訊息
description: 瞭解如何藉由執行適當的介面，跨 WCF 用戶端或服務來檢查或修改傳入或傳出的訊息。
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 1f8b75001754739b48d10ee577ae26a175e72860
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249042"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="dfe09-103">作法：檢查或修改用戶端上的訊息</span><span class="sxs-lookup"><span data-stu-id="dfe09-103">How to: Inspect or Modify Messages on the Client</span></span>

<span data-ttu-id="dfe09-104">您可以藉由執行 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> ，並將其插入用戶端執行時間中，來檢查或修改 WCF 用戶端上的傳入或傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="dfe09-104">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="dfe09-105">如需詳細資訊，請參閱 [擴充用戶端](extending-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe09-105">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="dfe09-106">服務上對等的功能為 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="dfe09-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dfe09-107">如需完整的程式碼範例，請參閱 [訊息](../samples/message-inspectors.md) 偵測器範例。</span><span class="sxs-lookup"><span data-stu-id="dfe09-107">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="dfe09-108">檢查或修改訊息</span><span class="sxs-lookup"><span data-stu-id="dfe09-108">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="dfe09-109">實作 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="dfe09-109">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="dfe09-110">根據您要插入用戶端訊息偵測器的範圍，實作 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="dfe09-110">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="dfe09-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 可讓您變更端點層級的行為。</span><span class="sxs-lookup"><span data-stu-id="dfe09-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="dfe09-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> 可讓您變更合約層級的行為。</span><span class="sxs-lookup"><span data-stu-id="dfe09-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="dfe09-113">在 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 方法前，請先插入行為。</span><span class="sxs-lookup"><span data-stu-id="dfe09-113">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dfe09-114">如需詳細資訊，請參閱 [使用行為設定和擴充運行](configuring-and-extending-the-runtime-with-behaviors.md)時間。</span><span class="sxs-lookup"><span data-stu-id="dfe09-114">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfe09-115">範例</span><span class="sxs-lookup"><span data-stu-id="dfe09-115">Example</span></span>  

 <span data-ttu-id="dfe09-116">下列程式碼範例會依序顯示：</span><span class="sxs-lookup"><span data-stu-id="dfe09-116">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="dfe09-117">用戶端偵測器實作。</span><span class="sxs-lookup"><span data-stu-id="dfe09-117">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="dfe09-118">插入偵測器的端點行為。</span><span class="sxs-lookup"><span data-stu-id="dfe09-118">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="dfe09-119"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 衍生類別，允許您在組態檔中加入行為。</span><span class="sxs-lookup"><span data-stu-id="dfe09-119">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="dfe09-120">加入端點行為的組態檔，這個行為會將用戶端訊息偵測器插入用戶端執行階段中。</span><span class="sxs-lookup"><span data-stu-id="dfe09-120">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfe09-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfe09-121">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="dfe09-122">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="dfe09-122">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
