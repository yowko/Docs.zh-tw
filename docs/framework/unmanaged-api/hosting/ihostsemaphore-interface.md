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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803697"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore 介面
表示執行緒之信號的主機執行。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ReleaseSemaphore 方法](ihostsemaphore-releasesemaphore-method.md)|`IHostSemaphore`依指定的數量增加目前實例的計數。|  
|[Wait 方法](ihostsemaphore-wait-method.md)|使目前的 `IHostSemaphore` 實例等到其擁有或指定的時間量經過之後，才等候。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostManualEvent 介面](ihostmanualevent-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
