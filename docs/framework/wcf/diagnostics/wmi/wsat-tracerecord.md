---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923405"
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>語法  
  
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
  
### <a name="eventid"></a>事件 ID  
 資料型別：sint32  
存取類型：唯讀  
  
 追蹤記錄的事件識別碼。  
  
### <a name="tracerecord"></a>TraceRecord  
 資料型別：字串  
存取類型：唯讀  
  
 追蹤記錄  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
