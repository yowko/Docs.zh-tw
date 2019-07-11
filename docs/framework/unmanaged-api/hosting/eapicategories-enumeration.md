---
title: EApiCategories 列舉
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41513d9b6f98743bfad95e4d9606cfb4927369e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769786"
---
# <a name="eapicategories-enumeration"></a>EApiCategories 列舉
描述分類的主機可以封鎖無法在部分信任程式碼中執行的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eAll`|指定所有 managed 類別和成員所涵蓋的其他`EApiCategories`欄位遭到封鎖而無法在部分信任程式碼中執行。|  
|`eExternalProcessMgmt`|指定封鎖受管理的類別和成員，可讓建立、 管理和解構的外部處理序在部分信任程式碼中執行。|  
|`eExternalThreading`|指定 managed 的類別和成員，可讓建立、 管理和解構的外部執行緒被封鎖而無法執行部分信任程式碼中。|  
|`eMayLeakOnAbort`|指定封鎖受管理的類型和成員，可能會洩漏中止上的記憶體在部分信任程式碼中執行。|  
|`eNoCategory`|指定沒有任何 managed 程式碼類別無法在部分信任程式碼中執行。|  
|`eSecurityInfrastructure`|指定通用語言執行平台 (CLR) 安全性基礎結構遭到封鎖而無法由部分信任程式碼。|  
|`eSelfAffectingProcessMgmt`|指定封鎖受管理的類別和其功能可能會影響裝載的處理序的成員在部分信任程式碼中執行。|  
|`eSelfAffectingThreading`|指定封鎖受管理的類別和其功能可能會影響裝載處理序中的執行緒的成員在部分信任程式碼中執行。|  
|`eSharedState`|指定封鎖受管理的類別和公開共用的狀態的成員在部分信任程式碼中執行。|  
|`eSynchronization`|指定封鎖 common language runtime 類別和成員，可讓使用者程式碼保留鎖定在部分信任程式碼中執行。|  
|`eUI`|指定封鎖受管理的類別和成員允許或需要人為互動在部分信任程式碼中執行。|  
  
## <a name="remarks"></a>備註  
 [Iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)方法會採用類型參數的`EApiCategories`。  
  
 `EApiCategories`列舉型別和`SetProtectedCategories`方法直接相關的 managed<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>類別。 受管理的類別會搭配<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列舉型別，其值直接對應到`EApiCategories`值，以將 managed 型別和將功能對應至所描述的類別公開的成員標示`EApiCategories`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
