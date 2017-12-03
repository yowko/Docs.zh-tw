---
title: "追蹤記錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 764253f24f75b4311f181671c7dc85677df701ff
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-records"></a>追蹤記錄
工作流程執行階段經檢測會發出追蹤記錄，以追蹤工作流程執行個體的執行。  
  
## <a name="tracking-records"></a>追蹤記錄  
 下表詳細說明工作流程執行階段發出的追蹤記錄。  
  
|追蹤記錄|描述|  
|---------------------|-----------------|  
|工作流程生命週期記錄|在工作流程執行個體開發週期的不同階段發出。 例如，當工作流程啟動或完成時，就會發出記錄。|  
|活動生命週期記錄|活動執行詳細資訊。 這些記錄會指出工作流程活動的狀態，例如活動排程時間、活動完成時間，或是發生錯誤的時間。|  
|書籤繼續記錄|只要工作流程執行個體中的書籤繼續，就會發出。|  
|自訂追蹤記錄|工作流程作者可建立自訂追蹤事件記錄，並在自訂活動中發出這些記錄。|  
  
 所有與追蹤相關的記錄均會從衍生自基底類別 <xref:System.Activities.Tracking.TrackingRecord> (包含通用資料集) 的 WF 執行階段發出。 追蹤記錄會顯示簡單工作流程的生命週期。 每個追蹤記錄均包含相關聯之追蹤事件的詳細資訊，例如 <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>、<xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>，以及追蹤記錄類型專屬的其他資訊。  
  
 工作流程執行階段會發出下列型別的 <xref:System.Activities.Tracking.TrackingRecord> 物件：  
  
-   **WorkflowInstanceRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>描述工作流程執行個體的生命週期。 例如，當工作流程啟動或完成時，就會發出記錄，同時包含工作流程執行個體的狀態。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.WorkflowInstanceRecord> 中找到。  
  
-   **WorkflowInstanceAbortedRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>中止工作流程執行個體時，就會發出。 記錄包含工作流程執行個體中止的原因。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord> 中找到。  
  
-   **WorkflowInstanceUnhandledExceptionRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>如果工作流程執行個體，就會發生例外狀況，而不由任何活動處理，就會發出。 記錄包含例外狀況的詳細資訊。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> 中找到。  
  
-   **WorkflowInstanceSuspendedRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>每當工作流程執行個體被擱置時，就會發出。 記錄包含工作流程執行個體暫停的原因。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord> 中找到。  
  
-   **WorkflowInstanceTerminatedRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>只要終止工作流程執行個體就會發出。 記錄包含工作流程執行個體終止的原因。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord> 中找到。  
  
-   **ActivityStateRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>工作流程內的活動執行時，就會發出。 這些記錄會指出工作流程執行個體內之活動的狀態。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.ActivityStateRecord> 中找到。  
  
-   **ActivityScheduledRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>當活動排程的子活動，就會發出。 這個記錄包含父活動 (排程活動) 及排程之子活動的詳細資訊。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.ActivityScheduledRecord> 中找到。  
  
-   **FaultPropagationRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>為每個處理常式在記錄處理它之前發出。 這個記錄會用於表示錯誤在工作流程執行個體中採取的路徑。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.FaultPropagationRecord> 中找到。  
  
-   **CancelRequestedRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>只要活動嘗試取消子活動就會發出。 這個記錄包含父活動及要取消之子活動的詳細資訊。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.CancelRequestedRecord> 中找到。  
  
-   **BookmarkResumptionRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>會追蹤順利繼續的任何書籤。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.BookmarkResumptionRecord> 中找到。  
  
-   **CustomTrackingRecord** -這個<xref:System.Activities.Tracking.TrackingRecord>建立後，工作流程作者在自訂工作流程活動所發出。 自訂追蹤記錄中可以填入要發出的資料與記錄。 這個記錄的詳細資訊可以在 <xref:System.Activities.Tracking.CustomTrackingRecord> 中找到。  
  
 例如，若有包含 <xref:System.Activities.Statements.Sequence> 作業的簡單 <xref:System.Activities.Statements.WriteLine> 活動，其追蹤記錄是按下列順序發出的：  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> 表示工作流程正在啟動。  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord> 表示活動已排程。 在此種情況下，這是 <xref:System.Activities.Statements.Sequence> 活動。  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord> 代表 <xref:System.Activities.Statements.WriteLine> 活動。  
  
4.  有兩個 <xref:System.Activities.Tracking.ActivityStateRecord> 記錄，代表兩個即將完成的活動。  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> 表示工作流程正在完成。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Server App Fabric 監控](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [使用 App Fabric 監控應用程式](http://go.microsoft.com/fwlink/?LinkId=201275)
