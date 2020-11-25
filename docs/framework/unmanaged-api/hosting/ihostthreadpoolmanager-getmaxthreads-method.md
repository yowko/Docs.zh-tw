---
title: IHostThreadPoolManager::GetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
ms.openlocfilehash: 3aecebe2803d3a795db801491d0f60a5eb7c00ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730782"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a>IHostThreadPoolManager::GetMaxThreads 方法

取得主機線上程集區中同時維護的執行緒數目上限。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a>參數  

 `pdwMaxWorkerThreads`  
 擴展主機線上程集區中維護之執行緒數目上限的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetMaxThreads` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR ( 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOTIMPL|主機未提供的實作為 `GetMaxThreads` 。|  
  
## <a name="remarks"></a>備註  

 CLR 會呼叫 `GetMaxThreads` 來判斷線程集區中的執行緒總數。 [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md)方法會取得目前未處理工作專案的執行緒數目。 所有高於參數傳回值的要求都會 `pdwMaxWorkerThreads` 保持佇列，直到執行緒變成可用為止。  
  
 如果主機未提供的實 `GetMaxThreads` 值，它應該會傳回 E_NOTIMPL 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads 方法](ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads 方法](ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager 介面](ihostthreadpoolmanager-interface.md)
