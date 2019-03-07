---
title: IHostTaskManager::LeaveRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2059657a6f4543ee29d795ecae7b93b72876fdf4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474627"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime 方法
主應用程式目前正在執行的工作是要將 common language runtime (CLR) 並輸入 unmanaged 程式碼。  
  
> [!IMPORTANT]
>  對應呼叫[ihosttaskmanager:: Enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)主應用程式目前正在執行的工作重新進入 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>參數  
 `target`  
 [in]呼叫 unmanaged 函式對應可攜式執行檔內的位址。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可完成要求的配置。|  
  
## <a name="remarks"></a>備註  
 與 unmanaged 程式碼的呼叫序列可以是巢狀。 例如，下列清單描述的假設性情況的呼叫順序`LeaveRuntime`， [ihosttaskmanager:: Reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)， [ihosttaskmanager:: Reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)，和`IHostTaskManager::EnterRuntime`可讓主機識別巢狀層級。  
  
|動作|對應的方法呼叫|  
|------------|-------------------------------|  
|受管理的 Visual Basic 可執行檔呼叫 unmanaged 函式以 C 撰寫使用平台叫用。|`IHostTaskManager::LeaveRuntime`|  
|Unmanaged 的 C 函式呼叫的方法中撰寫的 managed DLL C#。|`IHostTaskManager::ReverseEnterRuntime`|  
|ManagedC#函式會呼叫另一個以 C 撰寫的 unmanaged 函式，也使用平台叫用。|`IHostTaskManager::LeaveRuntime`|  
|第二個 unmanaged 函式會傳回執行C#函式。|`IHostTaskManager::EnterRuntime`|  
|C#函式會傳回第一個非受控函式執行。|`IHostTaskManager::ReverseLeaveRuntime`|  
|第一個非受控函式執行傳回 Visual Basic 程式。|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
