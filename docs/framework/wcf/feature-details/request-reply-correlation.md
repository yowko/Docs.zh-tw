---
title: 要求-回覆相互關聯
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: da7739af7368cd7ebb55ed0ea2511e10f0bcb3f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239064"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="f2b7b-102">要求-回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="f2b7b-102">Request-Reply Correlation</span></span>

<span data-ttu-id="f2b7b-103">要求-回復相互關聯可搭配使用， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 以在工作流程服務中執行雙向作業，並使用在 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 另一個 Web 服務中叫用雙向作業的配對來執行雙向作業。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="f2b7b-104">當您在 WCF 服務中叫用雙向作業時，服務可以是傳統的命令式程式碼型 Windows Communication Foundation (WCF) 服務，也可以是工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="f2b7b-105">若要使用要求-回覆相互關聯，則必須使用雙向繫結必須，例如 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="f2b7b-106">無論是叫用或實作雙向作業，初始化相互關聯的步驟都很類似，並且涵蓋於本章節中。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="f2b7b-107">在雙向作業中搭配 Receive/SendReply 使用相互關聯</span><span class="sxs-lookup"><span data-stu-id="f2b7b-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  

 <span data-ttu-id="f2b7b-108">在 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 工作流程服務中，會使用配對來執行雙向作業。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="f2b7b-109">執行階段會使用要求-回覆相互關聯，確保回覆分派至正確的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="f2b7b-110">如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> (適用於工作流程服務) 裝載工作流程，則預設的相互關聯初始化就已足夠。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="f2b7b-111">在此案例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 工作流程會使用配對，而不需要特定的相互關聯設定。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="f2b7b-112">明確初始化要求-回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="f2b7b-112">Explicitly Initializing Request-Reply Correlation</span></span>  

 <span data-ttu-id="f2b7b-113">如果有其他並行的雙向作業，則應該明確設定相互關聯。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="f2b7b-114">這可以藉由指定和來 <xref:System.ServiceModel.Activities.CorrelationHandle> 完成 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> ，或將放在 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 中 <xref:System.ServiceModel.Activities.CorrelationScope> 。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="f2b7b-115">在此範例中，會對一組設定要求-回復相互關聯 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="f2b7b-116">除了明確設定相互關聯之外，也可以使用 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="f2b7b-117"><xref:System.ServiceModel.Activities.CorrelationScope> 會提供隱含的 <xref:System.ServiceModel.Activities.CorrelationHandle> 給它所包含的訊息傳遞活動。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="f2b7b-118">在此範例中，會包含在中的 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 配對 <xref:System.ServiceModel.Activities.CorrelationScope> 。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="f2b7b-119">不需要明確的相互關聯組態。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-119">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="f2b7b-120">如果需要其他相互關聯，可以使用個別訊息傳遞活動的 <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> 屬性，透過需要的 `CorrelationInitializer` 型別進行設定。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="f2b7b-121">在雙向作業中搭配 Send/ReceiveReply 使用相互關聯</span><span class="sxs-lookup"><span data-stu-id="f2b7b-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  

 <span data-ttu-id="f2b7b-122">雖然活動只能在所裝載的 <xref:System.ServiceModel.Activities.Receive> 工作流程服務中使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> ， <xref:System.ServiceModel.Activities.Send> 但該 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 配對可用於任何必須在 Web 服務上叫用方法的工作流程。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="f2b7b-123">如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程，則適用上一節中所述的預設相互關聯，否則必須使用需要的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 和 <xref:System.ServiceModel.Activities.CorrelationHandle> 明確設定相互關聯，或是使用 <xref:System.ServiceModel.Activities.CorrelationScope> 的隱含控制代碼管理設定相互關聯。</span><span class="sxs-lookup"><span data-stu-id="f2b7b-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="f2b7b-124">在具有雙向作業的服務上使用 **加入服務參考** 時，會產生會在 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 內部包裝 a a a a a a a a a a a a a a a a a a a a a a a 的活動</span><span class="sxs-lookup"><span data-stu-id="f2b7b-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
