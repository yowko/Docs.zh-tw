---
title: EBindPolicyLevels 列舉
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8f2b08662e719a3308a62ab5b60f5dc490f2a6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142203"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列舉
提供旗標指定要套用或修改的組件原則的層級。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|指定原則應該套用系統管理員層級。|  
|`ePolicyLevelApp`|指定原則應該套用應用程式層級。|  
|`ePolicyLevelHost`|指定原則應該套用在主機層級。|  
|`ePolicyLevelNone`|不指定原則層級旗標。|  
|`ePolicyLevelPublisher`|指定原則應該套用在發行者層級。|  
|`ePolicyLevelRetargetable`|指定變數的層級應該是適用原則。|  
|`ePolicyPortability`|指定原則應該支援的.NET Framework 組件實作之間的可攜性。 請參閱[ \<Supportportability> >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)組態檔項目。|  
|`ePolicyUnifiedToCLR`|指定原則應該進行整合的 common language runtime (CLR)。|  
  
## <a name="remarks"></a>備註  
 此列舉會傳遞至方法[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面來指定應用程式原則中的變更。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
