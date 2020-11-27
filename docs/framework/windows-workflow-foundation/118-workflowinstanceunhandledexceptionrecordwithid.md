---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: 54bbb267902fe547821d4a5580f86da944ae70cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278683"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|118|  
|關鍵字|HealthMonitoring、WFTracking|  
|層級|錯誤|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 此事件是當工作流程執行個體發出 WorkflowInstanceUnhandledExceptionRecord 時，由 ETW 追蹤參與者發出。  
  
## <a name="message"></a>訊息  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、SourceName = %5、SourceId = %6、SourceInstanceId = %7、SourceTypeName=%8、Exception=%9、Annotations= %10、ProfileName = %11、WorkflowDefinitionIdentity = %12  
  
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
|州|xs:string|工作流程的目前狀態。|  
|註解|xs:string|加入至此事件中的附註。 這些值會以 a 格式儲存在 xml 元素中 \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> 。 如果未指定任何批註，則字串會包含 \<items/> 。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代注釋值來截斷事件。 \<items> \</items>|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|WorkflowDefinitionIdentity|xs:string|工作流程定義 ID|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
