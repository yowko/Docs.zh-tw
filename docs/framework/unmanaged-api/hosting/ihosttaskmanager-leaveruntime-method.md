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
ms.openlocfilehash: 8b2e8e636915b3921fcd727fc78a3fb18fc69104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959031"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime 方法
通知主機目前正在執行的工作即將離開 common language runtime (CLR), 並輸入非受控碼。  
  
> [!IMPORTANT]
> 對[IHostTaskManager:: EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)的對應呼叫, 會通知主機目前正在執行的工作是重新進入 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>參數  
 `target`  
 在要呼叫之非受控函式的對應可攜式可執行檔內的位址。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來完成要求的配置。|  
  
## <a name="remarks"></a>備註  
 不受管理程式碼的呼叫序列可以進行嵌套。 例如, 下列清單描述一種假設的情況, 其中的呼叫`LeaveRuntime`順序為[IHostTaskManager:: ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), 並`IHostTaskManager::EnterRuntime`允許主機識別嵌套層。  
  
|動作|對應的方法呼叫|  
|------------|-------------------------------|  
|Managed Visual Basic 可執行檔會使用平台叫用, 呼叫以 C 撰寫的非受控函式。|`IHostTaskManager::LeaveRuntime`|  
|非受控 C 函式會在以C#撰寫的 managed DLL 中呼叫方法。|`IHostTaskManager::ReverseEnterRuntime`|  
|Managed C#函式會呼叫以 C 撰寫的另一個非受控函式, 也會使用平台叫用。|`IHostTaskManager::LeaveRuntime`|  
|第二個非受控函式會C#將執行傳回函式。|`IHostTaskManager::EnterRuntime`|  
|C#函式會將執行傳回第一個非受控函式。|`IHostTaskManager::ReverseLeaveRuntime`|  
|第一個非受控函式會將執行傳回給 Visual Basic 程式。|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
