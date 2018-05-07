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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba53e4af114773a347d15b7308dc4c3567154e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtask-interface"></a>ICLRTask 介面
提供方法，讓主應用程式提出要求的 common language runtime (CLR)，或提供相關聯的工作有關 clr 的通知。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR 會中止工作的要求，目前`ICLRTask`執行個體所表示。|  
|[ExitTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|通知與目前的工作相關聯的 CLR`ICLRTask`執行個體即將結束，並嘗試依正常程序關閉的工作。|  
|[GetMemStats 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|取得表示由目前的工作所使用的記憶體資源統計資訊`ICLRTask`執行個體。|  
|[LocksHeld 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|取得目前工作上保留的鎖定數目。|  
|[NeedsPriorityScheduling 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|取得值，表示主機是否應將高優先順序指派給重新排定表示由目前的工作`ICLRTask`執行個體。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|通知主機已完成工作，並啟用 CLR，若要重複使用目前的 CLR`ICLRTask`來代表另一項工作的執行個體。|  
|[RudeAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|造成 CLR 中止表示由目前的工作`ICLRTask`立即執行個體，但不保證將會執行完成項。|  
|[SetTaskIdentifier 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|設定表示由目前的工作的唯一識別碼`ICLRTask`執行個體，以用於偵錯。|  
|[SwitchIn 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|通知代表由目前的工作 CLR`ICLRTask`執行個體處於運作狀態。|  
|[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|通知代表由目前的工作 CLR`ICLRTask`執行個體已不再處於運作狀態。|  
|[YieldTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|要求 CLR 讓處理器時間可供其他工作。 Clr 不保證會將該工作放在狀態，它可以在其中產生處理時間。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask` Clr 工作的表示法。 在任何時間點執行程式碼，工作可以描述為正在執行，或是等候執行。 主機會呼叫`ICLRTask::SwitchIn`方法來通知 CLR，工作的目前`ICLRTask`執行個體表示現在處於運作狀態。 若要在呼叫之後`ICLRTask::SwitchIn`，主機可以上排定工作的任何作業系統執行緒，除了在執行階段需要的執行緒相似性，呼叫所指定位置的情況下[ihosttaskmanager:: Beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)和[Ihosttaskmanager:: Endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)方法。 稍後，作業系統可能會決定從執行緒中移除工作，並將它放在非執行狀態。 比方說，這可能會發生工作同步處理原始物件，會封鎖或等候 I/O 作業完成時。 主機會呼叫[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)通知代表由目前的工作 CLR`ICLRTask`執行個體已不再處於運作狀態。  
  
 工作通常會終止執行程式碼的結尾。 此時，主機會呼叫`ICLRTask::ExitTask`終結相關聯`ICLRTask`。 不過，工作可以也被回收，做法是透過呼叫`ICLRTask::Reset`，可讓`ICLRTask`重複使用的執行個體。 這種方法可避免重複建立和終結執行個體的額外負荷。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
