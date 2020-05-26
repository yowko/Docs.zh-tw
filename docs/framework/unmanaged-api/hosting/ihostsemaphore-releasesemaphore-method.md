---
title: IHostSemaphore::ReleaseSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
ms.openlocfilehash: aa67aabbe8a7a47a9b3036f508e2f8bb6082c3e0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803549"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a>IHostSemaphore::ReleaseSemaphore 方法
依指定的數量增加目前[IHostSemaphore](ihostsemaphore-interface.md)實例的計數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a>參數  
 `lReleaseCount`  
 在要增加目前實例計數的數量 `IHostSemaphore` 。 此數量必須大於零。  
  
 `lpPreviousCount`  
 脫銷先前計數的指標，如果呼叫端不需要先前的計數，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ReleaseSemaphore`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 通常會呼叫， `ReleaseSemaphore` 以通知主機其已使用資源完成，並為參數傳遞1的值 `lReleaseCount` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostAutoEvent 介面](ihostautoevent-interface.md)
- [IHostManualEvent 介面](ihostmanualevent-interface.md)
- [IHostSemaphore 介面](ihostsemaphore-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
