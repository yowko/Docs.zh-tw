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
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493158"
---
# <a name="metahost_config_flags-enumeration"></a>METAHOST_CONFIG_FLAGS 列舉
描述在 `pdwConfigFlags` [ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)方法的參數中傳回的可能旗標，指出 `useLegacyV2RuntimeActivationPolicy` 設定檔[ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)的專案中屬性的目前狀態和設定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|`useLegacyV2RuntimeActivationPolicy`屬性不存在於[ \<startup> 元素](../../configure-apps/file-schema/startup/startup-element.md)中。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|`useLegacyV2RuntimeActivationPolicy`屬性存在且設定為 `true` 。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|`useLegacyV2RuntimeActivationPolicy`屬性存在且設定為 `false` 。|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|將此遮罩套用至中傳回的值 `pdwConfigFlags` ，以取得與相關的值 `useLegacyV2RuntimeActivationPolicy` 。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Metahost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
- [GetRequestedRuntime 方法](iclrmetahostpolicy-getrequestedruntime-method.md)
- [\<startup>元素](../../configure-apps/file-schema/startup/startup-element.md)
