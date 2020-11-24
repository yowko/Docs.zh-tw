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
ms.openlocfilehash: 5ecc42950775a620796a1c775e5f088f461a12c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690820"
---
# <a name="iclrtask-interface"></a>ICLRTask 介面

提供的方法可讓主控制項要求 (CLR) 的 common language runtime，或提供相關聯工作的通知給 CLR。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](iclrtask-abort-method.md)|要求 CLR 中止目前實例所代表的工作 `ICLRTask` 。|  
|[ExitTask 方法](iclrtask-exittask-method.md)|通知 CLR，與目前實例相關聯的工作 `ICLRTask` 已結束，並嘗試正常關閉工作。|  
|[GetMemStats 方法](iclrtask-getmemstats-method.md)|取得目前實例所代表之工作使用記憶體資源的統計資訊 `ICLRTask` 。|  
|[LocksHeld 方法](iclrtask-locksheld-method.md)|取得目前保留在工作上的鎖定數目。|  
|[NeedsPriorityScheduling 方法](iclrtask-needspriorityscheduling-method.md)|取得值，指出主機是否應指派高優先順序，以重新排程目前實例所代表的工作 `ICLRTask` 。|  
|[Reset 方法](iclrtask-reset-method.md)|通知 CLR 主機已完成工作，並讓 CLR 重複使用目前的 `ICLRTask` 實例來表示另一個工作。|  
|[RudeAbort 方法](iclrtask-rudeabort-method.md)|使 CLR 立即中止目前實例所代表的工作 `ICLRTask` ，而不保證會執行完成項。|  
|[SetTaskIdentifier 方法](iclrtask-settaskidentifier-method.md)|設定目前實例所代表之工作的唯一識別碼 `ICLRTask` ，以用於偵錯工具。|  
|[SwitchIn 方法](iclrtask-switchin-method.md)|通知 CLR，目前實例所代表的工作處於 `ICLRTask` 可操作的狀態。|  
|[SwitchOut 方法](iclrtask-switchout-method.md)|通知 CLR，目前實例所代表的工作 `ICLRTask` 不再處於可操作的狀態。|  
|[YieldTask 方法](iclrtask-yieldtask-method.md)|要求 CLR 讓處理器時間可供其他工作使用。 CLR 不保證會將工作置於可產生處理時間的狀態。|  
  
## <a name="remarks"></a>備註  

 `ICLRTask`是 CLR 工作的標記法。 在程式碼執行期間的任何時間點，都可以將工作描述為正在執行或等候執行。 主機 `ICLRTask::SwitchIn` 會呼叫方法，以通知 CLR 目前實例所代表的工作 `ICLRTask` 現在處於可操作的狀態。 在呼叫之後 `ICLRTask::SwitchIn` ，主機可以在任何作業系統執行緒上排程工作，但在執行時間需要執行緒親和性的情況下（如呼叫 [IHostTaskManager：： BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md) 和 [IHostTaskManager：： EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md) 方法所指定）。 稍後，作業系統可能會決定從執行緒中移除工作，並將它置於非執行狀態。 例如，當工作在同步處理原始物件上封鎖或等候 i/o 作業完成時，就可能發生這種情況。 主機會呼叫 [SwitchOut](iclrtask-switchout-method.md) 來通知 CLR，目前實例所代表的工作 `ICLRTask` 不再處於可操作的狀態。  
  
 工作通常會在程式碼執行結束時終止。 屆時，主機會呼叫以終結 `ICLRTask::ExitTask` 相關聯的 `ICLRTask` 。 不過，也可以使用的呼叫來回收 `ICLRTask::Reset` 工作，這樣可讓 `ICLRTask` 實例再次使用。 這種方法可避免重複建立和終結實例的額外負荷。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
- [ICLRTask2 介面](iclrtask2-interface.md)
