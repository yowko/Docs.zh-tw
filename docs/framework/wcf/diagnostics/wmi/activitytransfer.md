---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484184"
---
# <a name="activitytransfer"></a>ActivityTransfer
活動傳輸事件  
  
## <a name="syntax"></a>語法  
  
```  
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
  
-   資料型別：物件  
    存取類型：唯讀  
  
-   活動識別碼  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   資料型別：物件  
    存取類型：唯讀  
  
-   相關活動識別碼  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義。|
