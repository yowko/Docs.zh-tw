---
title: 使用追蹤來疑難排解應用程式
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: f991533b61705c8d0a1a8e71b632dd53f24dd979
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401273"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="81e3a-102">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="81e3a-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="81e3a-103">Windows Workflow Foundation (WF) 可讓您追蹤工作流程相關資訊，提供執行的 Windows Workflow Foundation 應用程式或服務的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="81e3a-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="81e3a-104">Windows Workflow Foundation 主機就能夠在工作流程執行個體執行期間擷取工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="81e3a-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="81e3a-105">如果您的工作流程產生錯誤或例外狀況，您可以使用 Windows Workflow Foundation 追蹤詳細資訊來疑難排解其處理程序。</span><span class="sxs-lookup"><span data-stu-id="81e3a-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="81e3a-106">使用 WF 追蹤疑難排解 WF</span><span class="sxs-lookup"><span data-stu-id="81e3a-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="81e3a-107">若要偵測的 Windows Workflow Foundation 活動處理作業中錯誤，您可以啟用查詢的追蹤設定檔的追蹤<xref:System.Activities.Tracking.ActivityStateRecord>為 Faulted 狀態。</span><span class="sxs-lookup"><span data-stu-id="81e3a-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="81e3a-108">下列程式碼中指定對應的查詢。</span><span class="sxs-lookup"><span data-stu-id="81e3a-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="81e3a-109">如果傳播錯誤，並在錯誤處理常式 (例如 <xref:System.Activities.Statements.TryCatch> 活動) 中處理該錯誤，則可使用 <xref:System.Activities.Tracking.FaultPropagationRecord> 偵測到此情形。</span><span class="sxs-lookup"><span data-stu-id="81e3a-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="81e3a-110"><xref:System.Activities.Tracking.FaultPropagationRecord> 會指出錯誤的來源活動，以及錯誤處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="81e3a-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="81e3a-111"><xref:System.Activities.Tracking.FaultPropagationRecord> 包含錯誤詳細資訊，其形式為該錯誤的例外狀況堆疊。下列範例中示範訂閱 <xref:System.Activities.Tracking.FaultPropagationRecord> 的查詢。</span><span class="sxs-lookup"><span data-stu-id="81e3a-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="81e3a-112">如果未在工作流程中處理錯誤，會導致工作流程執行個體出現未處理的例外狀況，而且該工作流程執行個體會中止。</span><span class="sxs-lookup"><span data-stu-id="81e3a-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="81e3a-113">若要了解未處理例外狀況的詳細資訊，追蹤設定檔必須查詢具有 `state name="UnhandledException"` 的工作流程執行個體記錄，如下列範例所指定。</span><span class="sxs-lookup"><span data-stu-id="81e3a-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="81e3a-114">當工作流程執行個體遇到未處理的例外狀況，<xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>如果 Windows Workflow Foundation 追蹤已啟用，就會發出物件。</span><span class="sxs-lookup"><span data-stu-id="81e3a-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="81e3a-115">這個追蹤記錄包含例外狀況堆疊形式的錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="81e3a-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="81e3a-116">它有錯誤 （例如，活動），發生錯誤，導致未處理的例外狀況來源的詳細資料。若要訂閱 Windows Workflow Foundation 錯誤事件，請加入追蹤參與者啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="81e3a-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="81e3a-117">使用會查詢 `ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord> 和 `WorkflowInstanceQuery (state="UnhandledException")` 的追蹤設定檔來設定這個參與者。</span><span class="sxs-lookup"><span data-stu-id="81e3a-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="81e3a-118">如果使用 ETW 追蹤參與者啟用追蹤，會將錯誤事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="81e3a-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="81e3a-119">使用事件檢視器即可檢視這些事件。</span><span class="sxs-lookup"><span data-stu-id="81e3a-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="81e3a-120">這可以在節點下找到**事件檢視器-> 應用程式及服務記錄檔]-> [Microsoft]-> [Windows]-> [應用程式伺服器-應用程式**在分析通道。</span><span class="sxs-lookup"><span data-stu-id="81e3a-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e3a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e3a-121">See Also</span></span>  
 [<span data-ttu-id="81e3a-122">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="81e3a-122">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="81e3a-123">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="81e3a-123">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
