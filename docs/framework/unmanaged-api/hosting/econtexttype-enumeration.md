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
ms.openlocfilehash: c6d1ace12bd07fa1f14c8570eca1f950a5c22be9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686328"
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
  
|member|描述|  
|------------|-----------------|  
|`eCurrentContext`|指出 common language runtime (CLR) 呼叫 [IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md) 方法，或呼叫 [IHostSecurityManager：： SetSecurityCoNtext](ihostsecuritymanager-setsecuritycontext-method.md) 方法時，clr 所要求的內容在目前線程上的內容。|  
|`eRestrictedContext`|指出主機具有較低許可權的內容，例如垃圾收集行程，或類別或模組的函式。|  
  
## <a name="remarks"></a>備註  

 CLR 會 `EContextType` 在呼叫和方法時，將其中一個值作為參數值 `IHostSecurityManager::GetSecurityContext` 提供 `IHostSecurityManager::SetSecurityContext` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
