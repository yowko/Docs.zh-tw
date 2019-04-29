---
title: ICLRTaskManager::CreateTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8833daa9cd385a1a76c5b706f15a76bb15139b84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763421"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask 方法
明確要求的 common language runtime (CLR) 建立新的工作。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>參數  
 `pTask`  
 [out]新建立的位址指標[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)，或為 null，如果無法建立工作。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可配置要求的資源。|  
  
## <a name="remarks"></a>備註  
 當使用者程式碼會建立執行緒使用中的型別時，CLR 會建立新的工作，在初始化後自動<xref:System.Threading>命名空間，或當執行緒集區的大小已增加。 當 unmanaged 程式碼會呼叫 managed 函式時，它也會建立工作。  
  
 `CreateTask` 可讓主應用程式發出明確的要求，CLR 會建立新的工作。 例如，主機可以叫用這個方法，以先行初始化資料結構。  
  
> [!IMPORTANT]
>  新的工作會傳回在暫停狀態，並會保持暫停，直到主機明確呼叫[ihosttask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
