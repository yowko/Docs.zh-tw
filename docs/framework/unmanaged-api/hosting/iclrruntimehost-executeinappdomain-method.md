---
title: ICLRRuntimeHost::ExecuteInAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314ffb143e99f9490bcd4a6489f2afed314b7c2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768769"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain 方法
指定<xref:System.AppDomain>要執行指定的 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>參數  
 `AppDomainId`  
 [in]數字識別碼<xref:System.AppDomain>要執行指定的方法。  
  
 `pCallback`  
 [in]執行位於指定之函式指標<xref:System.AppDomain>。  
  
 `cookie`  
 [in]不透明的呼叫端配置的記憶體指標。 這個參數會傳遞由 common language runtime (CLR) 中，網域回呼。 它不是執行階段受管理的堆積記憶體;配置和存留期的這個記憶體是由呼叫者控制的。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `ExecuteInAppDomain` 可讓主機控制管理 over<xref:System.AppDomain>應該在執行指定的 managed 的方法。 您可以取得應用程式定義域的識別項，對應至值的值<xref:System.AppDomain.Id%2A>屬性，藉由呼叫[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
