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
|`dclActionMask`|保留的。|  
|`dclActionNil`|保留的。|  
|`dclRequest`|保留的。|  
|`dclDemand`|呼叫堆疊中較高層的所有呼叫端，必須已獲得目前權限物件所指定的權限。|  
|`dclAssert`|The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource|  
|`dclDeny`|The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.|  
|`dclPermitOnly`|只可存取這個權限物件所指定的資源，即使程式碼已獲得其他資源存取權限亦然。|  
|`dclLinktimeCheck`|The immediate caller is required to have been granted the specified permission for a given period of time.|  
|`dclInheritanceCheck`|The derived class inheriting another class or overriding a method is required to have been granted the specified permission.|  
|`dclRequestMinimum`|The caller can request for the minimum permissions required for code to run. 這個動作只能在組件的範圍內使用。|  
|`dclRequestOptional`|The caller can request for additional permissions that are optional (not required to run). 這項要求會隱含拒絕未特別要求的所有其他權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestRefuse`|The caller's request for permissions that might be misused will not be granted. 這個動作只能在組件的範圍內使用。|  
|`dclPrejitGrant`|保留的。|  
|`dclPrejitDenied`|保留的。|  
|`dclNonCasDemand`|保留的。|  
|`dclNonCasLinkDemand`|直接呼叫端必須已獲得指定權限。|  
|`dclNonCasInheritance`|保留的。|  
|`dclLinkDemandChoice`|保留的。|  
|`dclInheritanceDemandChoice`|保留的。|  
|`dclDemandChoice`|保留的。|  
|`dclMaximumValue`|保留的。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
