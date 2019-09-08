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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796352"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity 介面
表示程式碼物件之唯一簽章的參考。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|取得與這個`IReferenceIdentity` `IReferenceIdentity`相同的新實例介面指標，但指定的屬性變更除外。|  
|`IReferenceIdentity::EnumAttributes`|取得`IEnumIDENTITY_ATTRIBUTE`實例的介面指標，其中包含與這個`IReferenceIdentity`相關聯的屬性。|  
|`IReferenceIdentity::GetAttribute`|取得指定之命名空間中具有指定名稱之屬性的值。|  
|`IReferenceIdentity::SetAttribute`|將具有指定之命名空間和指定名稱的屬性設定為指定的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE 介面](ienumidentity-attribute-interface.md)
