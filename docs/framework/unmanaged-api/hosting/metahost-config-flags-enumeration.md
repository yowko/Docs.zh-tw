---
title: METAHOST_CONFIG_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 07cab119810c4da25d16a4ad7c13f2d2bda16455
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140306"
---
# <a name="metahost_config_flags-enumeration"></a>METAHOST_CONFIG_FLAGS 列舉
描述在[ICLRMetaHostPolicy：： GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法的 `pdwConfigFlags` 參數中傳回的可能旗標，指出在的[\<啟動 >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)專案中，`useLegacyV2RuntimeActivationPolicy` 屬性的目前狀態和設定。設定檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|`useLegacyV2RuntimeActivationPolicy` 屬性不存在於[\<啟動 > 元素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)中。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|`useLegacyV2RuntimeActivationPolicy` 屬性已存在，且設定為 `true`。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|`useLegacyV2RuntimeActivationPolicy` 屬性已存在，且設定為 `false`。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|將此遮罩套用到 `pdwConfigFlags` 中傳回的值，以取得與 `useLegacyV2RuntimeActivationPolicy`相關的值。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Metahost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [\<startup> 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
