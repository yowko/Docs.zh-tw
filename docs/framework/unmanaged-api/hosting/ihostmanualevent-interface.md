---
title: IHostManualEvent 介面
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208627"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent 介面
提供手動重設事件的表示主機的實作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|重設目前`IHostManualEvent`未收到信號狀態的執行個體。|  
|[Set 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|設定目前`IHostManualEvent`執行個體收到信號的狀態。|  
|[Wait 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|造成目前`IHostManualEvent`等候，直到它所屬於的執行個體或指定的時間量。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
