---
title: 113 - WorkflowInstanceTerminatedRecord
ms.date: 03/30/2017
ms.assetid: f53204ee-4ea2-45e1-8859-e86d07305efd
ms.openlocfilehash: e6ea25de7ceea33ca1e552c12545525bbc17f198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924224"
---
# <a name="113---workflowinstanceterminatedrecord"></a>113 - WorkflowInstanceTerminatedRecord
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|113|  
|關鍵字|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|層級|錯誤|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件是當工作流程執行個體發出 WorkflowInstanceTerminatedRecord 時，由 ETW 追蹤參與者發出。  
  
## <a name="message"></a>訊息  
 TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|ActivityDefinitionId|xs:string|工作流程中根活動的名稱。|  
|原因|xs:string|工作流程終止的原因。|  
|標註|xs:string|加入至此事件中的附註。  值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"t"> 以\</項目 > \< /i >。  如果沒有註釋指定的字串包含\<項目 / >。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則捨棄註釋，並取代註釋值來截斷事件\<項目 >... \< /i >。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。  其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' 範例：'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
