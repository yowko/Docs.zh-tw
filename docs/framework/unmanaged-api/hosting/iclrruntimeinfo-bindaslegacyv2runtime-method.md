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
ms.openlocfilehash: d37ec8e17e62f58212a5f79f4d6b6aa75f57bf7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120262"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
將目前的執行時間系結至所有舊版 common language runtime （CLR）第2版啟用原則決策。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 Hresult：  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|任一系結成功，或此執行時間已系結為舊版 CLR 版本2啟用原則執行時間。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|不同的執行時間已系結至舊版 CLR 第2版啟用原則。|  
  
## <a name="remarks"></a>備註  
 如果目前的執行時間已系結至所有舊版 CLR 第2版啟用原則決策（例如，藉由在設定檔中使用[\<啟動 >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)專案上的 `useLegacyV2RuntimeActivationPolicy` 屬性），則這個方法不會傳回錯誤結果。相反地，結果是 S_OK，如同方法已成功系結舊版啟用原則一樣。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [\<startup> 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
