---
title: IHostTaskManager::EnterRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a47f51ba32a9dfc16300a8de7c2d4b380a8ba988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerenterruntime-method"></a>IHostTaskManager::EnterRuntime 方法
通知主機的呼叫未受管理的方法，例如平台叫用方法時，會執行將控制權傳回給 common language runtime (CLR)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`EnterRuntime` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|記憶體不足，無法完成要求的配置。|  
  
## <a name="remarks"></a>備註  
 `EnterRuntime` 呼叫以通知主機的 unmanaged 函式，其之前呼叫[LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)方法進行、 已完成執行，並會將執行控制權傳回給執行階段。  
  
> [!NOTE]
>  [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)呼叫以通知主機的 unmanaged 函式，其之前呼叫`LeaveRuntime`提出、 正在進行的呼叫至 managed 程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [進階 COM 互通性](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [LeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
