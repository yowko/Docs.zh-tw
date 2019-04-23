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
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088197"
---
# <a name="iclrtask-interface"></a>ICLRTask 介面
提供方法，可讓主應用程式提出要求的 common language runtime (CLR)，或以用於 CLR 有關相關聯的工作提供通知。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR 會中止工作的要求，目前`ICLRTask`執行個體表示。|  
|[ExitTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|通知與目前的工作相關聯的 CLR`ICLRTask`執行個體即將結束，並會嘗試依正常程序關閉工作。|  
|[GetMemStats 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|取得表示目前的工作上使用的記憶體資源的統計資訊`ICLRTask`執行個體。|  
|[LocksHeld 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|取得目前工作上保留的鎖定數目。|  
|[NeedsPriorityScheduling 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|取得值，指出主應用程式是否應該重新排定表示由目前的工作指派高優先順序`ICLRTask`執行個體。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|告訴 CLR，主應用程式已完成的工作，並可讓重複使用目前的 CLR`ICLRTask`來代表另一項工作的執行個體。|  
|[RudeAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|造成 CLR 中止表示由目前的工作`ICLRTask`立即執行個體，不保證，則會執行完成項。|  
|[SetTaskIdentifier 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|設定由目前工作的唯一識別碼`ICLRTask`執行個體，以用於偵錯。|  
|[SwitchIn 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|通知工作表示由目前的 CLR`ICLRTask`執行個體處於運作狀態。|  
|[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|通知工作表示由目前的 CLR`ICLRTask`執行個體已不再處於運作狀態。|  
|[YieldTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|要求的 CLR 讓處理器時間可供其他工作。 CLR 並不保證工作將會處於的狀態，它可以在其中產生的處理時間。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask` Clr 工作的表示法。 在任何時間點在程式碼執行期間，工作可以描述為正在執行，或是等候執行。 主機會呼叫`ICLRTask::SwitchIn`方法來通知 CLR，工作的目前`ICLRTask`執行個體表示現在處於運作狀態。 若要在呼叫之後`ICLRTask::SwitchIn`，主應用程式可以將工作排定在任何作業系統執行緒上，除了在執行階段需要執行緒相似性，藉由呼叫指定的位置的情況下[ihosttaskmanager:: Beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)和[Ihosttaskmanager:: Endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)方法。 稍後，作業系統可能會決定從執行緒中移除工作，並將它放在非執行中狀態。 比方說，這可能是工作同步處理原始物件，會封鎖或等候 I/O 作業完成時。 主機會呼叫[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)來通知 CLR 表示由目前工作`ICLRTask`執行個體已不再處於運作狀態。  
  
 工作通常會終止執行程式碼的結尾。 此時，主機會呼叫`ICLRTask::ExitTask`終結關聯`ICLRTask`。 不過，工作可以也被回收，做法是透過呼叫`ICLRTask::Reset`，可讓`ICLRTask`可再次使用的執行個體。 這種方法可避免重複建立和終結執行個體的額外負荷。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
