---
title: IHostSecurityManager::SetSecurityContext 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: dadacaea2b8741afc7b8c51404e2604dc759a629
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680374"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext 方法

設定目前執行中線程的安全性內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>參數  

 `eContextType`  
 在其中一個 [ECoNtextType](econtexttype-enumeration.md) 值，指出 common language RUNTIME (CLR) 放置在主機上的內容類型。  
  
 `ppSecurityContext`  
 擴展新 [IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 CLR 會 `SetSecurityContext` 在數個案例中呼叫。 在執行類別和模組的函式和完成項之前，CLR 會呼叫 `SetSecurityContext` 以防止主機執行失敗。 然後，它會在執行函式或完成項之後，使用的另一個呼叫，將安全性內容重設為其原始狀態 `SetSecurityContext` 。 I/o 完成時，會發生類似的模式。 如果主機執行 [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)，則 CLR 會在 `SetSecurityContext` 主機呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md)之後呼叫。  
  
 在背景工作執行緒的非同步點上，CLR `SetSecurityContext` <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 會在 [IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)內或內部呼叫，視主機或 CLR 是否正在執行執行緒集區而定。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType 列舉](econtexttype-enumeration.md)
- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager 介面](ihostthreadpoolmanager-interface.md)
