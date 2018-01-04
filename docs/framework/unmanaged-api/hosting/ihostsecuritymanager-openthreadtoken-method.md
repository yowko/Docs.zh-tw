---
title: "IHostSecurityManager::OpenThreadToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.OpenThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken 方法
會開啟與目前執行中執行緒相關聯的判別存取語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 [in]存取值，指定存取此執行緒語彙基元要求的類型的遮罩。 這些值會定義在 Win32`OpenThreadToken`函式。 必要的存取類型會調解對權杖的判別存取控制清單 (DACL) 來判斷哪些類型的存取權授與或拒絕。  
  
 `bOpenAsSelf`  
 [in]`true`來指定，應該使用的安全性內容的程序呼叫的執行緒; 進行存取檢查`false`來指定要執行呼叫的執行緒本身使用的安全性內容的存取檢查。 如果執行緒正在模擬用戶端，可以是用戶端處理序的安全性內容。  
  
 `phThreadToken`  
 [out]新開啟的存取語彙基元的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `IHostSecurityManager::OpenThreadToken`行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫端来傳入任意的執行緒控制代碼，而`IHostSecurityManager::OpenThreadToken`開啟與呼叫執行緒相關聯的語彙基元。  
  
 `HANDLE`類型不是 COM 相容，也就是它的大小是特定的作業系統，且其需要自訂封送處理。 因此，這個語彙基元是僅供處理程序，則 CLR 與主機之間。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
