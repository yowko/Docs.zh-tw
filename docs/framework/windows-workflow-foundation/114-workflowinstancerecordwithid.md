---
title: "114 - WorkflowInstanceRecordWithId | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 114 - WorkflowInstanceRecordWithId
## 屬性  
  
|||  
|-|-|  
|ID|114|  
|關鍵字|HealthMonitoring, WFTracking|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當工作流程執行個體發出 WorkflowInstanceRecord 工作流程狀態：Resumed、Persisted、Idle、Deleted、Completed、Canceled、Unloaded 與 Unsuspended 時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord\= WorkflowInstanceRecord, InstanceID \= %1, RecordNumber \= %2, EventTime \= %3, ActivityDefinitionId \= %4, State \= %5, Annotations \= %6, ProfileName \= %7, WorkflowDefinitionIdentity \= %8  
  
## 詳細資訊  
  
|資料項目名稱|資料項目型別|說明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|ActivityDefinitionId|xs:string|工作流程中根活動的名稱。|  
|狀態|xs:string|工作流程的目前狀態。|  
|註釋|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|WorkflowDefinitionIdentity|xs:string|工作流程定義 ID|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|