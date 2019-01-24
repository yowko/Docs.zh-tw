---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b0f4b184a11e769291c64d83d11d57b5b3d19c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498800"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromStream 方法
取得指定的資料流中的組件的標準組件身分識別資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStream`  
 [in]要評估的組件資料流。  
  
 `dwFlags`  
 [in]供未來擴充。 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime (CLR) 支援的唯一值。  
  
 `pwzBuffer`  
 [out]包含的不透明的組件身分識別資料的緩衝區。  
  
 `pcchBufferSize`  
 [in、 out]大小`pwzBuffer`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法傳回成功。|  
|E_INVALIDARG|提供`pStream`為 null。|  
|ERROR_INSUFFICIENT_BUFFER|大小`pwzBuffer`太小。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
