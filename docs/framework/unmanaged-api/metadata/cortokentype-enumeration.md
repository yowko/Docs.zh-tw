---
title: CorTokenType 列舉
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b33b50e53c454f2b62253d12943ea044240d8cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045197"
---
# <a name="cortokentype-enumeration"></a>CorTokenType 列舉
表示中繼資料語彙基元的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`mdtModule`|`mdModule`語彙基元。|  
|`mdtTypeRef`|`mdTypeRef`語彙基元。|  
|`mdtTypeDef`|`mdTypeDef`語彙基元。|  
|`mdtFieldDef`|`mdFieldDef`語彙基元。|  
|`mdtMethodDef`|`mdMethodDef`語彙基元。|  
|`mdtParamDef`|`mdParamDef`語彙基元。|  
|`mdtInterfaceImpl`|`mdInterfaceImpl`語彙基元。|  
|`mdtMemberRef`|`mdMemberRef`語彙基元。|  
|`mdtCustomAttribute`|`mdCustomAttribute`語彙基元。|  
|`mdtPermission`|`mdPermission`語彙基元。|  
|`mdtSignature`|`mdSignature`語彙基元。|  
|`mdtEvent`|`mdEvent`語彙基元。|  
|`mdtProperty`|`mdProperty`語彙基元。|  
|`mdtModuleRef`|`mdModuleRef`語彙基元。|  
|`mdtTypeSpec`|`mdTypeSpec`語彙基元。|  
|`mdtAssembly`|`mdAssembly`語彙基元。|  
|`mdtAssemblyRef`|`mdAssemblyRef`語彙基元。|  
|`mdtFile`|`mdFile`語彙基元。|  
|`mdtExportedType`|`mdExportedType`語彙基元。|  
|`mdtManifestResource`|`mdManifestResource`語彙基元。|  
|`mdtGenericParam`|`mdGenericParam`語彙基元。|  
|`mdtMethodSpec`|`mdMethodSpec`語彙基元。|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint`語彙基元。|  
|`mdtString`|`mdString`語彙基元。|  
|`mdtName`|`mdName`語彙基元。|  
|`mdtBaseType`|未使用。|  
  
## <a name="remarks"></a>備註  
 每個值會等於對應的中繼資料語彙基元中的第一個位元組值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
