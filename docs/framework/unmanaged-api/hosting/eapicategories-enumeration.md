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
ms.openlocfilehash: f90e08373c0497201816bc7eead89b83b84be255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726869"
---
# <a name="eapicategories-enumeration"></a>EApiCategories 列舉

描述主機可以封鎖在部分信任程式碼中執行的功能類別。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`eAll`|指定封鎖其他欄位所涵蓋的所有 managed 類別和成員，使 `EApiCategories` 其無法在部分信任的程式碼中執行。|  
|`eExternalProcessMgmt`|指定允許建立、操作和終結外部進程的 managed 類別和成員，無法在部分信任的程式碼中執行。|  
|`eExternalThreading`|指定允許在部分信任程式碼中執行外部執行緒的建立、操作和銷毀的 managed 類別和成員。|  
|`eMayLeakOnAbort`|指定無法在部分信任的程式碼中執行中止時可能流失記憶體的 managed 類型和成員。|  
|`eNoCategory`|指定禁止在部分信任程式碼中執行 managed 程式碼類別。|  
|`eSecurityInfrastructure`|指定禁止部分信任程式碼使用 common language runtime (CLR) 安全性基礎結構。|  
|`eSelfAffectingProcessMgmt`|指定受管理的類別和成員的功能可能會影響裝載進程，而無法在部分信任的程式碼中執行。|  
|`eSelfAffectingThreading`|指定受管理的類別和成員的功能可能會影響裝載進程中的執行緒，使其無法在部分信任的程式碼中執行。|  
|`eSharedState`|指定公開共用狀態的 managed 類別和成員，在部分信任的程式碼中遭到封鎖而無法執行。|  
|`eSynchronization`|指定允許使用者程式碼保存鎖定的 common language runtime 類別和成員，在部分信任的程式碼中遭到封鎖而無法執行。|  
|`eUI`|指定允許或要求人類互動的 managed 類別和成員，無法在部分信任的程式碼中執行。|  
  
## <a name="remarks"></a>備註  

 [ICLRHostProtectionManager：： SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md)方法接受型別為的參數 `EApiCategories` 。  
  
 `EApiCategories`列舉和方法與 `SetProtectedCategories` managed 類別直接相關 <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> 。 Managed 類別會搭配 <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> 列舉使用，其值會直接對應至 `EApiCategories` 值，以標示 managed 類型和成員，而這些型別和成員會公開對應至所描述之類別目錄的功能 `EApiCategories` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
