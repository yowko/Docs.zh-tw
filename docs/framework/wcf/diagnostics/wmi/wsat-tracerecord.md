---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262212"
---
# <a name="wsat_tracerecord"></a>WSAT_TraceRecord

WSAT_TraceRecord  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>方法  

 WSAT_TraceRecord 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  

 WSAT_TraceRecord 類別有下列屬性：  
  
### <a name="activityid"></a>ActivityID  

 資料型別：物件  
存取類型：唯讀  
  
 追蹤記錄的活動識別碼。  
  
### <a name="eventid"></a>EventID  

 資料型別：sint32  
存取類型：唯讀  
  
 追蹤記錄的事件識別碼。  
  
### <a name="tracerecord"></a>TraceRecord  

 資料類型：字串  
存取類型：唯讀  
  
 追蹤記錄  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
