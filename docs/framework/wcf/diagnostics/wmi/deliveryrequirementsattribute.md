---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979208"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>語法  
  
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

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
