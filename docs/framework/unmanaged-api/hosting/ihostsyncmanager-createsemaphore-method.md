---
title: IHostSyncManager::CreateSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43935829d11a925d4a3389149f5c316df15f06bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764595"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a>IHostSyncManager::CreateSemaphore 方法
會建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)以作為等候事件的號誌的 common language runtime (CLR) 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwInitial`  
 [in]初始計數`ppSemaphore`。  
  
 `dwMax`  
 [in]最大計數`ppSemaphore`。  
  
 `ppSemaphore`  
 [out]位址指標`IHostSemaphore`執行個體，或如果無法建立號誌，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`CreateSemaphore` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|記憶體不足，無法建立要求的事件物件。|  
  
## <a name="remarks"></a>備註  
 `CreateSemaphore` 鏡像 Win32 函式具有相同的名稱。 `dwInitial`並`dwMax`參數使用相同的語意號誌計數做為 Win32`lInitialCount`和`lMaximumCount`參數，分別。 `dwInitial` 必須是介於 0 和`dwMax`（包含頭尾)。 `dwMax` 必須是小於或等於零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSemaphore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
