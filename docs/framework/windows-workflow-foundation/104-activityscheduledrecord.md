---
title: "104 - ActivityScheduledRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 104 - ActivityScheduledRecord
## 屬性  
  
|||  
|-|-|  
|ID|104|  
|關鍵字|EndToEndMonitoring，Troubleshooting，HealthMonitoring，WFTracking|  
|層級|Information|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當工作流程執行個體內的活動發出 ActivityScheduledRecord 時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord \= ActivityScheduledRecord, InstanceID \= %1,  RecordNumber \= %2, EventTime \= %3, Name \= %4, ActivityId \= %5, ActivityInstanceId \= %6, ActivityTypeName \= %7, ChildActivityName \= %8, ChildActivityId \= %9, ChildActivityInstanceId \= %10, ChildActivityTypeName \=%11, Annotations\=%12, ProfileName \= %13  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|說明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|Name|xs:string|排程子活動之活動的名稱。|  
|ActivityId|xs:string|排程子活動之活動的 ID。|  
|ActivityInstanceId|xs:string|排程子活動之活動的執行個體 ID。|  
|ActivityTypeName|xs:string|要求取消作業的活動型別。|  
|ChildActivityName|xs:string|已排程活動的名稱。|  
|ChildActivityId|xs:string|已排程活動的 ID。|  
|ChildActivityInstanceId|xs:string|已排程活動的執行個體 ID。|  
|ChildActivityTypeName|xs:string|已排程活動的型別。|  
|Annotations|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|