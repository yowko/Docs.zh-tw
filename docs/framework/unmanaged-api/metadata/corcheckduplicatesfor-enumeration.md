---
title: CorCheckDuplicatesFor 列舉
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007893"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor 列舉
指定將檢查是否有重複的元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`MDDupAll`|檢查所有元資料標記的重複專案。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|請勿檢查元資料標記是否有重複的專案。|  
|`MDDupTypeDef`|檢查是否有重複的 `mdTypeDef` 權杖。|  
|`MDDupInterfaceImpl`|檢查是否有重複的 `mdInterfaceImpl` 權杖。|  
|`MDDupMethodDef`|檢查是否有重複的 `mdMethodDef` 權杖。|  
|`MDDupTypeRef`|檢查是否有重複的 `mdTypeRef` 權杖。|  
|`MDDupMemberRef`|檢查是否有重複的 `mdMemberRef` 權杖。|  
|`MDDupCustomAttribute`|檢查是否有重複的 `mdCustomAttribute` 權杖。|  
|`MDDupParamDef`|檢查是否有重複的 `mdParamDef` 權杖。|  
|`MDDupPermission`|檢查是否有重複的 `mdPermission` 權杖。|  
|`MDDupProperty`|檢查是否有重複的 `mdProperty` 權杖。|  
|`MDDupEvent`|檢查是否有重複的 `mdEvent` 權杖。|  
|`MDDupFieldDef`|檢查是否有重複的 `mdFieldDef` 權杖。|  
|`MDDupSignature`|檢查是否有重複的 `mdSignature` 權杖。|  
|`MDDupModuleRef`|檢查是否有重複的 `mdModuleRef` 權杖。|  
|`MDDupTypeSpec`|檢查是否有重複的 `mdTypeSpec` 權杖。|  
|`MDDupImplMap`|檢查是否有重複的 `mdImplMap` 權杖。|  
|`MDDupAssemblyRef`|檢查是否有重複的 `mdAssemblyRef` 權杖。|  
|`MDDupFile`|檢查是否有重複的 `mdFile` 權杖。|  
|`MDDupExportedType`|檢查是否有重複的 `mdExportedType` 權杖。|  
|`MDDupManifestResource`|檢查是否有重複的 `mdManifestResource` 權杖。|  
|`MDDupGenericParam`|檢查是否有重複的 `mdGenericParam` 權杖。|  
|`MDDupMethodSpec`|檢查是否有重複的 `mdMethodSpec` 權杖。|  
|`MDDupGenericParamConstraint`|檢查是否有重複的 `mdGenericParamConstraint` 權杖。|  
|`MDDupAssembly`|檢查是否有重複的 `mdAssembly` 權杖。|  
|`MDDupDefault`|檢查 `mdMemberRef` 、 `mdTypeRef` 、 `mdSignature` 、 `mdTypeSpec` 和 `mdMethodSpec` 權杖的重複專案。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
