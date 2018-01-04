---
title: "使用流程追蹤判斷工作流程的執行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2687d045db28974e99b2f2b6a3222924a520720
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="3d6d2-102">使用流程追蹤判斷工作流程的執行</span><span class="sxs-lookup"><span data-stu-id="3d6d2-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="3d6d2-103">本主題示範如何判斷成功完成的自行裝載工作流程使用工作流程追蹤來執行所需的時間。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="3d6d2-104">若要使用工作流程追蹤來判斷工作流程應用程式執行的持續期間</span><span class="sxs-lookup"><span data-stu-id="3d6d2-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="3d6d2-105">開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="3d6d2-106">選取**檔案**，**新**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="3d6d2-107">在下**C#**，選取**工作流程**節點。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="3d6d2-108">選取**工作流程主控台應用程式**從範本清單。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="3d6d2-109">將新專案`WorkflowDurationTracing`按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="3d6d2-110">開啟 Workflow1.xaml。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="3d6d2-111">將 <xref:System.Activities.Statements.Delay> 活動拖曳至設計工具介面上。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="3d6d2-112">將 00:00:10 值 (十秒鐘) 指派給活動的 Duration 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="3d6d2-113">開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="3d6d2-114">如果您尚未啟用工作流程追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**.</span><span class="sxs-lookup"><span data-stu-id="3d6d2-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="3d6d2-115">選取**檢視**，**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="3d6d2-116">以滑鼠右鍵按一下**偵錯**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="3d6d2-117">讓 [事件檢視器] 保持開啟狀態，如此在工作流程執行之後就能檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="3d6d2-118">按 CTRL+SHIFT+B 執行工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="3d6d2-119">在 [事件檢視器] 中，尋找 ID 為 1009 的最近事件，並尋找類似以下的訊息。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="3d6d2-120">請記下當初記錄訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="3d6d2-121">**父活動 '、 DisplayName: '、 InstanceId: ' 已排的程子活動 'WorkflowDurationTracking.Workflow1'、 DisplayName: 'Workflow1'、 InstanceId: '1'。**</span><span class="sxs-lookup"><span data-stu-id="3d6d2-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="3d6d2-122">尋找 ID 為 1001 的另一個最近事件，並尋找類似以下的訊息。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="3d6d2-123">從這個訊息的記錄值中減去上一個訊息的時間，以判斷工作流程執行的持續期間，應該大約 10 秒鐘左右。</span><span class="sxs-lookup"><span data-stu-id="3d6d2-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="3d6d2-124">**WorkflowInstance Id: ' 1bbac57b-3322-498e-9e27-8833fda3a5bf' 已在 Closed 狀態中完成。**</span><span class="sxs-lookup"><span data-stu-id="3d6d2-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6d2-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d6d2-125">See Also</span></span>  
 [<span data-ttu-id="3d6d2-126">工作流程追蹤</span><span class="sxs-lookup"><span data-stu-id="3d6d2-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="3d6d2-127">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="3d6d2-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="3d6d2-128">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="3d6d2-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
