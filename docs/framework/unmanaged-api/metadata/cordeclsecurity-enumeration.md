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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47819740207ae94b814b3009708c2fd247688661
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563999"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity 列舉
指定可以使用宣告式安全性執行的安全性動作。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`dclActionMask`|保留的。|  
|`dclActionNil`|保留的。|  
|`dclRequest`|保留的。|  
|`dclDemand`|呼叫堆疊中較高層的所有呼叫端，必須已獲得目前權限物件所指定的權限。|  
|`dclAssert`|呼叫端程式碼可以存取目前權限物件所識別的資源，即使堆疊中較高層的呼叫端未獲得存取資源的權限|  
|`dclDeny`|存取目前的使用權限物件所指定之資源的能力被拒絕呼叫端，即使使用者已獲得存取權限。|  
|`dclPermitOnly`|只可存取這個權限物件所指定的資源，即使程式碼已獲得其他資源存取權限亦然。|  
|`dclLinktimeCheck`|已授與指定的一段時間的指定權限需要立即呼叫端。|  
|`dclInheritanceCheck`|衍生的類別繼承另一個類別或覆寫的方法，才能獲得指定權限。|  
|`dclRequestMinimum`|呼叫端可以要求執行的程式碼所需的最低權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestOptional`|呼叫端可以要求的是選擇性的 （不需要執行） 的其他權限。 這項要求會隱含拒絕未特別要求的所有其他權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestRefuse`|未被授與呼叫端的要求可能遭到誤用的權限。 這個動作只能在組件的範圍內使用。|  
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
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
