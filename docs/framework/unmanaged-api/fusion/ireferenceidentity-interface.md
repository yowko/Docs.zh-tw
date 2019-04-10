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
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220158"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity 介面
表示唯一的簽章的程式碼物件的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|取得新的介面指標`IReferenceIdentity`等於這個執行個體`IReferenceIdentity`，但不包括指定的屬性變更。|  
|`IReferenceIdentity::EnumAttributes`|取得的介面指標`IEnumIDENTITY_ATTRIBUTE`執行個體，包含與此相關聯的屬性`IReferenceIdentity`。|  
|`IReferenceIdentity::GetAttribute`|取得屬性的值中指定的命名空間，以指定的名稱。|  
|`IReferenceIdentity::SetAttribute`|設定具有指定的命名空間和指定的值指定之名稱的屬性。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE 介面](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
