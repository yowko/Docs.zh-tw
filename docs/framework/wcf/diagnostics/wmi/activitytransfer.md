---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
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
