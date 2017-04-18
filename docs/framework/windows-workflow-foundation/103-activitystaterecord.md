---
title: "103 - ActivityStateRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 103 - ActivityStateRecord
## 屬性  
  
|||  
|-|-|  
|ID|103|  
|關鍵字|EndToEndMonitoring，Troubleshooting，HealthMonitoring，WFTracking|  
|層級|Information|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 說明  
 此事件是當工作流程執行個體內的活動發出 ActivityStateRecord 時，由 ETW 追蹤參與者發出。  
  
## 訊息  
 TrackRecord \= ActivityStateRecord, InstanceID \= %1, RecordNumber\=%2, EventTime\=%3, State \= %4, Name\=%5, ActivityId\=%6, ActivityInstanceId\=%7, ActivityTypeName\=%8, Arguments\=%9, Variables\=%10, Annotations\=%11, ProfileName \= %12  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|說明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|State|xs:string|活動的狀態|  
|Name|xs:string|發出事件之活動的顯示名稱。|  
|ActivityId|xs:string|發出之活動的活動識別碼|  
|ActivityInstanceId|xs:string|發出之活動的活動執行個體 ID。|  
|ActivityTypeName|xs:string|發出之活動的型別名稱|  
|Arguments|xs:string|以這個事件追蹤的引數。這些值會以下列格式儲存在 xml 項目中：\<items\>\<\> item  name \= "argumentName" type\="System.String"\<argumentValue\>\<\/item\>\/items。如果未追蹤任何引數，則字串包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。以下型別會儲存為由 ToString\(\); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime 傳回給它們的值。所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|Variables|xs:string|以這個事件追蹤的變數。這些值以下列格式儲存在 xml 項目中：\<items\>\<\> item  name \= "variableName" type\="System.String"\<variableValue\>\<\/item\>\/items。如果未追蹤任何變數，則字串包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄變數並以 \<items\>...\<\/items\> 取代附註值來截斷事件。以下型別會儲存為由 ToString\(\); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime 傳回給它們的值。所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|註釋|xs:string|加入至此事件中的附註。這些值會以下列格式儲存在 XML 項目中：\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items。如果沒有指定的附註，則字串會包含 \<items\/\>。ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。如果事件大小超過 ETW 限制，則會捨棄附註並以 \<items\>...\<\/items\> 取代附註值來截斷事件。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。範例：'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|