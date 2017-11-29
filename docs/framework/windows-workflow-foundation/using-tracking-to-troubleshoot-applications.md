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
# <a name="using-tracking-to-troubleshoot-applications"></a>使用追蹤來疑難排解應用程式
[!INCLUDE[wf](../../../includes/wf-md.md)] 可讓您追蹤工作流程相關資訊，提供有關 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 應用程式或服務執行的詳細資訊。 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 主機可以在工作流程執行個體執行期間擷取工作流程事件。 如果您的工作流程產生錯誤或例外狀況，您可以使用 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 追蹤詳細資訊來疑難排解其處理程序。  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>使用 WF 追蹤疑難排解 WF  
 若要偵測 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 活動處理作業中的錯誤，您可以啟用以追蹤設定檔進行追蹤，該設定檔會查詢狀態為 Faulted 的 <xref:System.Activities.Tracking.ActivityStateRecord>。 下列程式碼中指定對應的查詢。  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 如果傳播錯誤，並在錯誤處理常式 (例如 <xref:System.Activities.Statements.TryCatch> 活動) 中處理該錯誤，則可使用 <xref:System.Activities.Tracking.FaultPropagationRecord> 偵測到此情形。 <xref:System.Activities.Tracking.FaultPropagationRecord> 會指出錯誤的來源活動，以及錯誤處理常式的名稱。 <xref:System.Activities.Tracking.FaultPropagationRecord> 包含錯誤詳細資訊，其形式為該錯誤的例外狀況堆疊。下列範例中示範訂閱 <xref:System.Activities.Tracking.FaultPropagationRecord> 的查詢。  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 如果未在工作流程中處理錯誤，會導致工作流程執行個體出現未處理的例外狀況，而且該工作流程執行個體會中止。 若要了解未處理例外狀況的詳細資訊，追蹤設定檔必須查詢具有 `state name="UnhandledException"` 的工作流程執行個體記錄，如下列範例所指定。  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 工作流程執行個體遇到未處理的例外狀況時，如果已啟用 <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> 追蹤，則會發出 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 物件。  
  
 這個追蹤記錄包含例外狀況堆疊形式的錯誤詳細資料。 記錄中包含出錯且造成未處理例外狀況之錯誤來源 (例如活動) 的詳細資訊。若要訂閱 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 的錯誤事件，請加入追蹤參與者，以啟用追蹤。 使用會查詢 `ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord> 和 `WorkflowInstanceQuery (state="UnhandledException")` 的追蹤設定檔來設定這個參與者。  
  
 如果使用 ETW 追蹤參與者啟用追蹤，會將錯誤事件發出至 ETW 工作階段。 使用事件檢視器即可檢視這些事件。 在節點下找到此**事件檢視器-> 應用程式及服務記錄檔]-> [Microsoft]-> [Windows]-> [應用程式伺服器-應用程式**在分析通道。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Server App Fabric 監控](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [使用 App Fabric 監控應用程式](http://go.microsoft.com/fwlink/?LinkId=201275)
