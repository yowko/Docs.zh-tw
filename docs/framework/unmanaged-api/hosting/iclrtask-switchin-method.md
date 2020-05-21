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
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762925"
---
# <a name="iclrtaskswitchin-method"></a>ICLRTask::SwitchIn 方法
通知 common language runtime （CLR）目前[ICLRTask](iclrtask-interface.md)實例所代表的工作現在處於可運作狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a>參數  
 `threadHandle`  
 在目前實例所代表之工作執行所在之實體執行緒的控制碼 `ICLRTask` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SwitchIn`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|`SwitchIn`在沒有先前呼叫[SwitchOut 方法](iclrtask-switchout-method.md)的情況下呼叫。|  
  
## <a name="remarks"></a>備註  
 `threadHandle`參數代表已排程目前實例所代表之工作的作業系統執行緒控制碼 `ICLRTask` 。 如果此執行緒發生模擬，您必須先呼叫[IHostSecurityManager：： RevertToSelf](ihostsecuritymanager-reverttoself-method.md) ，才能在工作中切換。  
  
> [!NOTE]
> 呼叫 `SwitchIn` 而不使用先前的呼叫 `SwitchOut` 會失敗，且 HRESULT 值為 HOST_E_INVALIDOPERATION。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
