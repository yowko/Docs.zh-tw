---
title: IHostGCManager 介面
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eaf5a0061b068d9adea3f6aeb28f9b6bb20c3174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710246"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager 介面
提供方法，以通知主機藉由將 common language runtime (CLR) 記憶體回收機制中的事件。  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[SuspensionEnding 方法](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|主應用程式，CLR 會繼續已暫止記憶體回收的執行緒上的工作執行。|  
|[SuspensionStarting 方法](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|CLR 會暫停執行的工作，以執行記憶體回收通知主機。|  
|[ThreadIsBlockingForSuspension 方法](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|主應用程式在進行方法呼叫的執行緒即將封鎖記憶體回收。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
