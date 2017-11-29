---
title: "使用追蹤來疑難排解應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02c6d346c6ebea27148c11f5f033f74dfb556e44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="9b303-102">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="9b303-102">Using Tracking to Troubleshoot Applications</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="9b303-103"> 可讓您追蹤工作流程相關資訊，提供有關 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 應用程式或服務執行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9b303-103"> enables you to track workflow-related information to give details into the execution of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] application or service.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="9b303-104"> 主機可以在工作流程執行個體執行期間擷取工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="9b303-104"> hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="9b303-105">如果您的工作流程產生錯誤或例外狀況，您可以使用 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 追蹤詳細資訊來疑難排解其處理程序。</span><span class="sxs-lookup"><span data-stu-id="9b303-105">If your workflow generates faults or exceptions, you can use the [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="9b303-106">使用 WF 追蹤疑難排解 WF</span><span class="sxs-lookup"><span data-stu-id="9b303-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="9b303-107">若要偵測 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 活動處理作業中的錯誤，您可以啟用以追蹤設定檔進行追蹤，該設定檔會查詢狀態為 Faulted 的 <xref:System.Activities.Tracking.ActivityStateRecord>。</span><span class="sxs-lookup"><span data-stu-id="9b303-107">To detect faults within the processing of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="9b303-108">下列程式碼中指定對應的查詢。</span><span class="sxs-lookup"><span data-stu-id="9b303-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="9b303-109">如果傳播錯誤，並在錯誤處理常式 (例如 <xref:System.Activities.Statements.TryCatch> 活動) 中處理該錯誤，則可使用 <xref:System.Activities.Tracking.FaultPropagationRecord> 偵測到此情形。</span><span class="sxs-lookup"><span data-stu-id="9b303-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="9b303-110"><xref:System.Activities.Tracking.FaultPropagationRecord> 會指出錯誤的來源活動，以及錯誤處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b303-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="9b303-111"><xref:System.Activities.Tracking.FaultPropagationRecord> 包含錯誤詳細資訊，其形式為該錯誤的例外狀況堆疊。下列範例中示範訂閱 <xref:System.Activities.Tracking.FaultPropagationRecord> 的查詢。</span><span class="sxs-lookup"><span data-stu-id="9b303-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="9b303-112">如果未在工作流程中處理錯誤，會導致工作流程執行個體出現未處理的例外狀況，而且該工作流程執行個體會中止。</span><span class="sxs-lookup"><span data-stu-id="9b303-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="9b303-113">若要了解未處理例外狀況的詳細資訊，追蹤設定檔必須查詢具有 `state name="UnhandledException"` 的工作流程執行個體記錄，如下列範例所指定。</span><span class="sxs-lookup"><span data-stu-id="9b303-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="9b303-114">工作流程執行個體遇到未處理的例外狀況時，如果已啟用 <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> 追蹤，則會發出 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="9b303-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking has been enabled.</span></span>  
  
 <span data-ttu-id="9b303-115">這個追蹤記錄包含例外狀況堆疊形式的錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9b303-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="9b303-116">記錄中包含出錯且造成未處理例外狀況之錯誤來源 (例如活動) 的詳細資訊。若要訂閱 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 的錯誤事件，請加入追蹤參與者，以啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="9b303-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a [!INCLUDE[wf2](../../../includes/wf2-md.md)], enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="9b303-117">使用會查詢 `ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord> 和 `WorkflowInstanceQuery (state="UnhandledException")` 的追蹤設定檔來設定這個參與者。</span><span class="sxs-lookup"><span data-stu-id="9b303-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="9b303-118">如果使用 ETW 追蹤參與者啟用追蹤，會將錯誤事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9b303-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="9b303-119">使用事件檢視器即可檢視這些事件。</span><span class="sxs-lookup"><span data-stu-id="9b303-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="9b303-120">在節點下找到此**事件檢視器-> 應用程式及服務記錄檔]-> [Microsoft]-> [Windows]-> [應用程式伺服器-應用程式**在分析通道。</span><span class="sxs-lookup"><span data-stu-id="9b303-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b303-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b303-121">See Also</span></span>  
 [<span data-ttu-id="9b303-122">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="9b303-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="9b303-123">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="9b303-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
