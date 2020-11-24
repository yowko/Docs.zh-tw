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
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673107"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager 介面

提供可讓 common language runtime (CLR) 透過主機處理工作的方法，而不是使用標準作業系統執行緒或光纖函數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginDelayAbort 方法](ihosttaskmanager-begindelayabort-method.md)|通知主機 managed 程式碼所輸入的期間，不能中止目前的工作。|  
|[BeginThreadAffinity 方法](ihosttaskmanager-beginthreadaffinity-method.md)|通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。|  
|[CallNeedsHostHook 方法](ihosttaskmanager-callneedshosthook-method.md)|可讓主機指定 common language runtime 是否可以將指定的呼叫內嵌至非受控函式。|  
|[CreateTask 方法](ihosttaskmanager-createtask-method.md)|要求主機建立新的工作。|  
|[EndDelayAbort 方法](ihosttaskmanager-enddelayabort-method.md)|在先前的呼叫之後，通知主機 managed 程式碼即將結束，也就是目前的工作不得中止的期間 `BeginDelayAbort` 。|  
|[EndThreadAffinity 方法](ihosttaskmanager-endthreadaffinity-method.md)|在先前的呼叫之後，通知主機 managed 程式碼即將結束，且目前的工作不得移至另一個作業系統執行緒 `BeginThreadAffinity` 。|  
|[EnterRuntime 方法](ihosttaskmanager-enterruntime-method.md)|通知主機，對非受控方法的呼叫（例如平台叫用方法）會將執行控制傳回至 CLR。|  
|[GetCurrentTask 方法](ihosttaskmanager-getcurrenttask-method.md)|取得執行此呼叫之作業系統執行緒上目前正在執行之工作的介面指標。|  
|[GetStackGuarantee 方法](ihosttaskmanager-getstackguarantee-method.md)|取得在堆疊作業完成之後，但在進程關閉之前，保證可供使用的堆疊空間量。|  
|[LeaveRuntime 方法](ihosttaskmanager-leaveruntime-method.md)|通知主機 managed 程式碼即將呼叫非受控函式。|  
|[ReverseEnterRuntime 方法](ihosttaskmanager-reverseenterruntime-method.md)|通知主機從非受控程式碼對 common language runtime (CLR) 進行呼叫。|  
|[ReverseLeaveRuntime 方法](ihosttaskmanager-reverseleaveruntime-method.md)|通知主控制項正在離開 CLR，並輸入從 managed 程式碼呼叫的非受控函式。|  
|[SetCLRTaskManager 方法](ihosttaskmanager-setclrtaskmanager-method.md)|為主機提供由 CLR 所執行之 [ICLRTaskManager](iclrtaskmanager-interface.md) 實例的介面指標。|  
|[SetLocale 方法](ihosttaskmanager-setlocale-method.md)|通知主機 CLR 已變更目前工作的地區設定。|  
|[SetStackGuarantee 方法](ihosttaskmanager-setstackguarantee-method.md)|已保留供內部使用。|  
|[SetUILocale 方法](ihosttaskmanager-setuilocale-method.md)|通知主機目前的工作已變更使用者介面地區設定。|  
|[Sleep 方法](ihosttaskmanager-sleep-method.md)|通知主機目前的工作即將進入睡眠狀態。|  
|[SwitchToTask 方法](ihosttaskmanager-switchtotask-method.md)|通知主機應該切換出目前的工作。|  
  
## <a name="remarks"></a>備註  

 `IHostTaskManager` 允許 CLR 建立和管理工作，以便在控制從 managed 至非受控程式碼的傳輸時，以及指定主機在程式碼執行期間可執行和不能執行的特定動作時，提供攔截功能讓主機採取動作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [裝載介面](hosting-interfaces.md)
