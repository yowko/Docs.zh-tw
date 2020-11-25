---
title: ICLRDebugManager::SetConnectionTasks 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 5df01ac929874d00a5fddda83f532927dc46d67b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719836"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks 方法

將 [ICLRTask](iclrtask-interface.md) 實例清單與識別碼和易記名稱產生關聯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>參數  

 `id`  
 在與陣列相關聯之連接的主機特定識別碼 `ppCLRTask` 。  
  
 `dwCount`  
 在的成員數目 `ppCLRTask` 。 此數目必須大於零。  
  
 `ppCLRTask`  
 在指標的陣列 `ICLRTask` ，與所識別的連接相關聯 `id` 。 此陣列必須至少包含一個成員。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|[BeginConnection](iclrdebugmanager-beginconnection-method.md)未使用此值 `id` 、或為零來呼叫 BeginConnection，或的 `dwCount` `id` 其中一個元素 `ppCLRTask` 為 null。|  
  
## <a name="remarks"></a>備註  

 [ICLRDebugManager](iclrdebugmanager-interface.md) 提供三種方法：、 `BeginConnection` `SetConnectionTasks` 和 [EndConnection](iclrdebugmanager-endconnection-method.md)，可讓工作清單與識別碼和易記名稱產生關聯。  
  
> [!IMPORTANT]
> 您必須針對每一組工作以特定順序呼叫這三種方法。 `BeginConnection` 先呼叫，以建立新的連接。 `SetConnectionTasks` 會在旁邊呼叫，以提供與該連接相關聯的工作集。 `EndConnection` 最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLRDebugManager 介面](iclrdebugmanager-interface.md)
- [BeginConnection 方法](iclrdebugmanager-beginconnection-method.md)
- [EndConnection 方法](iclrdebugmanager-endconnection-method.md)
- [IHostControl 介面](ihostcontrol-interface.md)
