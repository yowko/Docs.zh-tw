---
title: "要求-回覆相互關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29286950cfef7d8e3e2c453bbdcc307c26e641de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-correlation"></a><span data-ttu-id="48ac4-102">要求-回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="48ac4-102">Request-Reply Correlation</span></span>
<span data-ttu-id="48ac4-103">要求-回覆相互關聯會搭配<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組用來實作雙向作業，在工作流程服務與<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>叫用雙向作業中另一個 Web 組服務。</span><span class="sxs-lookup"><span data-stu-id="48ac4-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="48ac4-104">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務中叫用雙向作業時，服務可以是傳統的命令式程式碼架構 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，或是工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="48ac4-104">When invoking a two-way operation in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, the service can be either a traditional imperative code-based [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="48ac4-105">若要使用要求-回覆相互關聯，則必須使用雙向繫結必須，例如 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="48ac4-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="48ac4-106">無論是叫用或實作雙向作業，初始化相互關聯的步驟都很類似，並且涵蓋於本章節中。</span><span class="sxs-lookup"><span data-stu-id="48ac4-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="48ac4-107">在雙向作業中搭配 Receive/SendReply 使用相互關聯</span><span class="sxs-lookup"><span data-stu-id="48ac4-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="48ac4-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組用來在工作流程服務中實作雙向作業。</span><span class="sxs-lookup"><span data-stu-id="48ac4-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="48ac4-109">執行階段會使用要求-回覆相互關聯，確保回覆分派至正確的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="48ac4-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="48ac4-110">如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> (適用於工作流程服務) 裝載工作流程，則預設的相互關聯初始化就已足夠。</span><span class="sxs-lookup"><span data-stu-id="48ac4-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="48ac4-111">在此案例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組由工作流程，並不需要任何特定相互關聯組態。</span><span class="sxs-lookup"><span data-stu-id="48ac4-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="48ac4-112">明確初始化要求-回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="48ac4-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="48ac4-113">如果有其他並行的雙向作業，則應該明確設定相互關聯。</span><span class="sxs-lookup"><span data-stu-id="48ac4-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="48ac4-114">這可藉由指定<xref:System.ServiceModel.Activities.CorrelationHandle>和<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>，或是藉由將<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>內<xref:System.ServiceModel.Activities.CorrelationScope>。</span><span class="sxs-lookup"><span data-stu-id="48ac4-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="48ac4-115">在此範例中，設定要求-回覆相互關聯上<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組。</span><span class="sxs-lookup"><span data-stu-id="48ac4-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="48ac4-116">除了明確設定相互關聯之外，也可以使用 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。</span><span class="sxs-lookup"><span data-stu-id="48ac4-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="48ac4-117"><xref:System.ServiceModel.Activities.CorrelationScope> 會提供隱含的 <xref:System.ServiceModel.Activities.CorrelationHandle> 給它所包含的訊息傳遞活動。</span><span class="sxs-lookup"><span data-stu-id="48ac4-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="48ac4-118">在此範例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組包含在<xref:System.ServiceModel.Activities.CorrelationScope>。</span><span class="sxs-lookup"><span data-stu-id="48ac4-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="48ac4-119">不需要明確的相互關聯組態。</span><span class="sxs-lookup"><span data-stu-id="48ac4-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="48ac4-120">如果需要其他相互關聯，可以使用個別訊息傳遞活動的 <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> 屬性，透過需要的 `CorrelationInitializer` 型別進行設定。</span><span class="sxs-lookup"><span data-stu-id="48ac4-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="48ac4-121">在雙向作業中搭配 Send/ReceiveReply 使用相互關聯</span><span class="sxs-lookup"><span data-stu-id="48ac4-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="48ac4-122">雖然<xref:System.ServiceModel.Activities.Receive>活動只能在裝載的工作流程服務<xref:System.ServiceModel.Activities.WorkflowServiceHost>，<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組可用於任何必須叫用 Web 服務方法的工作流程。</span><span class="sxs-lookup"><span data-stu-id="48ac4-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="48ac4-123">如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程，則適用上一節中所述的預設相互關聯，否則必須使用需要的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 和 <xref:System.ServiceModel.Activities.CorrelationHandle> 明確設定相互關聯，或是使用 <xref:System.ServiceModel.Activities.CorrelationScope> 的隱含控制代碼管理設定相互關聯。</span><span class="sxs-lookup"><span data-stu-id="48ac4-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="48ac4-124">當使用**加入服務參考**活動會產生含雙向作業的服務，在該換行<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組在內部利用要求/回覆相互關聯的活動，明確指定。</span><span class="sxs-lookup"><span data-stu-id="48ac4-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
