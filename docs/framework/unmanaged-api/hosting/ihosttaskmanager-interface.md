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
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133013"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager 介面
提供的方法可讓 common language runtime （CLR）透過主機來處理工作，而不是使用標準作業系統執行緒或光纖函數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|通知主機 managed 程式碼所輸入的期間不得中止目前的工作。|  
|[BeginThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。|  
|[CallNeedsHostHook 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|可讓主機指定通用語言執行時間是否可以將指定的呼叫內嵌至非受控函式。|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|要求主機建立新的工作。|  
|[EndDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|在先前的 `BeginDelayAbort`呼叫之後，通知主機 managed 程式碼即將結束，但目前的工作不得中止。|  
|[EndThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|在先前的 `BeginThreadAffinity`呼叫之後，通知主機 managed 程式碼即將結束，而無法將目前的工作移至另一個作業系統執行緒。|  
|[EnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|通知主機呼叫非受控方法（例如平台叫用方法）時，會將執行控制傳回給 CLR。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|取得目前在執行此呼叫之作業系統執行緒上執行之工作的介面指標。|  
|[GetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|取得堆疊作業完成後，但在關閉進程之前，保證可以使用的堆疊空間量。|  
|[LeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|通知主機 managed 程式碼即將進行非受控函式的呼叫。|  
|[ReverseEnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|通知主機正在從非受控碼對 common language runtime （CLR）進行呼叫。|  
|[ReverseLeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|通知主控制項離開 CLR，並輸入從 managed 程式碼呼叫的非受控函式。|  
|[SetCLRTaskManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|提供具有 CLR 所實[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)實例之介面指標的主機。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|通知主機 CLR 已變更目前工作的地區設定。|  
|[SetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|已保留供內部使用。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|通知主機使用者介面地區設定已在目前的工作上變更。|  
|[Sleep 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|通知主機目前的工作即將進入睡眠狀態。|  
|[SwitchToTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|通知主機應該切換出目前的工作。|  
  
## <a name="remarks"></a>備註  
 `IHostTaskManager` 可讓 CLR 建立和管理工作，以提供攔截程式，讓主機在控制從 managed 傳送至非受控碼時採取動作，反之亦然，以及指定主機在程式碼執行期間可以執行的特定動作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
