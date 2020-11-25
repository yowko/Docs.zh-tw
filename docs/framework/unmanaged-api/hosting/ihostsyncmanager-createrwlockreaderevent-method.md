---
title: IHostSyncManager::CreateRWLockReaderEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: 7c9bf2186d3dc4500694225ea4023df3609b9010
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704379"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a>IHostSyncManager::CreateRWLockReaderEvent 方法

建立手動重設的事件物件，以執行讀取器鎖定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>參數  

 `bInitialState`  
 [in] `true` ，如果 `ppEvent` 應該收到信號，則為，否則為 `false` 。  
  
 `cookie`  
 在與讀取器鎖定相關聯的 cookie。  
  
 `ppEvent`  
 擴展 [IHostManualEvent](ihostmanualevent-interface.md) 實例位址的指標，如果無法建立事件物件，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CreateRWLockReaderEvent` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來建立要求的事件物件。|  
  
## <a name="remarks"></a>備註  

 CLR 會呼叫 `CreateRWLockReaderEvent` 來取得實例的參考， `IHostManualEvent` 以在其讀取器鎖定的執行中使用。 主機可以使用 cookie 來判斷哪些工作正在等候讀取器鎖定，方法是查詢 [ICLRSyncManager](iclrsyncmanager-interface.md) 介面。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostManualEvent 介面](ihostmanualevent-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
