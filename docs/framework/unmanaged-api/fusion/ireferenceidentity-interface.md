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
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity 介面
表示唯一的簽章的程式碼物件的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|取得新的介面指標`IReferenceIdentity`等同於此執行個體`IReferenceIdentity`，除非有指定的屬性變更。|  
|`IReferenceIdentity::EnumAttributes`|取得的介面指標`IEnumIDENTITY_ATTRIBUTE`包含與此相關聯之屬性的執行個體`IReferenceIdentity`。|  
|`IReferenceIdentity::GetAttribute`|在指定的命名空間中具有指定之名稱取得屬性的值。|  
|`IReferenceIdentity::SetAttribute`|設定具有指定的命名空間與指定的名稱，以指定的值的屬性。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE 介面](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
