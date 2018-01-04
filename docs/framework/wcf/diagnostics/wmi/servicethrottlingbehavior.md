---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf1c167c4d1a072737f725de2fa0c132ca686f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>語法  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceThrottlingBehavior 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceThrottlingBehavior 類別具有下列屬性：  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 在 ServiceHost 中的所有發送器物件上主動處理的訊息數目上限。  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 一次可執行的服務物件數目上限。  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 主機一次可接受的工作階段數目上限。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
