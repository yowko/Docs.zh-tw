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
ms.openlocfilehash: 4e40f684cc1578672cb8ff474972ce9cdc39efb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718822"
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`fdFieldAccessMask`|指定協助工具資訊。|  
|`fdPrivateScope`|指定無法參考此欄位。|  
|`fdPrivate`|指定欄位只能由其父類型存取。|  
|`fdFamANDAssem`|指定欄位可透過其元件中的衍生類別來存取。|  
|`fdAssembly`|指定欄位可供其元件中的所有類型存取。|  
|`fdFamily`|指定欄位只能透過其型別和衍生類別來存取。|  
|`fdFamORAssem`|指定欄位可供衍生類別以及其元件中的所有類型存取。|  
|`fdPublic`|指定欄位可供所有具有此範圍可見度的類型存取。|  
|`fdStatic`|指定欄位是其類型的成員，而不是實例成員。|  
|`fdInitOnly`|指定欄位在初始化之後便無法變更。|  
|`fdLiteral`|指定域值為編譯時間常數。|  
|`fdNotSerialized`|指定當欄位的類型為遠端時，不序列化欄位。|  
|`fdSpecialName`|指定欄位是特殊的，且其名稱會描述如何。|  
|`fdPinvokeImpl`|指定透過 PInvoke 轉送欄位執行。|  
|`fdReservedMask`|保留給 common language runtime 內部使用。|  
|`fdRTSpecialName`|指定 common language runtime 中繼資料內部 Api 應該檢查名稱的編碼方式。|  
|`fdHasFieldMarshal`|指定欄位包含封送處理資訊。|  
|`fdHasDefault`|指定此欄位含有預設值。|  
|`fdHasFieldRVA`|指定欄位具有相對虛擬位址。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
