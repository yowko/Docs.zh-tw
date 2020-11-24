---
title: EHostBindingPolicyModifyFlags 列舉
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: ec64f9bec0ee9b63796958b17c7f10b87692f1d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686138"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags 列舉

允許主機指定 common language runtime (CLR) 在將原則修改從來源元件套用至目標群組件時所應執行的重新導向類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|指定 CLR 會將來源元件的原則值鏈至目標群組件的原則值。|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|指定 CLR 將執行預設動作。|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|指定 CLR 將目標群組件的原則值設定為最大值。|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|指定 CLR 會將目標群組件的原則值取代為來源元件的原則值。|  
  
## <a name="remarks"></a>備註  

 [ICLRHostBindingPolicyManager：： ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)方法接受型別為的參數 `EHostBindingPolicyModifyFlags` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostBindingPolicyManager 介面](iclrhostbindingpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
