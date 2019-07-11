---
title: EInitializeNewDomainFlags 列舉
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d69b12404459de5dbc1c7748deee6ca09c1e5182
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772420"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags 列舉
可讓主應用程式執行階段提供的應用程式定義域初始化資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|沒有旗標。|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|會告知 common language runtime (CLR) 主機，將不進行變更的應用程式定義域的安全性狀態<xref:System.AppDomainManager.InitializeNewDomain%2A>方法。|  
  
## <a name="remarks"></a>備註  
 [Iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法會採用類型參數的`EInitializeNewDomainFlags`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [SetAppDomainManagerType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
