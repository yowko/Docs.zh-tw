---
title: IHostTaskManager::SetUILocale 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132935"
---
# <a name="ihosttaskmanagersetuilocale-method"></a>IHostTaskManager::SetUILocale 方法
通知主機 common language runtime （CLR）已變更目前正在執行之工作的使用者介面（UI）地區設定或文化特性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>參數  
 `lcid`  
 在地區設定識別碼值，對應至新指派的地理文化特性和語言。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `SetUILocale`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOTIMPL|主機不允許受管理的使用者程式碼變更 UI 文化特性。|  
  
## <a name="remarks"></a>備註  
 當 managed 程式碼變更 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> 屬性的值時，執行時間會呼叫 `SetUILocale`。 這個方法可讓主機執行任何可能對地區設定同步處理的機制。 如果主機不允許從 managed 程式碼變更 UI 地區設定，或未執行同步處理地區設定的機制，則應該從這個方法傳回 E_NOTIMPL。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
