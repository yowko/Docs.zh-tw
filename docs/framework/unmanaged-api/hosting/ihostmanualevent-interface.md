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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804588"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent 介面
提供主機的手動重設事件表示的執行方式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Reset 方法](ihostmanualevent-reset-method.md)|將目前的 `IHostManualEvent` 實例重設為未收到信號的狀態。|  
|[Set 方法](ihostmanualevent-set-method.md)|將目前的 `IHostManualEvent` 實例設定為已發出信號的狀態。|  
|[Wait 方法](ihostmanualevent-wait-method.md)|導致目前的 `IHostManualEvent` 實例等到其擁有，或經過指定的時間量為止。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostSemaphore 介面](ihostsemaphore-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
