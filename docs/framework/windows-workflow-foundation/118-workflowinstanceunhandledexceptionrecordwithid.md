---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: eb69fc4760cd89294e24680b5aab83fcd058feb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|118|  
|關鍵字|HealthMonitoring、WFTracking|  
|層級|錯誤|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件是當工作流程執行個體發出 WorkflowInstanceUnhandledExceptionRecord 時，由 ETW 追蹤參與者發出。  
  
## <a name="message"></a>訊息  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord、 InstanceID = %1、 RecordNumber = %2、 EventTime = %3、 ActivityDefinitionId = %4、 SourceName = %5、 SourceId = %6、 SourceInstanceId = %7、 SourceTypeName = %8、 Exception = %9、 Annotations = %10、 ProfileName =%11、 WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|ActivityDefinitionId|xs:string|工作流程中根活動的名稱。|  
|SourceName|xs:string|錯誤造成之 unhandledException 的來源活動名稱|  
|SourceId|xs:string|錯誤來源活動的活動識別碼。|  
|SourceInstanceId|xs:string|錯誤來源活動的活動執行個體 ID。|  
|SourceTypeName|xs:string|錯誤造成之 unhandledException 的來源活動型別名稱。|  
|例外狀況|xs:string|未處理之例外狀況的例外狀況詳細資料。|  
|狀態|xs:string|工作流程的目前狀態。|  
|標註|xs:string|加入至此事件中的附註。 值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。 如果沒有指定的註釋的字串，包含\<項目 / >。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|WorkflowDefinitionIdentity|xs:string|工作流程定義 ID|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
