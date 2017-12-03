---
title: "Windows Workflow 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b74ecc3363e84d006d82ecb14accbf40de7e2738
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-overview"></a><span data-ttu-id="2a6eb-102">Windows Workflow 概觀</span><span class="sxs-lookup"><span data-stu-id="2a6eb-102">Windows Workflow Overview</span></span>
<span data-ttu-id="2a6eb-103">工作流程是一組元素的單元*活動*，會儲存為描述真實世界的處理序模型。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-103">A workflow is a set of elemental units called *activities* that are stored as a model that describes a real-world process.</span></span> <span data-ttu-id="2a6eb-104">工作流程能夠描述執行的順序，以及短期工作和長期工作之間的相依關係。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-104">Workflows provide a way of describing the order of execution and dependent relationships between pieces of short- or long-running work.</span></span> <span data-ttu-id="2a6eb-105">這個工作會從頭到尾經過整個模型，而活動可能會由人員或系統功能執行。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-105">This work passes through the model from start to finish, and activities might be executed by people or by system functions.</span></span>  
  
## <a name="workflow-run-time-engine"></a><span data-ttu-id="2a6eb-106">工作流程執行階段引擎</span><span class="sxs-lookup"><span data-stu-id="2a6eb-106">Workflow Run-time Engine</span></span>  
 <span data-ttu-id="2a6eb-107">每個執行中的工作流程執行個體是由同處理序執行階段引擎建立與維護的，主機處理序會透過以下其中一種方式與該引擎互動：</span><span class="sxs-lookup"><span data-stu-id="2a6eb-107">Every running workflow instance is created and maintained by an in-process run-time engine that the host process interacts with through one of the following:</span></span>  
  
-   <span data-ttu-id="2a6eb-108"><xref:System.Activities.WorkflowInvoker>，如同方法一般叫用工作流程。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-108">A <xref:System.Activities.WorkflowInvoker>, which invokes the workflow like a method.</span></span>  
  
-   <span data-ttu-id="2a6eb-109"><xref:System.Activities.WorkflowApplication>，明確控制單一工作流程執行個體的執行。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-109">A <xref:System.Activities.WorkflowApplication> for explicit control over the execution of a single workflow instance.</span></span>  
  
-   <span data-ttu-id="2a6eb-110">在多個執行個體的案例中進行訊息式互動的 <xref:System.ServiceModel.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-110">A <xref:System.ServiceModel.WorkflowServiceHost> for message-based interactions in multi-instance scenarios.</span></span>  
  
 <span data-ttu-id="2a6eb-111">這裡每個類別都會包含核心活動執行階段，此執行階段是以負責活動執行的 <xref:System.Activities.ActivityInstance> 來表示。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-111">Each of these classes wraps the core activity runtime represented as a <xref:System.Activities.ActivityInstance> responsible for activity execution.</span></span> <span data-ttu-id="2a6eb-112">在並行執行的應用程式網域內可能有幾個 <xref:System.Activities.ActivityInstance> 物件。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-112">There can be several <xref:System.Activities.ActivityInstance> objects within an application domain running concurrently.</span></span>  
  
 <span data-ttu-id="2a6eb-113">前三個主機互動物件是從稱為工作流程程式的活動樹狀結構中所建立。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-113">Each of the preceding three host interaction objects is created from a tree of activities referred to as a workflow program.</span></span> <span data-ttu-id="2a6eb-114">使用這些型別或包含的 <xref:System.Activities.ActivityInstance> 自訂主機，工作流程即可在任何 Windows 處理序內部執行，包括主控台應用程式、表單架構應用程式、Windows 服務、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網站和 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-114">Using these types or a custom host that wraps <xref:System.Activities.ActivityInstance>, workflows can be executed inside any Windows process including console applications, forms-based applications, Windows Services, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sites, and [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]services.</span></span>  
  
 <span data-ttu-id="2a6eb-115">![在主控件程序中的工作流程元件](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")</span><span class="sxs-lookup"><span data-stu-id="2a6eb-115">![Workflow components in the host process](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")</span></span>  
<span data-ttu-id="2a6eb-116">主機處理序中的工作流程元件</span><span class="sxs-lookup"><span data-stu-id="2a6eb-116">Workflow components in the host process</span></span>  
  
## <a name="interaction-between-workflow-components"></a><span data-ttu-id="2a6eb-117">工作流程元件之間的互動</span><span class="sxs-lookup"><span data-stu-id="2a6eb-117">Interaction between Workflow Components</span></span>  
 <span data-ttu-id="2a6eb-118">下圖顯示工作流程元件之間的互動方式。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-118">The following diagram demonstrates how workflow components interact with one another.</span></span>  
  
 <span data-ttu-id="2a6eb-119">![工作流程互動](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")</span><span class="sxs-lookup"><span data-stu-id="2a6eb-119">![Workflow interaction](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")</span></span>  
  
 <span data-ttu-id="2a6eb-120">在上圖中，<xref:System.Activities.WorkflowInvoker.Invoke%2A> 類別的 <xref:System.Activities.WorkflowInvoker> 方法是用於叫用幾個工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-120">In the preceding diagram, the <xref:System.Activities.WorkflowInvoker.Invoke%2A> method of the <xref:System.Activities.WorkflowInvoker> class is used to invoke several workflow instances.</span></span> <span data-ttu-id="2a6eb-121"><xref:System.Activities.WorkflowInvoker> 是用於不需要從主機管理的輕量工作流程，需要從主機 (例如 <xref:System.Activities.Bookmark> 繼續) 管理的工作流程則必須改用 <xref:System.Activities.WorkflowApplication.Run%2A> 來執行。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-121"><xref:System.Activities.WorkflowInvoker> is used for lightweight workflows that do not need management from the host; workflows that need management from the host (such as <xref:System.Activities.Bookmark> resumption) must be executed using <xref:System.Activities.WorkflowApplication.Run%2A> instead.</span></span> <span data-ttu-id="2a6eb-122">不一定要先等候一個工作流程完成，才能叫用另一個工作流程，執行階段引擎支援同時執行多個工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-122">It isn’t required to wait for one workflow instance to complete before invoking another; the runtime engine supports running multiple workflow instances simultaneously.</span></span>  <span data-ttu-id="2a6eb-123">叫用的工作流程如下：</span><span class="sxs-lookup"><span data-stu-id="2a6eb-123">The workflows invoked are as follows:</span></span>  
  
-   <span data-ttu-id="2a6eb-124">包含 <xref:System.Activities.Statements.Sequence> 子活動的 <xref:System.Activities.Statements.WriteLine> 活動。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-124">A <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> child activity.</span></span> <span data-ttu-id="2a6eb-125">父活動的 <xref:System.Activities.Variable> 會繫結至子活動的 <xref:System.Activities.InArgument>。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-125">A <xref:System.Activities.Variable> of the parent activity is bound to an <xref:System.Activities.InArgument> of the child activity.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="2a6eb-126">變數、 引數，以及繫結，請參閱[變數和引數](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-126"> on variables, arguments, and binding, see [Variables and Arguments](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
-   <span data-ttu-id="2a6eb-127">稱為 `ReadLine` 的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-127">A custom activity called `ReadLine`.</span></span> <span data-ttu-id="2a6eb-128"><xref:System.Activities.OutArgument> 活動的 `ReadLine` 會傳回，以呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-128">An <xref:System.Activities.OutArgument> of the `ReadLine` activity is returned to the calling <xref:System.Activities.WorkflowInvoker.Invoke%2A> method.</span></span>  
  
-   <span data-ttu-id="2a6eb-129">衍生自 <xref:System.Activities.CodeActivity>抽象類別的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-129">A custom activity that derives from the <xref:System.Activities.CodeActivity> abstract class.</span></span> <span data-ttu-id="2a6eb-130"><xref:System.Activities.CodeActivity> 可存取使用 <xref:System.Activities.CodeActivityContext> 而可用來做為 <xref:System.Activities.CodeActivity.Execute%2A> 方法之參數的執行階段功能 (例如追蹤與屬性)。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-130">The <xref:System.Activities.CodeActivity> can access run-time features (such as tracking and properties) using the <xref:System.Activities.CodeActivityContext> that is available as a parameter of the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="2a6eb-131">這些執行階段功能，請參閱[工作流程追蹤](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)和[工作流程執行屬性](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6eb-131"> these run-time features, see [Workflow Tracking and Tracing](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Workflow Execution Properties](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a6eb-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6eb-132">See Also</span></span>  
 [<span data-ttu-id="2a6eb-133">BizTalk Server 2006 或 WF？為您的專案選擇正確的工作流程工具</span><span class="sxs-lookup"><span data-stu-id="2a6eb-133">BizTalk Server 2006 or WF? Choosing the Right Workflow Tool for Your Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=154901)
