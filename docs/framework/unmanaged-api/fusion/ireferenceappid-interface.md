---
title: "IReferenceAppId 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId 介面
代表目前範圍中的應用程式的唯一識別碼的參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|取得指標所參考的應用程式的程式碼識別項的字串表示`IReferenceAppId`。|  
|`IReferenceAppId::put_CodeBase`|設定所參考的應用程式的程式碼識別碼`IReferenceAppId`。|  
|`IReferenceAppId::EnumAppPath`|取得的介面指標`IEnumReferenceIdentity`執行個體包含`IReferenceIdentity`代表這個成員的執行個體`IReferenceAppId`。|  
|`IReferenceAppId::get_SubscriptionId`|取得權杖識別碼的字串表示的指標，此訂用帳戶`IReferenceAppId`。|  
|`IReferenceAppId::put_SubscriptionId`|設定此訂用帳戶的語彙基元識別碼`IReferenceAppId`設為指定的字串值。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
