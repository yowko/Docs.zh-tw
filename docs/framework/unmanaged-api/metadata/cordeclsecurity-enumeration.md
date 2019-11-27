---
title: CorDeclSecurity 列舉
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 98183ed02f8821b7c40852de2d040775d30f2518
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443738"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity 列舉
指定可以使用宣告式安全性執行的安全性動作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`dclActionMask`|保留。|  
|`dclActionNil`|保留。|  
|`dclRequest`|保留。|  
|`dclDemand`|呼叫堆疊中較高層的所有呼叫端，必須已獲得目前權限物件所指定的權限。|  
|`dclAssert`|呼叫程式碼可以存取目前權限物件所識別的資源，即使堆疊中較高層的呼叫端未獲得存取資源的許可權也一樣。|  
|`dclDeny`|存取目前權限物件所指定之資源的能力，會被拒絕呼叫端，即使已授與存取權。|  
|`dclPermitOnly`|只可存取這個權限物件所指定的資源，即使程式碼已獲得其他資源存取權限亦然。|  
|`dclLinktimeCheck`|立即呼叫端必須在指定的時間內被授與指定的許可權。|  
|`dclInheritanceCheck`|繼承另一個類別或覆寫方法的衍生類別，必須已授與指定的許可權。|  
|`dclRequestMinimum`|呼叫端可以要求執行程式碼所需的最小許可權。 這個動作只能在組件的範圍內使用。|  
|`dclRequestOptional`|呼叫端可以要求選擇性的其他許可權（不需要執行）。 這項要求會隱含拒絕未特別要求的所有其他權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestRefuse`|系統將不會授與呼叫者對可能誤用之許可權的要求。 這個動作只能在組件的範圍內使用。|  
|`dclPrejitGrant`|保留。|  
|`dclPrejitDenied`|保留。|  
|`dclNonCasDemand`|保留。|  
|`dclNonCasLinkDemand`|直接呼叫端必須已獲得指定權限。|  
|`dclNonCasInheritance`|保留。|  
|`dclLinkDemandChoice`|保留。|  
|`dclInheritanceDemandChoice`|保留。|  
|`dclDemandChoice`|保留。|  
|`dclMaximumValue`|保留。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
