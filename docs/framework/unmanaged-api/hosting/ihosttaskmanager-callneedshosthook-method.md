---
title: IHostTaskManager::CallNeedsHostHook 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 983cad5ed87d0666ed71a805a3b3f7a3c7e7c091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook 方法
可讓主應用程式指定 common language runtime (CLR) 是否可內嵌指定呼叫 unmanaged 函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a>參數  
 `target`  
 [in]要呼叫 unmanaged 函式的對應的可攜式執行檔 (PE) 檔案中的位址。  
  
 `pbCallNeedsHostHook`  
 [out]布林值，表示主機是否需要呼叫連結指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 若要協助最佳化程式碼執行，CLR 就會執行分析的每個平台叫用呼叫期間編譯，以判斷是否可以內嵌呼叫。 `CallNeedsHostHook` 可讓主應用程式需要被攔截的 unmanaged 函式呼叫，以覆寫該決策。 如果主機需要攔截程序，執行階段並不會內嵌呼叫。  
  
 主機通常需要攔截程序必須調整浮點狀態，或在收到呼叫會進入主應用程式無法追蹤記憶體或任何採用的鎖定的執行階段的要求，其中某一狀態的通知。 當主應用程式需要呼叫被攔截時，執行階段會使用呼叫通知 managed 程式碼往來的轉換主機[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)， [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)， [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)，和[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
