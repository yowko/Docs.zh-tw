---
title: IHostIoCompletionManager::InitializeHostOverlapped 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: cf257ab86d27946c861c89dff5e6f09a42013e58
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804704"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped 方法
讓主機有機會初始化任何自訂資料，以附加至 `OVERLAPPED` 用於非同步 i/o 要求的 Win32 結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>參數  
 `pvOverlapped`  
 在要 `OVERLAPPED` 包含在 i/o 要求中的 Win32 結構指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來配置要求的資源。|  
  
## <a name="remarks"></a>備註  
 Windows 平臺函式會使用 `OVERLAPPED` 結構來儲存非同步 i/o 要求的狀態。 CLR 會呼叫 `InitializeHostOverlapped` 方法，讓主機有機會將自訂資料附加至 `OVERLAPPED` 實例。  
  
> [!IMPORTANT]
> 若要取得自訂資料區塊的開頭，主機必須將位移設定為結構的大小 `OVERLAPPED` （ `sizeof(OVERLAPPED)` ）。  
  
 E_OUTOFMEMORY 的傳回值表示主機無法初始化其自訂資料。 在此情況下，CLR 會報告錯誤，並導致呼叫失敗。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize 方法](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
