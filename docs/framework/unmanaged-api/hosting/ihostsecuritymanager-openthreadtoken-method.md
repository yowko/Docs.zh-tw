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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176262"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken 方法
打開與當前正在執行的執行緒關聯的可自由訪問權杖。  
  
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
 [在]指定對執行緒權杖的請求訪問類型的訪問值的遮罩。 這些值在 Win32`OpenThreadToken`函數中定義。 請求的訪問類型與權杖的任意存取控制清單 （DACL） 協調，以確定授予或拒絕的訪問類型。  
  
 `bOpenAsSelf`  
 [在]`true`指定應使用調用執行緒的進程的安全上下文進行訪問檢查;`false`指定應使用調用執行緒本身的安全上下文執行訪問檢查。 如果執行緒正在類比用戶端，則安全上下文可以是用戶端進程的安全上下文。  
  
 `phThreadToken`  
 [出]指向新打開的訪問權杖的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 當方法返回E_FAIL時，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `IHostSecurityManager::OpenThreadToken`行為行為類似于同名的相應 Win32 函數，只不過 Win32 函數允許調用方在控制碼中傳遞到任意執行緒，同時`IHostSecurityManager::OpenThreadToken`僅打開與調用執行緒關聯的權杖。  
  
 類型`HANDLE`不符合 COM，即其大小特定于作業系統，並且需要自訂封送。 因此，此權杖僅用於進程，在 CLR 和主機之間。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
