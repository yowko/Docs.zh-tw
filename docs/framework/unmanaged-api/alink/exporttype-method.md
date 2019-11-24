---
title: ExportType 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438564"
---
# <a name="exporttype-method"></a>ExportType 方法
Specifies that a type is exportable.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 ID of the assembly to export from.  
  
 `FileToken`  
 File token or assembly ID of file that defines the exportable type.  
  
 `TypeToken`  
 Token of type to be made exportable.  
  
 `pszTypename`  
 Fully qualified type name to be made exportable.  
  
 `dwFlags`  
 `ComType` flags such as `tdPublic` or `tdNested`. This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Receives token for exported type.  
  
## <a name="return-value"></a>傳回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>需求  
 Requires alink.h  
  
## <a name="see-also"></a>請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
