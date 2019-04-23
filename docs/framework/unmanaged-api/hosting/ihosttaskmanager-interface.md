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
ms.openlocfilehash: da30e75bf4a58e66bb0dd8210368b162cf14c3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091261"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager 介面
提供方法，可讓 common language runtime (CLR) 會使用透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|通知主機 managed 程式碼輸入的期間，不會中止目前的工作。|  
|[BeginThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|通知主機 managed 程式碼會進入目前的工作不會移至另一個作業系統執行緒的週期。|  
|[CallNeedsHostHook 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|可讓主應用程式指定通用語言執行平台是否可以內嵌指定呼叫 unmanaged 函式。|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|主應用程式建立新工作的要求。|  
|[EndDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|通知主機 managed 程式碼正在結束的期間，在其中必須不會中止目前的工作，遵循先前呼叫`BeginDelayAbort`。|  
|[EndThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|通知主機 managed 程式碼正在結束目前的工作不會移至另一個的作業系統執行緒的週期遵循先前呼叫`BeginThreadAffinity`。|  
|[EnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|主應用程式的呼叫未受管理的方法，例如平台叫用方法，是執行將控制權還給 CLR。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|取得目前正在進行這個呼叫的作業系統執行緒執行工作的介面指標。|  
|[GetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|取得量的保證堆疊操作完成之後, 才能使用的堆疊空間，但處理程序關閉之前。|  
|[LeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|通知主機 managed 程式碼呼叫 unmanaged 函式。|  
|[ReverseEnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|主應用程式到從 unmanaged 程式碼的 common language runtime (CLR) 進行呼叫。|  
|[ReverseLeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|控制項是離開 CLR，並輸入 unmanaged 函式，接著呼叫函式從 managed 程式碼，請通知主機。|  
|[SetCLRTaskManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|主應用程式提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) ，CLR 所實作的執行個體。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|CLR 已變更目前的工作上的地區設定會告知主應用程式。|  
|[SetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|已保留供內部使用。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|主應用程式使用者介面的地區設定已變更為不同於目前的工作。|  
|[Sleep 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|將目前的工作會進入睡眠會告知主應用程式。|  
|[SwitchToTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|主應用程式，它應該切換移出目前的工作。|  
  
## <a name="remarks"></a>備註  
 `IHostTaskManager` 可讓 CLR 建立和管理工作，以提供主應用程式以採取動作，當控制權從 managed 到 unmanaged 程式碼，反之亦然，並指定特定動作的勾點主機可以和程式碼執行期間無法取得。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
