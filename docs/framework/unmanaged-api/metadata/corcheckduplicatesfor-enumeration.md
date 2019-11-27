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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443783"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`MDDupAll`|檢查所有元資料標記的重複專案。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|請勿檢查元資料標記是否有重複的專案。|  
|`MDDupTypeDef`|檢查 `mdTypeDef` token 的重複專案。|  
|`MDDupInterfaceImpl`|檢查 `mdInterfaceImpl` token 的重複專案。|  
|`MDDupMethodDef`|檢查 `mdMethodDef` token 的重複專案。|  
|`MDDupTypeRef`|檢查 `mdTypeRef` token 的重複專案。|  
|`MDDupMemberRef`|檢查 `mdMemberRef` token 的重複專案。|  
|`MDDupCustomAttribute`|檢查 `mdCustomAttribute` token 的重複專案。|  
|`MDDupParamDef`|檢查 `mdParamDef` token 的重複專案。|  
|`MDDupPermission`|檢查 `mdPermission` token 的重複專案。|  
|`MDDupProperty`|檢查 `mdProperty` token 的重複專案。|  
|`MDDupEvent`|檢查 `mdEvent` token 的重複專案。|  
|`MDDupFieldDef`|檢查 `mdFieldDef` token 的重複專案。|  
|`MDDupSignature`|檢查 `mdSignature` token 的重複專案。|  
|`MDDupModuleRef`|檢查 `mdModuleRef` token 的重複專案。|  
|`MDDupTypeSpec`|檢查 `mdTypeSpec` token 的重複專案。|  
|`MDDupImplMap`|檢查 `mdImplMap` token 的重複專案。|  
|`MDDupAssemblyRef`|檢查 `mdAssemblyRef` token 的重複專案。|  
|`MDDupFile`|檢查 `mdFile` token 的重複專案。|  
|`MDDupExportedType`|檢查 `mdExportedType` token 的重複專案。|  
|`MDDupManifestResource`|檢查 `mdManifestResource` token 的重複專案。|  
|`MDDupGenericParam`|檢查 `mdGenericParam` token 的重複專案。|  
|`MDDupMethodSpec`|檢查 `mdMethodSpec` token 的重複專案。|  
|`MDDupGenericParamConstraint`|檢查 `mdGenericParamConstraint` token 的重複專案。|  
|`MDDupAssembly`|檢查 `mdAssembly` token 的重複專案。|  
|`MDDupDefault`|檢查 `mdMemberRef`、`mdTypeRef`、`mdSignature`、`mdTypeSpec`和 `mdMethodSpec` 權杖的重複專案。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
