---
title: IHostSyncManager::CreateAutoEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803507"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a>IHostSyncManager::CreateAutoEvent 方法
建立自動重設事件物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEvent`  
 脫銷主機所實[IHostAutoEvent](ihostautoevent-interface.md)實例的位址指標，如果無法建立事件物件，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CreateAutoEvent`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來建立要求的事件物件。|  
  
## <a name="remarks"></a>備註  
 `CreateAutoEvent`建立自動事件物件，其狀態會在等候的執行緒釋放之後自動變更為非信號。 這個方法會 `CreateEvent` 使用 `false` 針對參數所指定的值來鏡像 Win32 函數。 `bManualReset`  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
