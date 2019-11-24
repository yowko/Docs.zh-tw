---
title: EmitAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: 6bbe5db75ded15f32a6ff3564e1116d40a745a65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446530"
---
# <a name="emitassembly-method"></a>EmitAssembly 方法
Creates the assembly. Call this method after all other files are closed except for the assembly file. Do not call this method when producing unbound modules.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 ID of the assembly.  
  
## <a name="return-value"></a>傳回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>需求  
 Requires alink.h  
  
## <a name="see-also"></a>請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
