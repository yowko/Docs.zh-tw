---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c85888e9d29e7b3ae6ad76d1e534e08a4603ed2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499021"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
將所有舊版 common language runtime (CLR) 第 2 版啟用原則決策的目前執行階段的繫結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 Hresult:  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|繫結成功，或此執行階段已繫結為舊版 CLR 版本 2 的啟用原則執行階段。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|不同的執行階段已經繫結到舊版的 CLR 版本 2 的啟用原則。|  
  
## <a name="remarks"></a>備註  
 如果目前的執行階段已繫結的所有舊版 CLR 第 2 版啟用原則決策 (例如，藉由使用`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔中)，這個方法不會傳回錯誤結果;相反地，結果會是 s_ok 時，就像它是如果方法已成功繫結舊版啟用原則。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [\<startup> 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
