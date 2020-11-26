---
title: 110 - CustomTrackingRecordWarning
ms.date: 03/30/2017
ms.assetid: 3bc093de-be47-4ed0-983f-05b4246446fc
ms.openlocfilehash: 8fced5fe4baabac34b25b9a00421c3ded1c83ca6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238765"
---
# <a name="110---customtrackingrecordwarning"></a>110 - CustomTrackingRecordWarning

## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|Id|110|  
|關鍵字|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|層級|警告|  
|通路|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  

 此事件是當工作流程執行個體內的活動發出連同層級警告的 CustomTrackingRecord 事件時，由 ETW 追蹤參與者發出。  
  
## <a name="message"></a>訊息  

 TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|Name|xs:string|CustomTrackingRecord 的名稱。|  
|ActivityName|xs:string|發出 CustomTrackingRecord 的活動名稱。|  
|ActivityId|xs:string|發出 CustomTrackingRecord 的活動 ID。|  
|ActivityInstanceId|xs:string|發出 CustomTrackingRecord 的活動執行個體 ID。|  
|ActivityTypeName|xs:string|發出 CustomTrackingRecord 的活動名稱。|  
|資料|xs:string|使用此事件所追蹤的資料。  這些值會以 dataValue 格式儲存在 xml 元素中 \<items> \< item  name = "dataName" type="System.String"> \</item> \</items> 。  如果未追蹤任何資料，則字串會包含 \<items/> 。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代資料值來截斷事件。 \<items> \</items> 下列類型會以 ToString 所傳回的值儲存為其值 ( # A1;string、char、bool、int、short、long、uint、ushort、ulong、System. Single、float、double、System.object、system.string、System.object。  所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|註解|xs:string|加入至此事件中的附註。  這些值會以 a 格式儲存在 xml 元素中 \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> 。  如果未指定任何批註，則字串會包含 \<items/> 。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代注釋值來截斷事件。 \<items> \</items>|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。  其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName ' 範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
