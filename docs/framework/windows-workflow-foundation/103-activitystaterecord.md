---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|103|  
|關鍵字|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 此事件是當工作流程執行個體內的活動發出 ActivityStateRecord 時，由 ETW 追蹤參與者發出。  
  
## <a name="message"></a>訊息  
 TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, State = %4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName = %12  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流程的執行個體 ID。|  
|RecordNumber|xs:long|發出之記錄的序號。|  
|EventTime|xs:dateTime|發出事件時的 UTC 時間。|  
|狀態|xs:string|活動的狀態|  
|名稱|xs:string|發出事件之活動的顯示名稱。|  
|ActivityId|xs:string|發出之活動的活動識別碼|  
|ActivityInstanceId|xs:string|發出之活動的活動執行個體 ID。|  
|ActivityTypeName|xs:string|發出之活動的型別名稱|  
|引數|xs:string|以這個事件追蹤的引數。  值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="argumentName"type ="> argumentValue\</項目 > \< /i >。  如果不追蹤的任何引數，則此字串包含\<項目 / >。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。  以下型別會儲存為由 ToString(); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime 傳回給它們的值。  所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|變數|xs:string|以這個事件追蹤的變數。  值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="variableName"type ="> variableValue\</項目 > \< /i >。  如果沒有追蹤的變數，則此字串包含\<項目 / >。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代變數值的截斷\<項目 >... \< /i >。  以下型別會儲存為由 ToString(); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime 傳回給它們的值。  所有其他的型別會使用 System.Runtime.Serialization.NetDataContractSerializer 序列化。|  
|標註|xs:string|加入至此事件中的附註。  值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。  如果沒有指定的註釋的字串，包含\<項目 / >。 ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。 如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。|  
|ProfileName|xs:string|造成發送這個事件的名稱或追蹤設定檔。|  
|HostReference|xs:string|若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。  其格式定義為 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' 範例:' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
