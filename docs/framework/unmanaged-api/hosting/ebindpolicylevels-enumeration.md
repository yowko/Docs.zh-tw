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
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726843"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列舉

提供旗標來指定要套用或修改元件原則的層級。  
  
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|指定應在系統管理員層級套用原則。|  
|`ePolicyLevelApp`|指定應在應用層級套用原則。|  
|`ePolicyLevelHost`|指定應在主機層級套用原則。|  
|`ePolicyLevelNone`|未指定原則層級旗標。|  
|`ePolicyLevelPublisher`|指定應在發行者層級套用原則。|  
|`ePolicyLevelRetargetable`|指定原則應該適用于變數層級。|  
|`ePolicyPortability`|指定原則應該支援 .NET Framework 元件的執行之間的可攜性。 請參閱 [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) 設定檔元素。|  
|`ePolicyUnifiedToCLR`|指定原則應該與 common language runtime (CLR) 整合。|  
  
## <a name="remarks"></a>備註  

 此列舉會傳遞給 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) 介面的方法，以指定應用程式原則的變更。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
