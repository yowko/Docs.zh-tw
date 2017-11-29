---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：字串  
存取類型：唯讀  
  
 追蹤記錄  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
