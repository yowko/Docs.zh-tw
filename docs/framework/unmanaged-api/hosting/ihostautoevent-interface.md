---
title: IHostAutoEvent 介面
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb5fea403f8210ea93d240aa3aabd4325524b987
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599451"
---
# <a name="ihostautoevent-interface"></a>IHostAutoEvent 介面
提供主機的自動重設事件實作的表示法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Set 方法](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|設定目前`IHostAutoEvent`執行個體收到信號的狀態。|  
|[Wait 方法](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|造成目前`IHostAutoEvent`等候，直到擁有事件的執行個體或指定的時間量。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostManualEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
