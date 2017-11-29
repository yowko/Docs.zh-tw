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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
