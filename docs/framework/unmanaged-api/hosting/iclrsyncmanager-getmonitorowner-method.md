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
ms.openlocfilehash: e1c986de068cd79ae3662c82ed24906d42bf2780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759031"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner 方法
取得[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)擁有所指定的 cookie 識別監視器的執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>參數  
 `cookie`  
 [in]與監視相關聯的 cookie。  
  
 `ppOwnerHostTask`  
 [out]指標`IHostTask`目前擁有監視器，則為 null 如果沒有工作具有擁有權。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 主機通常會呼叫`GetMonitorOwner`死結偵測機制的一部分。 建立藉由呼叫時，cookie 是與監視相關聯[ihostsyncmanager:: Createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)。  
  
> [!NOTE]
>  可能會封鎖呼叫釋放基準監視的事件，但不是會鎖死，如果此方法的呼叫正在目前作用中與該監視器相關聯的 cookie。 如果嘗試取得此監視，也可能會封鎖其他工作。  
  
 `GetMonitorOwner` 一律會立即傳回，而且可以在呼叫之後任何時間呼叫`CreateMonitorEvent`。 主應用程式不需要等候，直到工作在等候事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
