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
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728611"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId 介面

代表目前範圍中應用程式之唯一識別碼的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|取得這個所參考之應用程式之程式碼識別碼的字串標記法指標 `IReferenceAppId` 。|  
|`IReferenceAppId::put_CodeBase`|設定這個所參考之應用程式的程式碼識別碼 `IReferenceAppId` 。|  
|`IReferenceAppId::EnumAppPath`|取得實例的介面指標， `IEnumReferenceIdentity` 其中包含 `IReferenceIdentity` 代表這個之成員的實例 `IReferenceAppId` 。|  
|`IReferenceAppId::get_SubscriptionId`|取得這個的訂閱之標記識別項的字串表示指標 `IReferenceAppId` 。|  
|`IReferenceAppId::put_SubscriptionId`|將訂閱的標記識別項設定為 `IReferenceAppId` 指定的字串值。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IEnumReferenceIdentity 介面](ienumreferenceidentity-interface.md)
- [IReferenceIdentity 介面](ireferenceidentity-interface.md)
