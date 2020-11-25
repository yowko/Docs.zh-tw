---
title: IHostTaskManager::BeginDelayAbort 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f72cc15904d098e159dd7f75f673d43ae987998d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727324"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a>IHostTaskManager::BeginDelayAbort 方法

通知主機 managed 程式碼所輸入的期間，不能中止目前的工作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`BeginDelayAbort` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_UNEXPECTED|`BeginDelayAbort` 已經呼叫過，但尚未收到對應的 [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) 呼叫。|  
  
## <a name="remarks"></a>備註  

 在呼叫之前，主機不得中止目前的工作 `EndDelayAbort` 。 如果在沒有仲介呼叫的情況下發出另一個呼叫 `BeginDelayAbort` `EndDelayAbort` ，主機應該會傳回 E_UNEXPECTED `BeginDelayAbort` ，且不應該採取任何動作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
