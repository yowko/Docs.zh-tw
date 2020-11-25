---
title: IHostTaskManager::BeginThreadAffinity 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 6f6d57a52d960c975d468f370477b5d7e29c3aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727337"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a>IHostTaskManager::BeginThreadAffinity 方法

通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`BeginThreadAffinity` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 CLR 通常會 `IHostTaskManager::BeginThreadAffinity` 在呼叫的內容中呼叫 <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> 。 在對 [IHostTaskManager：： EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md)進行對應的呼叫之前，不能重新排程目前的工作。 您可以將工作切換出來，但是當它們切換回時，必須將它們指派給與其進行切換的相同作業系統執行緒。的嵌套呼叫 `BeginThreadAffinity` 不會有任何作用，因為呼叫會參考目前的工作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
