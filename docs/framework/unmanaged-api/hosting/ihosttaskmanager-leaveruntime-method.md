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
ms.openlocfilehash: 855f8a5d3582bbad59301a344d8a51198c40a051
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673042"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime 方法

通知主機目前正在執行的工作即將將 common language runtime (CLR) ，然後輸入非受控碼。  
  
> [!IMPORTANT]
> 對應的 [IHostTaskManager：： EnterRuntime](ihosttaskmanager-enterruntime-method.md) 呼叫會通知主機目前正在執行的工作正在重新進入 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>參數  

 `target`  
 在要呼叫之非受控函式的對應可攜式可執行檔中的位址。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可完成要求的配置。|  
  
## <a name="remarks"></a>備註  

 不受管理程式碼的呼叫序列可以進行嵌套。 例如，下列清單描述的是對 `LeaveRuntime` 、 [IHostTaskManager：： ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)、 [IHostTaskManager：： ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫順序，以及 `IHostTaskManager::EnterRuntime` 允許主機識別嵌套層的假設狀況。  
  
|動作|對應的方法呼叫|  
|------------|-------------------------------|  
|Managed Visual Basic 可執行檔會使用平台叫用呼叫以 C 撰寫的非受控函式。|`IHostTaskManager::LeaveRuntime`|  
|非受控 C 函式會在以 c # 撰寫的 managed DLL 中呼叫方法。|`IHostTaskManager::ReverseEnterRuntime`|  
|Managed c # 函式會呼叫另一個以 C 撰寫的非受控函式，也會使用平台叫用。|`IHostTaskManager::LeaveRuntime`|  
|第二個非受控函式會將執行傳回給 c # 函式。|`IHostTaskManager::EnterRuntime`|  
|C # 函式會將執行傳回至第一個非受控函數。|`IHostTaskManager::ReverseLeaveRuntime`|  
|第一個非受控函式會將執行傳回給 Visual Basic 程式。|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
