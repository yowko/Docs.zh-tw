---
title: IHostThreadPoolManager::SetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c79f18c1deec4183a5a736c5acf88e9a1fd8021
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749088"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a>IHostThreadPoolManager::SetMinThreads 方法
預期的要求中設定主應用程式必須維護的閒置執行緒的數目下限。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a>參數  
 `MinThreads`  
 [in]新執行緒的數目下限必須維護主機。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetMinThreads` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOTIMPL|主機並未提供的實作`SetMinThreads`。|  
  
## <a name="remarks"></a>備註  
 主機不需要提供的實作`SetMinThreads`。 在此情況下，它應該傳回 E_NOTIMPL 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
