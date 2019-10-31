---
title: IReferenceAppId 介面
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131652"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId 介面
代表目前範圍中應用程式的唯一識別碼參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|取得此 `IReferenceAppId`所參考應用程式之代碼識別碼的字串表示的指標。|  
|`IReferenceAppId::put_CodeBase`|設定此 `IReferenceAppId`所參考之應用程式的程式碼識別碼。|  
|`IReferenceAppId::EnumAppPath`|取得 `IEnumReferenceIdentity` 實例的介面指標，其中包含代表此 `IReferenceAppId`成員的 `IReferenceIdentity` 實例。|  
|`IReferenceAppId::get_SubscriptionId`|取得此 `IReferenceAppId`之訂閱的 token 識別碼之字串表示的指標。|  
|`IReferenceAppId::put_SubscriptionId`|將此 `IReferenceAppId` 之訂閱的 token 識別碼設定為指定的字串值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [融合介面](fusion-interfaces.md)
- [IEnumReferenceIdentity 介面](ienumreferenceidentity-interface.md)
- [IReferenceIdentity 介面](ireferenceidentity-interface.md)
