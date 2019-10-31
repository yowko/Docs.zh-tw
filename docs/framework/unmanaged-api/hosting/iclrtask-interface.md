---
title: ICLRTask 介面
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132637"
---
# <a name="iclrtask-interface"></a>ICLRTask 介面
提供的方法可讓主機提出 common language runtime （CLR）的要求，或提供相關聯工作的通知給 CLR。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|要求 CLR 中止目前 `ICLRTask` 實例所代表的工作。|  
|[ExitTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|通知 CLR，與目前 `ICLRTask` 實例相關聯的工作正在結束，並嘗試正常關閉工作。|  
|[GetMemStats 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|取得目前 `ICLRTask` 實例所代表之工作使用記憶體資源的統計資訊。|  
|[LocksHeld 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|取得目前保留在工作上的鎖定數目。|  
|[NeedsPriorityScheduling 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|取得值，指出主機是否應指派高優先順序來重新排定目前 `ICLRTask` 實例所代表的工作。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|通知 CLR 主機已完成工作，並讓 CLR 重複使用目前的 `ICLRTask` 實例，以代表另一個工作。|  
|[RudeAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|導致 CLR 立即中止目前 `ICLRTask` 實例所表示的工作，而不保證會執行完成項。|  
|[SetTaskIdentifier 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|設定目前 `ICLRTask` 實例所代表之工作的唯一識別碼，以用於偵錯工具。|  
|[SwitchIn 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|通知 CLR，目前 `ICLRTask` 實例所代表的工作處於可運作狀態。|  
|[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|通知 CLR，目前 `ICLRTask` 實例所代表的工作已不再處於可運作狀態。|  
|[YieldTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|要求 CLR 將處理器時間提供給其他工作使用。 CLR 不保證工作會進入可能會產生處理時間的狀態。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask` 是 CLR 工作的標記法。 在程式碼執行期間的任何時間點，可以將工作描述為正在執行或等待執行。 主機會呼叫 `ICLRTask::SwitchIn` 方法，以通知 CLR 目前 `ICLRTask` 實例所代表的工作現在處於可運作狀態。 呼叫 `ICLRTask::SwitchIn`之後，只要呼叫[IHostTaskManager：： BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)和 IHostTaskManager：：，主機就可以在任何作業系統執行緒上排程工作，但執行時間需要執行緒親和性的情況除外[。EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)方法。 一些時間之後，作業系統可能會決定從執行緒中移除工作，並將它置於非執行中的狀態。 例如，當工作在同步處理原始物件上封鎖，或等候 i/o 作業完成時，就可能發生這種情況。 主機會呼叫[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)來通知 CLR，目前 `ICLRTask` 實例所代表的工作已不再處於可運作狀態。  
  
 工作通常會在程式碼執行結束時終止。 此時，主機會呼叫 `ICLRTask::ExitTask` 以終結相關聯的 `ICLRTask`。 不過，也可以使用 `ICLRTask::Reset`的呼叫來回收工作，這樣可讓 `ICLRTask` 實例再次使用。 這種方法可防止重複建立和終結實例的額外負荷。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
