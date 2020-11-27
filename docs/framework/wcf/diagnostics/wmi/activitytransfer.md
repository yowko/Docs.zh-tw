---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291111"
---
# <a name="activitytransfer"></a>ActivityTransfer

活動傳輸事件  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>方法  

 ActivityTransfer 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  

 ActivityTransfer 類別具有下列屬性：  
  
### <a name="activityid"></a>ActivityID  
  
- 資料型別：物件  
    存取類型：唯讀  
  
- 活動識別碼  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- 資料型別：物件  
    存取類型：唯讀  
  
- 相關活動識別碼  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義。|
