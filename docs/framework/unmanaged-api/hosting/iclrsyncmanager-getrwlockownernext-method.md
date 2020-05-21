---
title: ICLRSyncManager::GetRWLockOwnerNext 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: e5a8f69e66bb4b6373aea2c753bff9351bff8128
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762483"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a>ICLRSyncManager::GetRWLockOwnerNext 方法
取得目前讀取器寫入器鎖定上封鎖的下一個[IHostTask](ihosttask-interface.md)實例。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>參數  
 `Iterator`  
 在使用[CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)的呼叫所建立的反覆運算器。  
  
 `ppOwnerHostTask`  
 脫銷下一個 `IHostTask` 正在等候鎖定的指標，如果沒有任何工作正在等候，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetRWLockOwnerNext`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 如果 `ppOwnerHostTask` 設定為 null，則反復專案會終止，而且主機應該呼叫[DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md)方法。  
  
> [!NOTE]
> CLR 會在上呼叫，以便在 `AddRef` `IHostTask` 主機保有 `ppOwnerHostTask` 指標時，阻止這項工作結束。 主機完成時，必須呼叫 `Release` 以遞減參考計數。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
