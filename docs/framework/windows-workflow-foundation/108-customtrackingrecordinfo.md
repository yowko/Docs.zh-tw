---
title: "108 - CustomTrackingRecordInfo | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 108 - CustomTrackingRecordInfo
## 屬性  
  
|||  
|-|-|  
|ID|108|  
|關鍵字|UserEvents，EndToEndMonitoring，Troubleshooting，HealthMonitoring，WFTracking|  
|層級|Information|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當工作流程執行個體內的活動發出連同層級資訊的 CustomTrackingRecord 事件時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord \= CustomTrackingRecord, InstanceID \= %1, RecordNumber\=%2, EventTime\=%3,  Name\=%4, ActivityName\=%5, ActivityId\=%6, ActivityInstanceId\=%7, ActivityTypeName\=%8, Data\=%9, Annotations\=%10, ProfileName \= %11  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|說明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|名稱|xs:string|CustomTrackingRecord 的名稱。|  
|ActivityName|xs:string|發出 CustomTrackingRecord 的活動名稱。|  
|ActivityId|xs:string|發出 CustomTrackingRecord 的活動 ID。|  
|ActivityInstanceId|xs:string|發出 CustomTrackingRecord 的活動執行個體 ID。|  
|ActivityTypeName|xs:string|發出 CustomTrackingRecord 的活動名稱。|  
|資料|xs:string|使用此事件所追蹤的資料。這些值會以下列格式儲存成 XML 項目：\<items\>\<\> item  name \= "dataName" type\="System.String"\<dataValue\>\<\/item\>\/items。如果沒有追蹤的資料，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代資料值來截斷事件。以下型別會儲存為由 ToString\(\); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime 傳回給它們的值。所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|註釋|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|