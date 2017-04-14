---
title: "105 - FaultPropagationRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 105 - FaultPropagationRecord
## 屬性  
  
|||  
|-|-|  
|ID|105|  
|關鍵字|EndToEndMonitoring，Troubleshooting，HealthMonitoring，WFTracking|  
|層級|Warning|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當具備工作流程執行個體的活動發出 FaultPropagationRecord 時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord \= FaultPropagationRecord, InstanceID\=%1, RecordNumber\=%2, EventTime\=%3, FaultSourceActivityName\=%4, FaultSourceActivityId\=%5, FaultSourceActivityInstanceId\=%6, FaultSourceActivityTypeName\=%7, FaultHandlerActivityName\=%8,  FaultHandlerActivityId \= %9, FaultHandlerActivityInstanceId \=%10, FaultHandlerActivityTypeName\=%11, Fault\=%12, IsFaultSource\=%13, Annotations\=%14, ProfileName \= %15  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間|  
|FaultSourceActivityName|xs:string|發出錯誤之活動的名稱|  
|FaultSourceActivityId|xs:string|發出錯誤之活動的 ID|  
|FaultSourceActivityInstanceId|xs:string|發出錯誤之活動的執行個體 ID|  
|FaultSourceActivityTypeName|xs:string|發出錯誤之活動的型別|  
|FaultHandlerActivityName|xs:string|錯誤處理常式活動的顯示名稱|  
|FaultHandlerActivityId|xs:string|錯誤處理常式活動的 ID|  
|FaultHandlerActivityInstanceId|xs:string|錯誤處理常式活動的執行個體 ID|  
|FaultHandlerActivityTypeName|xs:string|錯誤處理常式活動的型別|  
|Fault|xs:string|錯誤詳細資料|  
|IsFaultSource|xs:unsignedByte|指出事件是否由錯誤來源發出|  
|附註|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|