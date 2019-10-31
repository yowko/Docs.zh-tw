---
title: IHostIoCompletionManager::GetHostOverlappedSize 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 3c662021894acbb8eb448fa2166498254158caa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133869"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize 方法
取得主機打算附加到 i/o 要求的任何自訂資料大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `pcbSize`  
 脫銷除了 Win32 `OVERLAPPED` 物件的大小以外，common language runtime （CLR）應配置的位元組數目指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `GetHostOverlappedSize`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 所有對 Windows 平臺 Api 的非同步 i/o 呼叫都會採用 Win32 `OVERLAPPED` 物件，它會提供檔案指標位置等資訊。 若要維持狀態，進行非同步 i/o 呼叫的應用程式通常會將自訂資料加入至結構。 `GetHostOverlappedSize` 和[IHostIoCompletionManager：： InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)提供機會讓主機加入這類自訂資料。  
  
 CLR 會呼叫 `GetHostOverlappedSize` 方法，來判斷主機想要附加至 `OVERLAPPED` 物件的自訂資料大小。  
  
> [!NOTE]
> `GetHostOverlappedSize` 只會呼叫一次。 主機的自訂資料必須與每個 i/o 要求的大小相同。  
  
> [!IMPORTANT]
> `OVERLAPPED` 物件本身的大小不會包含在 `pcbSize`的值中。  
  
 如需 `OVERLAPPED` 結構的詳細資訊，請參閱 Windows 平臺檔。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
