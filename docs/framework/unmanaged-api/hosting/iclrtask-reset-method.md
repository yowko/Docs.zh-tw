---
title: ICLRTask::Reset 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124647"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset 方法
通知 common language runtime （CLR），表示主機已完成工作，並讓 CLR 重複使用目前的[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例來表示另一個工作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>參數  
 `fFull`  
 [in] `true`，如果執行時間除了與目前 `ICLRTask` 實例相關的安全性和地區設定資訊之外，應重設所有線程相關的靜態值;否則，`false`。  
  
 如果 `true`值，則執行時間會重設使用 <xref:System.Threading.Thread.AllocateDataSlot%2A> 或 <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>儲存的資料。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `Reset`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或處理呼叫的狀態。 能夠|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 CLR 可以回收先前建立的 `ICLRTask` 實例，以避免每次需要全新的工作時重複建立新實例的額外負荷。 主機會在完成工作時呼叫 `ICLRTask::Reset`，而不是[ICLRTask：： ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) ，藉以啟用這項功能。 下列清單摘要說明 `ICLRTask` 實例的一般生命週期：  
  
1. 執行時間會建立新的 `ICLRTask` 實例。  
  
2. 執行時間會呼叫[IHostTaskManager：： GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)以取得目前主機工作的參考。  
  
3. 執行時間會呼叫[IHostTask：： SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) ，將新的實例與主機工作產生關聯。  
  
4. 此工作會執行並完成。  
  
5. 主機會藉由呼叫 `ICLRTask::ExitTask`來終結工作。  
  
 `Reset` 以兩種方式改變此案例。 在上述步驟5中，主機會呼叫 `Reset`，將工作重設為「清除」狀態，然後將 `ICLRTask` 實例與相關聯的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例分離。 如有需要，主機也可以快取 `IHostTask` 實例以供重複使用。 在上述步驟1中，執行時間會從快取中提取回收的 `ICLRTask`，而不是建立新的實例。  
  
 當主機也有可重複使用之背景工作角色的集區時，這個方法會很有作用。 當主機終結其中一個 `IHostTask` 實例時，它會藉由呼叫 `ExitTask`來終結對應的 `ICLRTask`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
