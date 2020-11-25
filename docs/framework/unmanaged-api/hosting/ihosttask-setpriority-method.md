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
ms.openlocfilehash: 80b4bb2f6a547250acbc16a89e7396c60cc50d87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720447"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority 方法

要求主機調整目前 [IHostTask](ihosttask-interface.md) 實例所代表之工作的執行緒優先權層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>參數  

 `newPriority`  
 在整數，表示目前實例所代表之工作的要求執行緒優先權值 `IHostTask` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetPriority` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 執行緒是使用迴圈配置資源系統（部分依據執行緒的優先權層級）來授與處理時間。 `SetPriority` 允許 CLR 為目前的工作設定該執行緒的優先權層級。 支援下列 `newPriority` 值。  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 CLR 會在 `SetPriority` <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> 使用者程式碼修改的值時呼叫。 主機可以針對執行緒優先順序指派定義自己的演算法，而且可以自由地忽略此要求。  
  
> [!NOTE]
> `SetPriority` 不會報告執行緒優先權層級是否已變更。 呼叫 [IHostTask：： GetPriority](ihosttask-getpriority-method.md) 來判斷工作的執行緒優先權層級的值。  
  
 執行緒優先權層級值是由 Win32 `SetThreadPriority` 函式定義。 如需執行緒優先順序的詳細資訊，請參閱 Windows 平臺檔。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Thread>
- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [GetPriority 方法](ihosttask-getpriority-method.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
