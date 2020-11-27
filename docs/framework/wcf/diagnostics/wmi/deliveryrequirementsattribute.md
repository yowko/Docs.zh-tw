---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274045"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute

DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Syntax  
  
```csharp
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

 資料類型：字串  
  
 存取類型：唯讀  
  
 指定服務的繫結是否支援合約。  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  

 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定繫結是否支援已排序的訊息。  
  
### <a name="targetcontract"></a>TargetContract  

 資料類型：字串  
  
 存取類型：唯讀  
  
 它所套用的合約。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
