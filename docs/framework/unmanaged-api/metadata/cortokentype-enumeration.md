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
ms.openlocfilehash: 70b28ab0ca73988093eadb9628142fecd9442948
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705471"
---
# <a name="cortokentype-enumeration"></a>CorTokenType 列舉

表示元資料標記的型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|描述|  
|------------|-----------------|  
|`mdtModule`|`mdModule`標記。|  
|`mdtTypeRef`|`mdTypeRef`標記。|  
|`mdtTypeDef`|`mdTypeDef`標記。|  
|`mdtFieldDef`|`mdFieldDef`標記。|  
|`mdtMethodDef`|`mdMethodDef`標記。|  
|`mdtParamDef`|`mdParamDef`標記。|  
|`mdtInterfaceImpl`|`mdInterfaceImpl`標記。|  
|`mdtMemberRef`|`mdMemberRef`標記。|  
|`mdtCustomAttribute`|`mdCustomAttribute`標記。|  
|`mdtPermission`|`mdPermission`標記。|  
|`mdtSignature`|`mdSignature`標記。|  
|`mdtEvent`|`mdEvent`標記。|  
|`mdtProperty`|`mdProperty`標記。|  
|`mdtModuleRef`|`mdModuleRef`標記。|  
|`mdtTypeSpec`|`mdTypeSpec`標記。|  
|`mdtAssembly`|`mdAssembly`標記。|  
|`mdtAssemblyRef`|`mdAssemblyRef`標記。|  
|`mdtFile`|`mdFile`標記。|  
|`mdtExportedType`|`mdExportedType`標記。|  
|`mdtManifestResource`|`mdManifestResource`標記。|  
|`mdtGenericParam`|`mdGenericParam`標記。|  
|`mdtMethodSpec`|`mdMethodSpec`標記。|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint`標記。|  
|`mdtString`|`mdString`標記。|  
|`mdtName`|`mdName`標記。|  
|`mdtBaseType`|未使用。|  
  
## <a name="remarks"></a>備註  

 每個值都等於對應的元資料標記中的最上層位元組值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
