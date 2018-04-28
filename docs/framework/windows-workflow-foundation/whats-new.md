---
title: 什麼&#39;s Windows Workflow Foundation 的新功能
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6604c4fccec50369d83cede58ff2931c2015c5b9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="what39s-new-in-windows-workflow-foundation"></a><span data-ttu-id="ce09c-102">什麼&#39;s Windows Workflow Foundation 的新功能</span><span class="sxs-lookup"><span data-stu-id="ce09c-102">What&#39;s New in Windows Workflow Foundation</span></span>
<span data-ttu-id="ce09c-103">Windows Workflow Foundation (WF) 中[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]從舊版變更數種開發架構。</span><span class="sxs-lookup"><span data-stu-id="ce09c-103">Windows Workflow Foundation (WF) in [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] changes several development paradigms from previous versions.</span></span> <span data-ttu-id="ce09c-104">現在，建立、執行與維護工作流程以及實作新功能的主機都變得更簡單了。</span><span class="sxs-lookup"><span data-stu-id="ce09c-104">Workflows are now easier to create, execute, and maintain, and implement a host of new functionality.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ce09c-105"> 移轉.NET 3.0 和.NET 3.5 工作流程應用程式使用最新的版本，請參閱[移轉指引](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="ce09c-105"> migrating .NET 3.0 and .NET 3.5 workflow applications to use the latest version, see [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>  
  
## <a name="workflow-activity-model"></a><span data-ttu-id="ce09c-106">工作流程活動模型</span><span class="sxs-lookup"><span data-stu-id="ce09c-106">Workflow Activity Model</span></span>  
 <span data-ttu-id="ce09c-107">現在建立工作流程的基底單元是活動，而非使用 <xref:System.Workflow.Activities.SequentialWorkflowActivity> 或 <xref:System.Workflow.Activities.StateMachineWorkflowActivity> 類別。</span><span class="sxs-lookup"><span data-stu-id="ce09c-107">The activity is now the base unit of creating a workflow, rather than using the <xref:System.Workflow.Activities.SequentialWorkflowActivity> or <xref:System.Workflow.Activities.StateMachineWorkflowActivity> classes.</span></span> <span data-ttu-id="ce09c-108"><xref:System.Activities.Activity> 類別可提供工作流程行為的基底抽象部分。</span><span class="sxs-lookup"><span data-stu-id="ce09c-108">The <xref:System.Activities.Activity> class provides the base abstraction of workflow behavior.</span></span> <span data-ttu-id="ce09c-109">活動作者之後可以針對基本自訂活動功能實作 <xref:System.Activities.CodeActivity>，或是針對使用執行階段範圍的自訂活動功能實作 <xref:System.Activities.NativeActivity>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-109">Activity authors can then implement either <xref:System.Activities.CodeActivity> for basic custom activity functionality, or <xref:System.Activities.NativeActivity> for custom activity functionality that uses the breadth of the runtime.</span></span> <span data-ttu-id="ce09c-110"><xref:System.Activities.Activity> 是活動作者用來表示新的行為，以宣告方式是根據另一個類別<xref:System.Activities.NativeActivity>， <xref:System.Activities.CodeActivity>， <xref:System.Activities.AsyncCodeActivity>，或<xref:System.Activities.DynamicActivity>物件，無論是自訂開發或包含在[內建活動程式庫](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)。</span><span class="sxs-lookup"><span data-stu-id="ce09c-110"><xref:System.Activities.Activity> is a class used by activity authors to express new behaviors declaratively in terms of other <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.DynamicActivity> objects, whether they are custom-developed or included in the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span>  
  
## <a name="rich-composite-activity-options"></a><span data-ttu-id="ce09c-111">豐富的複合活動選項</span><span class="sxs-lookup"><span data-stu-id="ce09c-111">Rich Composite Activity Options</span></span>  
 <span data-ttu-id="ce09c-112"><xref:System.Activities.Statements.Flowchart> 是一個功能強大的新控制流程活動，允許作者建立任意迴圈和條件分支模型。</span><span class="sxs-lookup"><span data-stu-id="ce09c-112"><xref:System.Activities.Statements.Flowchart> is a powerful new control flow activity that allows authors to model arbitrary loops and conditional branching.</span></span> <span data-ttu-id="ce09c-113"><xref:System.Activities.Statements.Flowchart> 提供一個事件驅動的程式設計模型，此設計模型原來只能以 <xref:System.Workflow.Activities.StateMachineWorkflowActivity> 實作。</span><span class="sxs-lookup"><span data-stu-id="ce09c-113"><xref:System.Activities.Statements.Flowchart> provides an event-driven programming model that was previously only able to be implemented with <xref:System.Workflow.Activities.StateMachineWorkflowActivity>.</span></span> <span data-ttu-id="ce09c-114">以傳統流程控制結構為模型的新的流程控制活動 (例如 <xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.Switch%601>) 對程序性工作流程頗有助益。</span><span class="sxs-lookup"><span data-stu-id="ce09c-114">Procedural workflows benefit from new flow-control activities that model traditional flow-control structures, such as <xref:System.Activities.Statements.TryCatch> and <xref:System.Activities.Statements.Switch%601>.</span></span>  
  
## <a name="expanded-built-in-activity-library"></a><span data-ttu-id="ce09c-115">擴充的內建活動程式庫</span><span class="sxs-lookup"><span data-stu-id="ce09c-115">Expanded Built-In Activity Library</span></span>  
 <span data-ttu-id="ce09c-116">活動程式庫的新功能包括：</span><span class="sxs-lookup"><span data-stu-id="ce09c-116">New features of the activity library include:</span></span>  
  
-   <span data-ttu-id="ce09c-117">新的流程控制活動，例如 <xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.Pick>、<xref:System.Activities.Statements.TryCatch>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.Switch%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-117">New flow control activities, such as, <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
-   <span data-ttu-id="ce09c-118">用於處理成員資料的活動 (例如 <xref:System.Activities.Statements.Assign>) 與集合活動 (例如 <xref:System.Activities.Statements.AddToCollection%601>)。</span><span class="sxs-lookup"><span data-stu-id="ce09c-118">Activities for manipulating member data, such as <xref:System.Activities.Statements.Assign> and collection activities such as <xref:System.Activities.Statements.AddToCollection%601>.</span></span>  
  
-   <span data-ttu-id="ce09c-119">用於控制交易的活動，例如 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.Activities.Statements.Compensate>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-119">Activities for controlling transactions, such as <xref:System.Activities.Statements.TransactionScope> and <xref:System.Activities.Statements.Compensate>.</span></span>  
  
-   <span data-ttu-id="ce09c-120">新的傳訊活動，例如 <xref:System.ServiceModel.Activities.SendContent> 和 <xref:System.ServiceModel.Activities.ReceiveReply>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-120">New messaging activities such as <xref:System.ServiceModel.Activities.SendContent> and <xref:System.ServiceModel.Activities.ReceiveReply>.</span></span>  
  
## <a name="explicit-activity-data-model"></a><span data-ttu-id="ce09c-121">明確的活動資料模型</span><span class="sxs-lookup"><span data-stu-id="ce09c-121">Explicit Activity Data Model</span></span>  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]<span data-ttu-id="ce09c-122"> 包含用於儲存或移動資料的新選項。</span><span class="sxs-lookup"><span data-stu-id="ce09c-122"> includes new options for storing or moving data.</span></span> <span data-ttu-id="ce09c-123">使用 <xref:System.Activities.Variable> 可將資料儲存在活動中。</span><span class="sxs-lookup"><span data-stu-id="ce09c-123">Data can be stored in an activity using <xref:System.Activities.Variable>.</span></span> <span data-ttu-id="ce09c-124">將資料移入與移出活動時，會使用特殊的引數型別來判斷資料的移動方向。</span><span class="sxs-lookup"><span data-stu-id="ce09c-124">When moving data in and out of an activity, specialized argument types are used to determine which direction data is moving.</span></span> <span data-ttu-id="ce09c-125">這些型別為 <xref:System.Activities.InArgument>、<xref:System.Activities.InOutArgument> 與 <xref:System.Activities.OutArgument>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-125">These types are <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, and <xref:System.Activities.OutArgument>.</span></span> <span data-ttu-id="ce09c-126">如需詳細資訊，請參閱[Windows Workflow Foundation 資料模型](../../../docs/framework/windows-workflow-foundation/data-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ce09c-126">For more information, see [Windows Workflow Foundation Data Model](../../../docs/framework/windows-workflow-foundation/data-model.md).</span></span>  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a><span data-ttu-id="ce09c-127">增強型裝載、保存及追蹤選項</span><span class="sxs-lookup"><span data-stu-id="ce09c-127">Enhanced Hosting, Persistence, and Tracking Options</span></span>  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]<span data-ttu-id="ce09c-128"> 包含保存增強功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ce09c-128"> contains persistence enhancements such as the following:</span></span>  
  
-   <span data-ttu-id="ce09c-129">此外，還有更多用於執行工作流程的選項，包括 <xref:System.ServiceModel.Activities.WorkflowServiceHost>、<xref:System.Activities.WorkflowApplication> 與 <xref:System.Activities.WorkflowInvoker>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-129">There are more options for running workflows, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, and <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
-   <span data-ttu-id="ce09c-130">使用 <xref:System.Activities.Statements.Persist> 活動可明確保存工作流程狀態資料。</span><span class="sxs-lookup"><span data-stu-id="ce09c-130">Workflow state data can be explicitly persisted using the <xref:System.Activities.Statements.Persist> activity.</span></span>  
  
-   <span data-ttu-id="ce09c-131">主機可以保存而不卸載 <xref:System.Activities.ActivityInstance>。</span><span class="sxs-lookup"><span data-stu-id="ce09c-131">A host can persist an <xref:System.Activities.ActivityInstance> without unloading it.</span></span>  
  
-   <span data-ttu-id="ce09c-132">工作流程可以指定不保存區，同時處理不能保存的資料，將持續性延遲到不保存區結束為止。</span><span class="sxs-lookup"><span data-stu-id="ce09c-132">A workflow can specify no-persist zones while working with data that cannot be persisted, so that persistence is postponed until the no-persist zone exits.</span></span>  
  
-   <span data-ttu-id="ce09c-133">使用 <xref:System.Activities.Statements.TransactionScope> 可以將交易流動至工作流程中。</span><span class="sxs-lookup"><span data-stu-id="ce09c-133">Transactions can be flowed into a workflow using <xref:System.Activities.Statements.TransactionScope>.</span></span>  
  
-   <span data-ttu-id="ce09c-134">使用 <xref:System.Activities.Tracking.TrackingParticipant> 可更輕鬆地完成追蹤。</span><span class="sxs-lookup"><span data-stu-id="ce09c-134">Tracking is more easily accomplished using <xref:System.Activities.Tracking.TrackingParticipant>.</span></span>  
  
-   <span data-ttu-id="ce09c-135">系統事件記錄檔追蹤會使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 提供。</span><span class="sxs-lookup"><span data-stu-id="ce09c-135">Tracking to the system event log is provided using <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
-   <span data-ttu-id="ce09c-136">現在，恢復暫止中的工作流程會利用 <xref:System.Activities.Bookmark> 物件來管理。</span><span class="sxs-lookup"><span data-stu-id="ce09c-136">Resuming a pending workflow is now managed using a <xref:System.Activities.Bookmark> object.</span></span>  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a><span data-ttu-id="ce09c-137">更易於擴充 WF 設計工具經驗的能力</span><span class="sxs-lookup"><span data-stu-id="ce09c-137">Easier Ability to Extend WF Designer Experience</span></span>  
 <span data-ttu-id="ce09c-138">新的 WF 設計工具建立 Windows Presentation Foundation (WPF) 和提供重新裝載 WF 設計工具，Visual Studio 外部時所要使用更簡單的模型，並也會提供更簡單的機制，來建立自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="ce09c-138">The new WF Designer is built on Windows Presentation Foundation (WPF) and provides an easier model to use when rehosting the WF Designer outside of Visual Studio and also provides easier mechanisms for creating custom activity designers.</span></span> <span data-ttu-id="ce09c-139">如需詳細資訊，請參閱[自訂工作流程設計經驗](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="ce09c-139">For more information, see [Customizing the Workflow Design Experience](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).</span></span>
