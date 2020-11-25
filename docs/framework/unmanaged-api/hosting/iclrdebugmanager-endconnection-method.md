---
title: ICLRDebugManager::EndConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: d6f22d6185f4063078463043a6ffd46e56289267
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719849"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection 方法

移除工作清單與識別碼和易記名稱之間的關聯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwConnectionId`  
 在連接的主機特定識別碼以及 common language runtime (CLR) 工作的相關清單。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`EndConnection` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|[BeginConnection](iclrdebugmanager-beginconnection-method.md) 從未使用 `dwConnectionId` 或 `dwConnectionId` 為零來呼叫。|  
  
## <a name="remarks"></a>備註  

 [ICLRDebugManager](iclrdebugmanager-interface.md) 提供三種方法：、 `BeginConnection` [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)和 `EndConnection` ，以便將工作清單與識別碼和易記名稱產生關聯。  
  
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
- [SetConnectionTasks 方法](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl 介面](ihostcontrol-interface.md)
