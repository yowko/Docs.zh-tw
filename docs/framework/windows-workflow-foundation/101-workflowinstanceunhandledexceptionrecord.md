---
title: "101 - WorkflowInstanceUnhandledExceptionRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 101 - WorkflowInstanceUnhandledExceptionRecord
## 屬性  
  
|||  
|-|-|  
|ID|101|  
|關鍵字|EndToEndMonitoring，Troubleshooting，HealthMonitoring，WFTracking|  
|層級|Error|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當工作流程執行個體發出 WorkflowInstanceUnhandledExceptionRecord 時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord \= WorkflowInstanceUnhandledExceptionRecord, InstanceID \= %1, RecordNumber \= %2, EventTime \= %3, ActivityDefinitionId \= %4, SourceName \= %5, SourceId \= %6, SourceInstanceId \= %7, SourceTypeName\=%8, Exception\=%9, Annotations\= %10, ProfileName \= %11  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|說明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|ActivityDefinitionId|xs:string|工作流程中根活動的名稱。|  
|SourceName|xs:string|錯誤造成之 unhandledException 的來源活動名稱|  
|SourceId|xs:string|錯誤來源活動的活動識別碼。|  
|SourceInstanceId|xs:string|錯誤來源活動的活動執行個體 ID。|  
|SourceTypeName|xs:string|錯誤造成之 unhandledException 的來源活動型別名稱。|  
|Exception|xs:string|未處理之例外狀況的例外狀況詳細資料。|  
|Annotations|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|