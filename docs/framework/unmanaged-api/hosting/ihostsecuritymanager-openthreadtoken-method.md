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
ms.openlocfilehash: 30ec8cc8bbbd6d49f89cd67371c3326c0cb0df9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680608"
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
 在存取值的遮罩，可指定要求的執行緒 token 存取類型。 這些值是在 Win32 函數中定義的 `OpenThreadToken` 。 要求的存取類型會與權杖的任意存取控制清單一致 (DACL) 來判斷要授與或拒絕的存取權類型。  
  
 `bOpenAsSelf`  
 [in] `true` 指定應使用呼叫執行緒之進程的安全性內容進行存取檢查; `false` 指定應該使用呼叫執行緒本身的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，安全性內容可以是用戶端進程的安全性內容。  
  
 `phThreadToken`  
 擴展新開啟之存取權杖的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 `IHostSecurityManager::OpenThreadToken` 與相同名稱的對應 Win32 函數類似，不同之處在于 Win32 函數可讓呼叫端傳入任意執行緒的控制碼，而 `IHostSecurityManager::OpenThreadToken` 只會開啟與呼叫執行緒相關聯的標記。  
  
 `HANDLE`類型不符合 COM 規範，也就是它的大小是作業系統特有的，而且需要自訂封送處理。 因此，此權杖僅適用于在 CLR 與主機之間的進程內。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
