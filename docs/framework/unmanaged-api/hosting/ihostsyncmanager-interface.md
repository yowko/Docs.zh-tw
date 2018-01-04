---
title: "IHostSyncManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager 介面
提供方法讓 common language runtime (CLR) 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateAutoEvent 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|建立的自動重設事件物件。|  
|[CreateCrst 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|建立關鍵區段進行同步處理物件。|  
|[CreateCrstWithSpinCount 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|建立關鍵區段物件具有微調計數進行同步處理。|  
|[CreateManualEvent 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|建立手動重設事件物件。|  
|[CreateMonitorEvent 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|建立受監視的自動重設事件物件。|  
|[CreateRWLockReaderEvent 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|建立手動重設事件物件的讀取器鎖定的實作。|  
|[CreateRWLockWriterEvent 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|建立自動重設事件物件的寫入器鎖定的實作。|  
|[CreateSemaphore 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)作為等候事件信號的 CLR 物件。|  
|[SetCLRSyncManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|設定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)與目前的執行個體`IHostSyncManager`執行個體。|  
  
## <a name="remarks"></a>備註  
 CLR 會探索主應用程式的實作`IHostSyncManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法`IID`IID_IHostSyncManager。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
