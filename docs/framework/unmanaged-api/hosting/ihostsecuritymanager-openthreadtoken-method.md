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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68ebfdcd0ef34edec724a044791d05dd48580b12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697481"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken 方法
開啟與目前執行中執行緒相關聯的 discretionary 存取權杖。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 [in]存取值，指定的存取權的執行緒 token 的要求的類型的遮罩。 這些值會定義在 Win32 中`OpenThreadToken`函式。 要求的存取類型會協調對權杖的判別存取控制清單 (DACL)，以判斷哪些類型的存取權授與或拒絕。  
  
 `bOpenAsSelf`  
 [in]`true`來指定應該使用的安全性內容的程序呼叫的執行緒; 會建立在存取檢查`false`可以指定應該使用的安全性內容呼叫的執行緒本身要執行存取檢查。 如果執行緒模擬用戶端，可以是安全性內容的用戶端處理序。  
  
 `phThreadToken`  
 [out]新開啟的存取語彙基元指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `IHostSecurityManager::OpenThreadToken` 行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫者傳入任意的執行緒控制代碼，而`IHostSecurityManager::OpenThreadToken`開啟呼叫的執行緒相關聯的語彙基元。  
  
 `HANDLE`類型不是 COM 相容，也就是它的大小是特定作業系統，而且需要自訂封送處理。 因此，此權杖是只在處理序中，CLR 和主機之間使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
