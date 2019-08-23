---
title: ICLRSyncManager::GetMonitorOwner 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e08af840d1c4a654fa9b9ff8b2064f5265afaf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943247"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner 方法
取得擁有指定之 cookie 所識別之監視器的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>參數  
 `cookie`  
 在與監視相關聯的 cookie。  
  
 `ppOwnerHostTask`  
 脫銷目前擁有此監視器`IHostTask`之的指標, 如果沒有任何工作具有擁有權, 則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 主機通常會呼叫`GetMonitorOwner`作為鎖死偵測機制的一部分。 當使用[IHostSyncManager:: CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)的呼叫建立時, cookie 會與監視相關聯。  
  
> [!NOTE]
> 呼叫以釋放監視所基礎的事件可能會封鎖, 但不會鎖死, 如果對此方法的呼叫目前作用於與該監視相關聯的 cookie。 其他工作也可能會在嘗試取得此監視時封鎖。  
  
 `GetMonitorOwner`一律會立即傳回, 而且可以在呼叫`CreateMonitorEvent`之後隨時呼叫。 主機不需要等候, 直到工作在等候事件為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
