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
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176184"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor 列舉
指定將檢查重複項的中繼資料權杖。  
  
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
|`MDDupAll`|檢查所有中繼資料權杖的重複項。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|不要檢查中繼資料權杖的重複項。|  
|`MDDupTypeDef`|檢查權杖的`mdTypeDef`重複項。|  
|`MDDupInterfaceImpl`|檢查權杖的`mdInterfaceImpl`重複項。|  
|`MDDupMethodDef`|檢查權杖的`mdMethodDef`重複項。|  
|`MDDupTypeRef`|檢查權杖的`mdTypeRef`重複項。|  
|`MDDupMemberRef`|檢查權杖的`mdMemberRef`重複項。|  
|`MDDupCustomAttribute`|檢查權杖的`mdCustomAttribute`重複項。|  
|`MDDupParamDef`|檢查權杖的`mdParamDef`重複項。|  
|`MDDupPermission`|檢查權杖的`mdPermission`重複項。|  
|`MDDupProperty`|檢查權杖的`mdProperty`重複項。|  
|`MDDupEvent`|檢查權杖的`mdEvent`重複項。|  
|`MDDupFieldDef`|檢查權杖的`mdFieldDef`重複項。|  
|`MDDupSignature`|檢查權杖的`mdSignature`重複項。|  
|`MDDupModuleRef`|檢查權杖的`mdModuleRef`重複項。|  
|`MDDupTypeSpec`|檢查權杖的`mdTypeSpec`重複項。|  
|`MDDupImplMap`|檢查權杖的`mdImplMap`重複項。|  
|`MDDupAssemblyRef`|檢查權杖的`mdAssemblyRef`重複項。|  
|`MDDupFile`|檢查權杖的`mdFile`重複項。|  
|`MDDupExportedType`|檢查權杖的`mdExportedType`重複項。|  
|`MDDupManifestResource`|檢查權杖的`mdManifestResource`重複項。|  
|`MDDupGenericParam`|檢查權杖的`mdGenericParam`重複項。|  
|`MDDupMethodSpec`|檢查權杖的`mdMethodSpec`重複項。|  
|`MDDupGenericParamConstraint`|檢查權杖的`mdGenericParamConstraint`重複項。|  
|`MDDupAssembly`|檢查權杖的`mdAssembly`重複項。|  
|`MDDupDefault`|檢查`mdMemberRef`、、、`mdTypeRef``mdSignature``mdTypeSpec`和`mdMethodSpec`權杖的重複項。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫德  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
