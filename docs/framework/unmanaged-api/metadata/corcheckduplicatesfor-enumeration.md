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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074868"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor 列舉
指定要檢查重複項目中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`MDDupAll`|請檢查重複項目的所有中繼資料語彙基元。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|不會檢查重複項目中繼資料語彙基元。|  
|`MDDupTypeDef`|檢查是否有重複的`mdTypeDef`語彙基元。|  
|`MDDupInterfaceImpl`|檢查是否有重複的`mdInterfaceImpl`語彙基元。|  
|`MDDupMethodDef`|檢查是否有重複的`mdMethodDef`語彙基元。|  
|`MDDupTypeRef`|檢查是否有重複的`mdTypeRef`語彙基元。|  
|`MDDupMemberRef`|檢查是否有重複的`mdMemberRef`語彙基元。|  
|`MDDupCustomAttribute`|檢查是否有重複的`mdCustomAttribute`語彙基元。|  
|`MDDupParamDef`|檢查是否有重複的`mdParamDef`語彙基元。|  
|`MDDupPermission`|檢查是否有重複的`mdPermission`語彙基元。|  
|`MDDupProperty`|檢查是否有重複的`mdProperty`語彙基元。|  
|`MDDupEvent`|檢查是否有重複的`mdEvent`語彙基元。|  
|`MDDupFieldDef`|檢查是否有重複的`mdFieldDef`語彙基元。|  
|`MDDupSignature`|檢查是否有重複的`mdSignature`語彙基元。|  
|`MDDupModuleRef`|檢查是否有重複的`mdModuleRef`語彙基元。|  
|`MDDupTypeSpec`|檢查是否有重複的`mdTypeSpec`語彙基元。|  
|`MDDupImplMap`|檢查是否有重複的`mdImplMap`語彙基元。|  
|`MDDupAssemblyRef`|檢查是否有重複的`mdAssemblyRef`語彙基元。|  
|`MDDupFile`|檢查是否有重複的`mdFile`語彙基元。|  
|`MDDupExportedType`|檢查是否有重複的`mdExportedType`語彙基元。|  
|`MDDupManifestResource`|檢查是否有重複的`mdManifestResource`語彙基元。|  
|`MDDupGenericParam`|檢查是否有重複的`mdGenericParam`語彙基元。|  
|`MDDupMethodSpec`|檢查是否有重複的`mdMethodSpec`語彙基元。|  
|`MDDupGenericParamConstraint`|檢查是否有重複的`mdGenericParamConstraint`語彙基元。|  
|`MDDupAssembly`|檢查是否有重複的`mdAssembly`語彙基元。|  
|`MDDupDefault`|檢查是否有重複項目`mdMemberRef`， `mdTypeRef`， `mdSignature`， `mdTypeSpec`，和`mdMethodSpec`語彙基元。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
