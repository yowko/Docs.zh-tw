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
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136556"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列舉
提供旗標，以指定要套用或修改元件原則的層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|指定應該在系統管理員層級套用原則。|  
|`ePolicyLevelApp`|指定應該在應用層級套用原則。|  
|`ePolicyLevelHost`|指定應該在主機層級套用原則。|  
|`ePolicyLevelNone`|不指定原則層級旗標。|  
|`ePolicyLevelPublisher`|指定應該在發行者層級套用原則。|  
|`ePolicyLevelRetargetable`|指定原則應該適用于變數層級。|  
|`ePolicyPortability`|指定原則應該支援 .NET Framework 元件的執行之間的可攜性。 請參閱[\<supportportability> >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)設定檔元素。|  
|`ePolicyUnifiedToCLR`|指定應該與 common language runtime （CLR）的原則一致。|  
  
## <a name="remarks"></a>備註  
 此列舉會傳遞給[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面的方法，以指定應用程式原則中的變更。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
