---
title: 使用追蹤來疑難排解應用程式
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b64b92de9cb36807a2bf1eb7ff57f9f6e1a07156
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988939"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="ca648-102">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="ca648-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="ca648-103">Windows Workflow Foundation （WF）可讓您追蹤工作流程相關資訊，以提供有關 Windows Workflow Foundation 應用程式或服務執行的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ca648-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="ca648-104">Windows Workflow Foundation 主機可以在工作流程實例執行期間捕捉工作流程事件。</span><span class="sxs-lookup"><span data-stu-id="ca648-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="ca648-105">如果您的工作流程產生錯誤或例外狀況，您可以使用 Windows Workflow Foundation 追蹤詳細資料來疑難排解其處理。</span><span class="sxs-lookup"><span data-stu-id="ca648-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="ca648-106">使用 WF 追蹤疑難排解 WF</span><span class="sxs-lookup"><span data-stu-id="ca648-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="ca648-107">若要偵測 Windows Workflow Foundation 活動處理內的錯誤，您可以使用追蹤設定檔來啟用追蹤，以查詢<xref:System.Activities.Tracking.ActivityStateRecord>具有錯誤狀態的。</span><span class="sxs-lookup"><span data-stu-id="ca648-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="ca648-108">下列程式碼中指定對應的查詢。</span><span class="sxs-lookup"><span data-stu-id="ca648-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="ca648-109">如果傳播錯誤，並在錯誤處理常式 (例如 <xref:System.Activities.Statements.TryCatch> 活動) 中處理該錯誤，則可使用 <xref:System.Activities.Tracking.FaultPropagationRecord> 偵測到此情形。</span><span class="sxs-lookup"><span data-stu-id="ca648-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="ca648-110"><xref:System.Activities.Tracking.FaultPropagationRecord> 會指出錯誤的來源活動，以及錯誤處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ca648-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="ca648-111"><xref:System.Activities.Tracking.FaultPropagationRecord>包含錯誤詳細資料，格式為錯誤的例外狀況堆疊。</span><span class="sxs-lookup"><span data-stu-id="ca648-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="ca648-112">要訂閱<xref:System.Activities.Tracking.FaultPropagationRecord>的查詢，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ca648-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="ca648-113">如果未在工作流程中處理錯誤，會導致工作流程執行個體出現未處理的例外狀況，而且該工作流程執行個體會中止。</span><span class="sxs-lookup"><span data-stu-id="ca648-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="ca648-114">若要了解未處理例外狀況的詳細資訊，追蹤設定檔必須查詢具有 `state name="UnhandledException"` 的工作流程執行個體記錄，如下列範例所指定。</span><span class="sxs-lookup"><span data-stu-id="ca648-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="ca648-115">當工作流程實例遇到未處理的例外狀況<xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>時，如果已啟用 Windows Workflow Foundation 追蹤，就會發出物件。</span><span class="sxs-lookup"><span data-stu-id="ca648-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="ca648-116">這個追蹤記錄包含例外狀況堆疊形式的錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ca648-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="ca648-117">其中包含錯誤來源的詳細資料（例如活動），並導致未處理的例外狀況。若要從 Windows Workflow Foundation 訂閱錯誤事件，請藉由新增追蹤參與者來啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="ca648-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="ca648-118">使用會查詢 `ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord> 和 `WorkflowInstanceQuery (state="UnhandledException")` 的追蹤設定檔來設定這個參與者。</span><span class="sxs-lookup"><span data-stu-id="ca648-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="ca648-119">如果使用 ETW 追蹤參與者啟用追蹤，會將錯誤事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ca648-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="ca648-120">使用事件檢視器即可檢視這些事件。</span><span class="sxs-lookup"><span data-stu-id="ca648-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="ca648-121">這可以在 [**事件檢視器 > 應用程式和服務記錄] 節點下找到，> Microsoft > Windows >-** 分析通道中的應用程式伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca648-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca648-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca648-122">See also</span></span>

- [<span data-ttu-id="ca648-123">Windows Server App Fabric 監視</span><span class="sxs-lookup"><span data-stu-id="ca648-123">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="ca648-124">使用 App Fabric 監視應用程式</span><span class="sxs-lookup"><span data-stu-id="ca648-124">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
