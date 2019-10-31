---
title: IReferenceIdentity 介面
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127070"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity 介面
表示程式碼物件之唯一簽章的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|取得與這個 `IReferenceIdentity`相同的新 `IReferenceIdentity` 實例介面指標，但指定的屬性變更除外。|  
|`IReferenceIdentity::EnumAttributes`|取得 `IEnumIDENTITY_ATTRIBUTE` 實例的介面指標，其中包含與此 `IReferenceIdentity`相關聯的屬性。|  
|`IReferenceIdentity::GetAttribute`|取得指定之命名空間中具有指定名稱之屬性的值。|  
|`IReferenceIdentity::SetAttribute`|將具有指定之命名空間和指定名稱的屬性設定為指定的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [融合介面](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE 介面](ienumidentity-attribute-interface.md)
