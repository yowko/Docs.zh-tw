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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2289a9a75311c9642a764844ee466adcc5838655
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744345"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId 介面
代表目前範圍中的應用程式的唯一識別碼的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|取得指標所參考的應用程式的程式碼識別項的字串表示`IReferenceAppId`。|  
|`IReferenceAppId::put_CodeBase`|設定應用程式所參考的程式碼識別碼`IReferenceAppId`。|  
|`IReferenceAppId::EnumAppPath`|取得的介面指標`IEnumReferenceIdentity`執行個體，包含`IReferenceIdentity`執行個體，表示這個成員`IReferenceAppId`。|  
|`IReferenceAppId::get_SubscriptionId`|此訂用帳戶取得的 token 識別碼的字串表示的指標`IReferenceAppId`。|  
|`IReferenceAppId::put_SubscriptionId`|此設定訂用帳戶的語彙基元識別碼`IReferenceAppId`設為指定的字串值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [IReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
