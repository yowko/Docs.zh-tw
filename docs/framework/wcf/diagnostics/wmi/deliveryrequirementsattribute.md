---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>語法  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>方法  
 DeliveryRequirementsAttribute 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 DeliveryRequirementsAttribute 類別具有下列屬性：  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定服務的繫結是否支援合約。  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定繫結是否支援已排序的訊息。  
  
### <a name="targetcontract"></a>TargetContract  
 資料型別：字串  
  
 存取類型：唯讀  
  
 它所套用的合約。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
