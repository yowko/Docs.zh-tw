---
title: ICLRIoCompletionManager::OnComplete 方法
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703822"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete 方法
使用對[IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md)方法的呼叫，通知 common language RUNTIME （CLR）所發出的 i/o 要求狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwErrorCode`  
 在HRESULT 值，指出系結作業的狀態。  
  
- S_OK 表示作業已成功完成。  
  
- HOST_E_INTERRUPTED 表示呼叫在完成前終止。  
  
- E_FAIL 表示發生未知、無法復原、嚴重失敗。  
  
 `NumberOfBytesTransferred`  
 在處理 i/o 要求期間所傳輸的位元組數目。  
  
 `pvOverlapped`  
 在`OVERLAPPED`傳遞至方法之呼叫的結構指標 `IHostIoCompletionManager::Bind` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`OnComplete`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 如果主機執行 i/o 完成抽象概念，CLR 會使用[IHostIoCompletionManager](ihostiocompletionmanager-interface.md)的方法，透過主機進行 i/o 要求。 然後，主機會呼叫 `OnComplete` 方法，以通知執行時間此類要求的結果。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager 介面](ihostthreadpoolmanager-interface.md)
