---
title: "CorDeclSecurity 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
|`dclAssert`|即使堆疊中較高層的呼叫端未獲得存取資源的權限，呼叫程式碼可以存取目前權限物件所識別的資源|  
|`dclDeny`|即使使用者已獲得存取權限給呼叫者，拒絕存取目前權限物件所指定之資源的能力。|  
|`dclPermitOnly`|只可存取這個權限物件所指定的資源，即使程式碼已獲得其他資源存取權限亦然。|  
|`dclLinktimeCheck`|立即呼叫者，才能被授與指定的一段時間的指定權限。|  
|`dclInheritanceCheck`|在衍生的類別繼承另一個類別，或覆寫的方法，才能被授與指定權限。|  
|`dclRequestMinimum`|呼叫端可以要求執行的程式碼所需的最低權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestOptional`|呼叫端可以要求其他權限為選擇性 （不需要執行）。 這項要求會隱含拒絕未特別要求的所有其他權限。 這個動作只能在組件的範圍內使用。|  
|`dclRequestRefuse`|未被授與呼叫者的要求可能會誤用的權限。 這個動作只能在組件的範圍內使用。|  
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
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
