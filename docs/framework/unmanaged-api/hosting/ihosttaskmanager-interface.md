---
title: IHostTaskManager 介面
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9715738931d1b6a91ad9fae7e00ba607905d380f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager 介面
提供方法讓 common language runtime (CLR) 處理透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|通知主機 managed 程式碼正在進入的期間，不會中止目前的工作。|  
|[BeginThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|通知主機 managed 程式碼會進入目前的工作不會移至另一個作業系統執行緒的週期。|  
|[CallNeedsHostHook 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|可讓主應用程式指定通用語言執行平台是否可以內嵌指定呼叫 unmanaged 函式。|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|主應用程式建立新工作的要求。|  
|[EndDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|通知主機 managed 程式碼正在結束的期間所在必須中止目前的工作，遵循之前呼叫`BeginDelayAbort`。|  
|[EndThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|通知主機 managed 程式碼會結束目前的工作不會移至另一個作業系統執行緒的期間遵循之前呼叫`BeginThreadAffinity`。|  
|[EnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|通知主機的呼叫未受管理的方法，例如平台叫用方法時，會執行將控制權傳回給 CLR。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|取得目前正在進行這個呼叫時之作業系統執行緒上執行工作的介面指標。|  
|[GetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|取得量保證堆疊操作完成之後, 可供使用的堆疊空間但之前結束處理序。|  
|[LeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|通知主機 managed 程式碼即將呼叫以 unmanaged 函式。|  
|[ReverseEnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|通知主機到從 unmanaged 程式碼的 common language runtime (CLR) 進行呼叫。|  
|[ReverseLeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|通知主機，控制會離開 CLR，並輸入，接著，從 managed 程式碼呼叫 unmanaged 函式。|  
|[SetCLRTaskManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|主機提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) CLR 所實作的執行個體。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|通知主機，CLR 會變更目前的工作上的地區設定。|  
|[SetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|已保留供內部使用。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|通知主機在目前的工作到已變更的使用者介面的地區設定。|  
|[Sleep 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|通知主機在目前的工作會進入睡眠。|  
|[SwitchToTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|通知主機，它應該切換移出目前的工作。|  
  
## <a name="remarks"></a>備註  
 `IHostTaskManager` 允許 CLR 建立和管理工作，提供主機控制權時從 managed 到 unmanaged 程式碼，反之亦然，採取動作，並指定特定動作的攔截程序主機可以和程式碼執行期間無法使用。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
