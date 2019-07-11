---
title: IHostTask::SetPriority 方法
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9ecdeb4df6210805490586f1818298025fc036
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749948"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority 方法
表示由目前的工作要求主應用程式調整的執行緒優先權層級[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>參數  
 `newPriority`  
 [in]整數，表示要求的執行緒優先順序值，表示由目前的工作`IHostTask`執行個體。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`SetPriority` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 執行緒正在授與處理使用的部分以執行緒的優先權層級為基礎的循環配置資源系統的時間。 `SetPriority` 可讓 CLR 設定目前工作的執行緒優先權層級。 下列`newPriority`支援值。  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 CLR 會呼叫`SetPriority`時的值<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>修改使用者程式碼。 主機可以定義自己的演算法，來指派執行緒優先權，，而且可以自由地忽略這項要求。  
  
> [!NOTE]
>  `SetPriority` 不會報告是否已變更的執行緒優先權層級。 呼叫[ihosttask:: Getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)來判斷工作的執行緒優先權層級的值。  
  
 定義 win32 執行緒優先權層級值`SetThreadPriority`函式。 如需執行緒優先權的詳細資訊，請參閱 < Windows 平台的文件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Thread>
- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [GetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
