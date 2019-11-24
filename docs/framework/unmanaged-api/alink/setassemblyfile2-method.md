---
title: SetAssemblyFile2 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445594"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 方法
Sets the name of and options for a new assembly. Do not call this method when you produce unbound modules.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFilename`  
 Name of manifest file.  
  
 `pEmitter`  
 [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.  
  
 `afFlags`  
 Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Receives unique ID for the assembly being constructed.  
  
## <a name="return-value"></a>傳回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>需求  
 Requires alink.h.  
  
## <a name="see-also"></a>請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
