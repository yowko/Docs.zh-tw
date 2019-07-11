---
title: IHostSecurityManager::SetSecurityContext 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01aefbc764e2620319da04356a25af63c8edc839
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769353"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext 方法
設定目前執行中執行緒的安全性內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>參數  
 `eContextType`  
 [in]其中一個[EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，指出哪種類型的內容 common language runtime (CLR) 會放置在主機上。  
  
 `ppSecurityContext`  
 [out]新的位址指標[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)物件。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫`SetSecurityContext`數種案例中。 類別和模組建構函式和完成項，它會執行之前，CLR 會呼叫`SetSecurityContext`來防禦執行失敗的主應用程式。 它然後重設的安全性內容為其原始狀態後執行建構函式或完成項，使用另一個呼叫`SetSecurityContext`。 與 I/O 完成，就會發生類似的模式。 如果主應用程式實作[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)，CLR 會呼叫`SetSecurityContext`主機呼叫之後[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。  
  
 在背景工作執行緒中的非同步點，CLR 會呼叫`SetSecurityContext`內<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>或是在[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)，取決於是否在主機或 CLR 正在實作執行緒集區。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType 列舉](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [ICLRIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
