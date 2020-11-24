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
ms.openlocfilehash: 4acdfd6df410f229a002fa191ef24766748a1262
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672353"
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
  
|member|描述|  
|------------|-----------------|  
|`MDDupAll`|檢查重複專案的所有元資料標記。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|請勿檢查重複專案的元資料標記。|  
|`MDDupTypeDef`|檢查是否有重複的 `mdTypeDef` 標記。|  
|`MDDupInterfaceImpl`|檢查是否有重複的 `mdInterfaceImpl` 標記。|  
|`MDDupMethodDef`|檢查是否有重複的 `mdMethodDef` 標記。|  
|`MDDupTypeRef`|檢查是否有重複的 `mdTypeRef` 標記。|  
|`MDDupMemberRef`|檢查是否有重複的 `mdMemberRef` 標記。|  
|`MDDupCustomAttribute`|檢查是否有重複的 `mdCustomAttribute` 標記。|  
|`MDDupParamDef`|檢查是否有重複的 `mdParamDef` 標記。|  
|`MDDupPermission`|檢查是否有重複的 `mdPermission` 標記。|  
|`MDDupProperty`|檢查是否有重複的 `mdProperty` 標記。|  
|`MDDupEvent`|檢查是否有重複的 `mdEvent` 標記。|  
|`MDDupFieldDef`|檢查是否有重複的 `mdFieldDef` 標記。|  
|`MDDupSignature`|檢查是否有重複的 `mdSignature` 標記。|  
|`MDDupModuleRef`|檢查是否有重複的 `mdModuleRef` 標記。|  
|`MDDupTypeSpec`|檢查是否有重複的 `mdTypeSpec` 標記。|  
|`MDDupImplMap`|檢查是否有重複的 `mdImplMap` 標記。|  
|`MDDupAssemblyRef`|檢查是否有重複的 `mdAssemblyRef` 標記。|  
|`MDDupFile`|檢查是否有重複的 `mdFile` 標記。|  
|`MDDupExportedType`|檢查是否有重複的 `mdExportedType` 標記。|  
|`MDDupManifestResource`|檢查是否有重複的 `mdManifestResource` 標記。|  
|`MDDupGenericParam`|檢查是否有重複的 `mdGenericParam` 標記。|  
|`MDDupMethodSpec`|檢查是否有重複的 `mdMethodSpec` 標記。|  
|`MDDupGenericParamConstraint`|檢查是否有重複的 `mdGenericParamConstraint` 標記。|  
|`MDDupAssembly`|檢查是否有重複的 `mdAssembly` 標記。|  
|`MDDupDefault`|檢查 `mdMemberRef` 、、 `mdTypeRef` `mdSignature` 、 `mdTypeSpec` 和 `mdMethodSpec` 權杖的重複專案。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
