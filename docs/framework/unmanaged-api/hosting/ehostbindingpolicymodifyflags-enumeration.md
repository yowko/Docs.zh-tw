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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fa8cc15f77ff59e3d3c570341d9bba70cf1e953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags 列舉
可讓主機指定的重新導向時套用至目標組件的原則修改從來源組件，應執行 common language runtime (CLR) 類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|指定 CLR 會鏈結到目標組件的來源組件的原則值。|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|指定 CLR 會執行預設動作。|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|指定 CLR 會設定為最大值的目標組件的原則值。|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|指定 CLR 會取代目標組件的原則值的來源組件。|  
  
## <a name="remarks"></a>備註  
 [Iclrhostbindingpolicymanager:: Modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)方法使用的型別參數`EHostBindingPolicyModifyFlags`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
