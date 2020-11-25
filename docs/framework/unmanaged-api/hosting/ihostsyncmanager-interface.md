---
title: IHostSyncManager 介面
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: 8a5fc42191634a2e5a441baecc4b78212ffad687
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720486"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager 介面

提供方法，讓 common language runtime (CLR) 透過呼叫主機而非使用 Win32 同步處理函式來建立同步處理原始物件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateAutoEvent 方法](ihostsyncmanager-createautoevent-method.md)|建立自動重設事件物件。|  
|[CreateCrst 方法](ihostsyncmanager-createcrst-method.md)|建立同步處理的重要區段物件。|  
|[CreateCrstWithSpinCount 方法](ihostsyncmanager-createcrstwithspincount-method.md)|使用微調計數來建立重要區段物件以進行同步處理。|  
|[CreateManualEvent 方法](ihostsyncmanager-createmanualevent-method.md)|建立手動重設事件物件。|  
|[CreateMonitorEvent 方法](ihostsyncmanager-createmonitorevent-method.md)|建立受監視的自動重設事件物件。|  
|[CreateRWLockReaderEvent 方法](ihostsyncmanager-createrwlockreaderevent-method.md)|建立手動重設的事件物件，以執行讀取器鎖定。|  
|[CreateRWLockWriterEvent 方法](ihostsyncmanager-createrwlockwriterevent-method.md)|建立自動重設事件物件，以執行寫入器鎖定。|  
|[CreateSemaphore 方法](ihostsyncmanager-createsemaphore-method.md)|建立 [IHostSemaphore](ihostsemaphore-interface.md) 物件，讓 CLR 用來作為等候事件的信號。|  
|[SetCLRSyncManager 方法](ihostsyncmanager-setclrsyncmanager-method.md)|設定要與目前實例相關聯的 [ICLRSyncManager](iclrsyncmanager-interface.md) 實例 `IHostSyncManager` 。|  
  
## <a name="remarks"></a>備註  

 CLR 會藉 `IHostSyncManager` 由呼叫 [IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md) 方法和 IID_IHostSyncManager 來探索主機的實 `IID` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
