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
ms.openlocfilehash: a2cb82d8071518af4d4bc3276871f3846a5a5693
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687064"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner 方法

取得擁有指定之 cookie 所識別之監視的 [IHostTask](ihosttask-interface.md) 實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>參數  

 `cookie`  
 在與監視器相關聯的 cookie。  
  
 `ppOwnerHostTask`  
 擴展 `IHostTask` 目前擁有監視之的指標，如果沒有任何工作擁有擁有權，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 主機通常會在 `GetMonitorOwner` 鎖死偵測機制中呼叫。 當您使用 [IHostSyncManager：： CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md)的呼叫來建立時，cookie 會與監視器相關聯。  
  
> [!NOTE]
> 如果呼叫這個方法的呼叫目前在與該監視相關聯的 cookie 上生效，則呼叫可能會封鎖監視器基礎的事件，但不會產生鎖死。 其他工作也可能會在嘗試取得此監視器時封鎖。  
  
 `GetMonitorOwner` 一律會立即傳回，而且可以在呼叫之後隨時呼叫 `CreateMonitorEvent` 。 主機不需要等到工作正在等候事件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
