---
title: 內容交換相互關聯
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: da5ab2c89e4e2011c38f5fca99aeb5c2c73801a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492319"
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="7ea65-102">內容交換相互關聯</span><span class="sxs-lookup"><span data-stu-id="7ea65-102">Context Exchange Correlation</span></span>
<span data-ttu-id="7ea65-103">內容相互關聯根據所述的內容交換機制[.NET 內容交換通訊協定規格](http://go.microsoft.com/fwlink/?LinkId=166059)。</span><span class="sxs-lookup"><span data-stu-id="7ea65-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="7ea65-104">內容相互關聯使用一般熟知的內容標頭或 Cookie，將訊息關聯至正確的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ea65-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="7ea65-105">若要使用內容相互關聯，您必須在提供給 <xref:System.ServiceModel.BasicHttpContextBinding> 的端點上使用以內容為基礎的繫結，例如 <xref:System.ServiceModel.WSHttpContextBinding>、<xref:System.ServiceModel.NetTcpContextBinding> 或 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="7ea65-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="7ea65-106">本主題說明如何在工作流程服務中使用內容相互關聯搭配訊息活動。</span><span class="sxs-lookup"><span data-stu-id="7ea65-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="7ea65-107">使用內容相互關聯</span><span class="sxs-lookup"><span data-stu-id="7ea65-107">Using Context Correlation</span></span>  
 <span data-ttu-id="7ea65-108">在用戶端必須重複呼叫某個工作流程服務，而該服務是使用其中一種內容繫結來裝載的時候，就會使用內容相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7ea65-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="7ea65-109">這種類型的相互關聯由初始化<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組工作流程服務中的。</span><span class="sxs-lookup"><span data-stu-id="7ea65-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="7ea65-110">內容會與回覆一起傳送回用戶端，然後用戶端會針對服務的後續呼叫，附加這個內容。</span><span class="sxs-lookup"><span data-stu-id="7ea65-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="7ea65-111">在工作流程服務中設定內容相互關聯</span><span class="sxs-lookup"><span data-stu-id="7ea65-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="7ea65-112">內容相互關聯是使用與回覆初始傳入訊息之 <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> 活動相關聯的 <xref:System.ServiceModel.Activities.SendReply> 初始化。</span><span class="sxs-lookup"><span data-stu-id="7ea65-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="7ea65-113">在下列範例中，<xref:System.ServiceModel.Activities.SendReply> 會設定為初始化內容相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7ea65-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  <span data-ttu-id="7ea65-114">在此範例中，所使用的相互關聯型別實際上有兩種：內容相互關聯與要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7ea65-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="7ea65-115">使用內容相互關聯可將用戶端的呼叫路由傳送至正確的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ea65-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="7ea65-116"><xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動會一起使用要求-回覆相互關聯來實作這些活動所模型化的雙向作業。</span><span class="sxs-lookup"><span data-stu-id="7ea65-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="7ea65-117">在此範例中，明確地設定內容相互關聯，而<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>配對正在使用的預設要求-回覆相互關聯所提供的隱含<xref:System.ServiceModel.Activities.CorrelationHandle>管理<xref:System.ServiceModel.Activities.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="7ea65-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="7ea65-118">當使用**ReceiveAndSendReply**活動範本，在工作流程設計工具中，要求-回覆相互關聯已明確設定。</span><span class="sxs-lookup"><span data-stu-id="7ea65-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> <span data-ttu-id="7ea65-119">如需要求-回覆相互關聯與隱含相互關聯控制代碼管理的詳細資訊，請參閱[要求-回覆](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)和[相互關聯概觀](../../../../docs/framework/wcf/feature-details/correlation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7ea65-119">For more information about request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> <span data-ttu-id="7ea65-120">如需有關**ReceiveAndSendReply**活動範本，請參閱[ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer)。</span><span class="sxs-lookup"><span data-stu-id="7ea65-120">For more information about the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="7ea65-121">工作流程服務中的後續 <xref:System.ServiceModel.Activities.Receive> 活動，可以參考在前一個範例中，由 <xref:System.ServiceModel.Activities.CorrelationHandle> 初始化的 <xref:System.ServiceModel.Activities.SendReply>。</span><span class="sxs-lookup"><span data-stu-id="7ea65-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="7ea65-122">然後，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 上的端點就會進行設定，並使用以內容為主的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>。</span><span class="sxs-lookup"><span data-stu-id="7ea65-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="7ea65-123">設定工作流程用戶端中的內容相互關聯</span><span class="sxs-lookup"><span data-stu-id="7ea65-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="7ea65-124">如果用戶端是另一個工作流程，也必須在用戶端上設定內容相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7ea65-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="7ea65-125">用戶端工作流程上<xref:System.ServiceModel.Activities.ReceiveReply>的<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> ，最初呼叫工作流程服務的組必須設有<xref:System.ServiceModel.Activities.ContextCorrelationInitializer>。</span><span class="sxs-lookup"><span data-stu-id="7ea65-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 <span data-ttu-id="7ea65-126">初始化相互關聯之後，後續的 <xref:System.ServiceModel.Activities.Send> 活動就可以使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 來叫用同一個服務執行個體上的方法。</span><span class="sxs-lookup"><span data-stu-id="7ea65-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="7ea65-127">請注意，在這些範例中，內容相互關聯已明確設定。</span><span class="sxs-lookup"><span data-stu-id="7ea65-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="7ea65-128">如果用戶端工作流程並沒有同時裝載在 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中，除非這些活動已包含在 <xref:System.ServiceModel.Activities.CorrelationScope> 活動內，否則相互關聯必須明確設定。</span><span class="sxs-lookup"><span data-stu-id="7ea65-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> <span data-ttu-id="7ea65-129">如需內容相互關聯的詳細資訊，請參閱[NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)範例。</span><span class="sxs-lookup"><span data-stu-id="7ea65-129">For more information about context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="7ea65-130">如果正在呼叫工作流程服務的用戶端不是工作流程，只要該用戶端明確傳遞回第一個工作流程服務呼叫傳回的內容，它仍然可以重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="7ea65-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="7ea65-131">根據預設，透過在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中加入服務參考而產生的 Proxy，將會儲存並傳遞這項內容。</span><span class="sxs-lookup"><span data-stu-id="7ea65-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
