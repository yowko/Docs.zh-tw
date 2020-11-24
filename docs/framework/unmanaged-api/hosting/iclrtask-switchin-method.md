---
title: ICLRTask::SwitchIn 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: e98ae17d55c74d32844da96137c258d076ebc2db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691050"
---
# <a name="iclrtaskswitchin-method"></a>ICLRTask::SwitchIn 方法

通知 common language runtime (CLR) 目前 [ICLRTask](iclrtask-interface.md) 實例所代表的工作現在處於可操作的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a>參數  

 `threadHandle`  
 在實體執行緒的控制碼，目前實例所代表的工作正在其上 `ICLRTask` 執行。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SwitchIn` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|`SwitchIn` 在沒有先前呼叫 [SwitchOut 方法](iclrtask-switchout-method.md)的情況下呼叫。|  
  
## <a name="remarks"></a>備註  

 `threadHandle`參數代表作業系統執行緒的控制碼，此控制碼已排程目前實例所代表的工作 `ICLRTask` 。 如果此執行緒上發生模擬，您必須先呼叫 [IHostSecurityManager：： RevertToSelf](ihostsecuritymanager-reverttoself-method.md) ，才能在工作中切換。  
  
> [!NOTE]
> `SwitchIn`沒有先前呼叫的呼叫 `SwitchOut` 會失敗，並出現 HOST_E_INVALIDOPERATION 的 HRESULT 值。  
  
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
