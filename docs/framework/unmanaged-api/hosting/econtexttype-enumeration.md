---
title: EContextType 列舉
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131150"
---
# <a name="econtexttype-enumeration"></a>EContextType 列舉
描述目前執行中線程的安全性內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`eCurrentContext`|指出當 common language runtime （CLR）呼叫[IHostSecurityManager：： GetSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)方法時，或 clr 要求的內容呼叫[IHostSecurityManager：： SetSecurityCoNtext 時，目前線程上的內容](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)方法。|  
|`eRestrictedContext`|表示主機具有較低許可權的內容，例如垃圾收集行程或類別或模組的處理常式。|  
  
## <a name="remarks"></a>備註  
 CLR 會在呼叫 `IHostSecurityManager::GetSecurityContext` 和 `IHostSecurityManager::SetSecurityContext` 方法時，提供其中一個 `EContextType` 值做為參數值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
