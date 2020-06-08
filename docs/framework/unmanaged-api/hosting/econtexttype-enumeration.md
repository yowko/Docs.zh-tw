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
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493382"
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`eCurrentContext`|指出當 common language runtime （CLR）呼叫[IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md)方法時，或 clr 在呼叫[IHostSecurityManager：： SetSecurityCoNtext](ihostsecuritymanager-setsecuritycontext-method.md)方法時要求的內容時，目前線程上的內容。|  
|`eRestrictedContext`|表示主機具有較低許可權的內容，例如垃圾收集行程或類別或模組的處理常式。|  
  
## <a name="remarks"></a>備註  
 CLR 會 `EContextType` 在對和方法的呼叫中提供其中一個值做為參數值 `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
