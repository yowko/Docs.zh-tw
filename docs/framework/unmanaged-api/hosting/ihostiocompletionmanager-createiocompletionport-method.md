---
title: IHostIoCompletionManager::CreateIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: 240712296254e02f4d268a00e1c15ef34f4519f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501535"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a>IHostIoCompletionManager::CreateIoCompletionPort 方法
要求主機建立新的 i/o 完成埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a>參數  
 `phPort`  
 脫銷新建立的 i/o 完成埠的控制碼指標，如果無法建立埠，則為0（零）。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`CreateIoCompletionPort`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來配置要求的資源。|  
  
## <a name="remarks"></a>備註  
 CLR `CreateIoCompletionPort` 會呼叫方法，以要求主機建立新的 i/o 完成埠。 它會透過呼叫[IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md)方法，將 i/o 作業系結至這個埠。 主機會藉由呼叫[ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md)，將狀態報表回 CLR。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
