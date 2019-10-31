---
title: IHostCrst 介面
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130517"
---
# <a name="ihostcrst-interface"></a>IHostCrst 介面
作為執行緒之重要區段的主機標記法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Enter 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|進入重要區段。|  
|[Leave 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|離開重要區段。|  
|[SetSpinCount 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|設定重要區段的微調計數。|  
|[TryEnter 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|嘗試進入重要區段，並立即報告成功或失敗。|  
  
## <a name="remarks"></a>備註  
 `IHostCrst` 可讓 common language runtime （CLR）直接與主控制項的重要區段表示進行通訊，而不是使用 `EnterCriticalSection` 或 `LeaveCriticalSection`之類的 Win32 函數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
