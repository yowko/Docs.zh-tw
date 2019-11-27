---
title: CorFieldAttr 列舉
ms.date: 03/30/2017
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
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450310"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 列舉
包含值，這些值描述與欄位有關的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`fdFieldAccessMask`|指定協助工具資訊。|  
|`fdPrivateScope`|指定無法參考欄位。|  
|`fdPrivate`|指定欄位只能由其父類型存取。|  
|`fdFamANDAssem`|指定欄位可由其元件中的衍生類別存取。|  
|`fdAssembly`|指定欄位可由其元件中的所有類型存取。|  
|`fdFamily`|指定欄位只能由其類型和衍生類別存取。|  
|`fdFamORAssem`|指定欄位可由衍生類別以及其元件中的所有類型存取。|  
|`fdPublic`|指定此欄位可供具有此範圍可見度的所有類型存取。|  
|`fdStatic`|指定欄位是其類型的成員，而不是實例成員。|  
|`fdInitOnly`|指定欄位在初始化之後就無法變更。|  
|`fdLiteral`|指定域值是編譯時間常數。|  
|`fdNotSerialized`|指定當欄位的類型是遠端時，不會序列化該欄位。|  
|`fdSpecialName`|指定欄位為 [特殊]，而其名稱描述了如何。|  
|`fdPinvokeImpl`|指定透過 PInvoke 轉送欄位執行。|  
|`fdReservedMask`|保留供 common language runtime 內部使用。|  
|`fdRTSpecialName`|指定 common language runtime 中繼資料內部 Api 應該檢查名稱的編碼方式。|  
|`fdHasFieldMarshal`|指定欄位包含封送處理資訊。|  
|`fdHasDefault`|指定欄位具有預設值。|  
|`fdHasFieldRVA`|指定欄位具有相對的虛擬位址。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
