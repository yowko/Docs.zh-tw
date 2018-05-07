---
title: IHostSemaphore 介面
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103deb5ec46ba8c1d385c5339bc52a0c220c4c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore 介面
表示執行緒的號誌的主機的實作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ReleaseSemaphore 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|會在目前的計數增加`IHostSemaphore`執行個體，以指定的數量。|  
|[Wait 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|造成目前`IHostSemaphore`等候，直到它擁有的執行個體或指定的經過時間量。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostAutoEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [IHostManualEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
