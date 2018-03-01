---
title: "CorFieldAttr 列舉"
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
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5128ea59f7668737885835723156fc7f1786872
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 列舉
包含值，這些值描述與欄位有關的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`fdFieldAccessMask`|指定的協助工具資訊。|  
|`fdPrivateScope`|指定的欄位不能參考。|  
|`fdPrivate`|指定欄位可存取只能由其父型別。|  
|`fdFamANDAssem`|指定欄位是由其組件中的衍生類別存取。|  
|`fdAssembly`|指定欄位可存取其組件中的所有型別。|  
|`fdFamily`|指定欄位只有才可以存取它的型別和衍生類別。|  
|`fdFamORAssem`|指定欄位可存取衍生的類別和其組件中的所有型別。|  
|`fdPublic`|指定欄位可存取此範圍的可見性與所有類型。|  
|`fdStatic`|指定欄位是其類型的成員，而不是執行個體成員。|  
|`fdInitOnly`|指定在初始化之後，無法變更欄位。|  
|`fdLiteral`|指定欄位值是編譯時間常數。|  
|`fdNotSerialized`|指定當其類型為遠端時，則不會序列化的欄位。|  
|`fdSpecialName`|指定欄位是特殊的且其名稱描述如何。|  
|`fdPinvokeImpl`|指定欄位的實作會透過 PInvoke 轉送。|  
|`fdReservedMask`|保留供內部使用的 common language runtime。|  
|`fdRTSpecialName`|指定用 common language runtime 中繼資料內部的應用程式開發介面應該檢查名稱的編碼方式。|  
|`fdHasFieldMarshal`|指定的欄位包含封送處理資訊。|  
|`fdHasDefault`|指定的欄位具有預設值。|  
|`fdHasFieldRVA`|指定的欄位具有相對虛擬位址。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
