---
title: ICLRSyncManager::CreateRWLockOwnerIterator 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c742410da8e7dbce53b53978516ab94243455849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763707"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator 方法
Common language runtime (CLR) 建立迭代器，用來判斷一組工作正在等候讀取器-寫入器鎖定主機的要求。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>參數  
 `cookie`  
 [in]使用所需的讀取器-寫入器鎖定相關聯的 cookie。  
  
 `pIterator`  
 [out]指標迭代器可以傳遞給[GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)並[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator` 目前正在執行的 managed 程式碼的執行緒上呼叫。|  
  
## <a name="remarks"></a>備註  
 主機通常會呼叫`CreateRWLockOwnerIterator`， `DeleteRWLockOwnerIterator`，和`GetRWLockOwnerNext`死結偵測期間的方法。 主應用程式會負責確保 reader-writer 鎖定仍然有效，因為 CLR 並不會嘗試維持 reader-writer 鎖定。 數種策略可供主應用程式，以確保有效性的鎖定：  
  
- 主應用程式可能會封鎖讀取器-寫入器鎖定上發行的呼叫 (例如[ihostsemaphore:: Releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) 同時確保此區塊不會造成死結。  
  
- 主機可以封鎖等候讀取器-寫入器鎖定相關聯的事件物件上的結束，確定此區塊不會造成死結。  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator` 必須只能在目前正在執行 unmanaged 程式碼的執行緒上呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
