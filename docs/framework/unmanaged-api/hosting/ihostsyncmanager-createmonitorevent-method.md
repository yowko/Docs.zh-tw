---
title: IHostSyncManager::CreateMonitorEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803313"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a>IHostSyncManager::CreateMonitorEvent 方法
建立受監視的自動重設事件物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>參數  
 `cookie`  
 在要與事件物件產生關聯的 cookie。  
  
 `ppEvent`  
 脫銷[IHostAutoEvent](ihostautoevent-interface.md)實例位址的指標，如果無法建立事件物件則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CreateMonitorEvent`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來建立要求的事件物件。|  
  
## <a name="remarks"></a>備註  
 `CreateMonitorEvent`傳回 `IHostAutoEvent` CLR 在其 managed 類型的實作為中使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 。 這個方法會鏡像 Win32 函式 `CreateEvent` ，並為 `false` 參數指定的值 `bManualReset` 。  
  
 主機可以使用 cookie，藉由呼叫[ICLRSyncManager：： GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md)方法來判斷哪一項工作正在等候監視器。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
