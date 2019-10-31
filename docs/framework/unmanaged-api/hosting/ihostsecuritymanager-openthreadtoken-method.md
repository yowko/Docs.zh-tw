---
title: IHostSecurityManager::OpenThreadToken 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121474"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken 方法
開啟與目前執行中線程相關聯的任意存取權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 在存取值的遮罩，指定對執行緒 token 所要求的存取類型。 這些值是在 Win32 `OpenThreadToken` 函數中定義。 要求的存取類型會與權杖的任意存取控制清單（DACL）進行協調，以決定要授與或拒絕哪些類型的存取權。  
  
 `bOpenAsSelf`  
 [in] `true` 指定應該使用呼叫執行緒之進程的安全性內容來進行存取檢查;`false`，指定應該使用呼叫執行緒本身的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，則安全性內容可以是用戶端進程的其中一個。  
  
 `phThreadToken`  
 脫銷新開啟之存取權杖的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `OpenThreadToken`。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `IHostSecurityManager::OpenThreadToken` 的行為類似于相同名稱的對應 Win32 函式，不同之處在于 Win32 函式允許呼叫端將控制碼傳入任意執行緒，而 `IHostSecurityManager::OpenThreadToken` 只會開啟與呼叫執行緒相關聯的 token。  
  
 `HANDLE` 類型不符合 COM 標準，也就是說，它的大小是作業系統特有的，而且需要自訂封送處理。 因此，此權杖僅適用于在進程內的 CLR 與主控制項之間使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
