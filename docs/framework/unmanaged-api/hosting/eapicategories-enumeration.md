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
ms.openlocfilehash: d31b0190ef9a697fb27c849db080bec6c57618ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616381"
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
  
|成員|說明|  
|------------|-----------------|  
|`eAll`|指定封鎖其他欄位涵蓋的所有 managed 類別和成員，使 `EApiCategories` 其無法在部分信任的程式碼中執行。|  
|`eExternalProcessMgmt`|指定允許建立、操作和終結外部進程的 managed 類別和成員，無法在部分信任的程式碼中執行。|  
|`eExternalThreading`|指定允許建立、操作和終結外部執行緒的 managed 類別和成員，無法在部分信任的程式碼中執行。|  
|`eMayLeakOnAbort`|指定封鎖在部分信任程式碼中執行的 managed 類型和成員可能會在中止時遺漏記憶體。|  
|`eNoCategory`|指定不封鎖 managed 程式碼分類，使其無法在部分信任的程式碼中執行。|  
|`eSecurityInfrastructure`|指定禁止部分信任程式碼使用 common language runtime （CLR）安全性基礎結構。|  
|`eSelfAffectingProcessMgmt`|指定受管理的類別和成員的功能可能會影響裝載的進程，使其無法在部分信任的程式碼中執行。|  
|`eSelfAffectingThreading`|指定受管理的類別和成員，其功能可能會影響裝載進程中的執行緒，而無法在部分信任的程式碼中執行。|  
|`eSharedState`|指定會封鎖公開共用狀態的 managed 類別和成員，使其無法在部分信任的程式碼中執行。|  
|`eSynchronization`|指定允許使用者程式碼保留鎖定的通用語言執行平臺類別和成員，無法在部分信任的程式碼中執行。|  
|`eUI`|指定允許或要求人為互動的 managed 類別和成員，無法在部分信任的程式碼中執行。|  
  
## <a name="remarks"></a>備註  
 [ICLRHostProtectionManager：： SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md)方法接受型別為的參數 `EApiCategories` 。  
  
 `EApiCategories`列舉和方法與 `SetProtectedCategories` managed 類別直接相關 <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> 。 Managed 類別會搭配 <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> 列舉使用，其值會直接對應至 `EApiCategories` 值，以標示會公開功能的 managed 類型和成員，而這些對應于所描述的分類 `EApiCategories` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
