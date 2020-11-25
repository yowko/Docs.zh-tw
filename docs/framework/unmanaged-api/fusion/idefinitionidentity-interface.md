---
title: IDefinitionIdentity 介面
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 4f08fbbf9c8be16dff092327713e731c5aa14661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732862"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity 介面

表示在目前範圍中定義應用程式之程式碼的唯一簽章。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|取得與 `IDefinitionIdentity` 此相同之新物件的介面指標 `IDefinitionIdentity` ，但指定的屬性變更除外。|  
|`IDefinitionIdentity::EnumAttributes`|取得 [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) 物件的介面指標，其中包含與這個相關聯的屬性 `IDefinitionIdentity` 。|  
|`IDefinitionIdentity::GetAttribute`|取得指定的命名空間中具有指定名稱之屬性的值。|  
|`IDefinitionIdentity::SetAttribute`|將指定的命名空間中具有指定之名稱的屬性設定為指定的值。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
