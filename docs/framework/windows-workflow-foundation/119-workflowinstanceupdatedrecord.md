---
title: 119 - WorkflowInstanceUpdatedRecord
ms.date: 03/30/2017
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
ms.openlocfilehash: c76ce2ffcd25ebe09463e6d704787f321baa2cb3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278657"
---
# <a name="119---workflowinstanceupdatedrecord"></a>119 - WorkflowInstanceUpdatedRecord

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|識別碼|119|  
|關鍵字|HealthMonitoring、WFTracking|  
|層級|資訊|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 當工作流程執行個體更新時，ETW 追蹤參與者就會發出此事件。  
  
## <a name="message"></a>訊息  

 TrackRecord= WorkflowInstanceUpdatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、OriginalDefinitionIdentity = %6、UpdatedDefinitionIdentity = %7、Annotations = %8、ProfileName = %9  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|ActivityDefinitionId|xs:string|工作流程中根活動的名稱。|  
|州|xs:string|工作流程的目前狀態。|  
|OriginalDefinitionIdentity|xs:string|原始工作流程定義 ID|  
|UpdatedDefinitionIdentity|xs:string|更新的工作流程定義 ID|  
|註解|xs:string|加入至此事件中的附註。 這些值會以 a 格式儲存在 xml 元素中 \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> 。 如果未指定任何批註，則字串會包含 \<items/> 。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代注釋值來截斷事件。 \<items> \</items>|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|WorkflowDefinitionIdentity|xs:string|工作流程定義 ID|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
