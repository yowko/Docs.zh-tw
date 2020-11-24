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
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683052"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore 介面

代表主機針對執行緒所執行的信號。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ReleaseSemaphore 方法](ihostsemaphore-releasesemaphore-method.md)|依指定的數量增加目前 `IHostSemaphore` 實例的計數。|  
|[Wait 方法](ihostsemaphore-wait-method.md)|導致目前的 `IHostSemaphore` 實例等到其擁有或經過指定的時間量為止。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostManualEvent 介面](ihostmanualevent-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
