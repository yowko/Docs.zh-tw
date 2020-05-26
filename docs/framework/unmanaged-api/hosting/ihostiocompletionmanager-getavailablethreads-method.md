---
title: IHostIoCompletionManager::GetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 7ea7395bb1f185ba59940d76def562ab5440e560
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804758"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a>IHostIoCompletionManager::GetAvailableThreads 方法
取得目前未服務要求的 i/o 完成執行緒數目，這是由主機管理的執行緒總數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwAvailableIoCompletionThreads`  
 脫銷主機所管理的 i/o 完成執行緒數目指標，目前可供服務要求使用。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetAvailableThreads`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOTIMPL|主機未提供的執行 `GetAvailableThreads` 。|  
  
## <a name="remarks"></a>備註  
 主機可能會想要獨佔控制 i/o 完成執行緒集區的大小，以因應執行、效能或擴充性等原因。 因此，主機不需要執行 `GetAvailableThreads` 。 在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
