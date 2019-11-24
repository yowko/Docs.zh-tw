---
title: ISymUnmanagedWriter2::DefineLocalVariable2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438301"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 方法
在目前的語彙範圍中定義單一變數。 This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope. In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 [in] The local variable name.  
  
 `attributes`  
 [in] The local variable attributes.  
  
 `sigToken`  
 [in] The metadata token of the signature.  
  
 `addrKind`  
 [in] The address type.  
  
 `addr1`  
 [in] The first address for the parameter specification.  
  
 `addr2`  
 [in] The second address for the parameter specification.  
  
 `addr3`  
 [in] The third address for the parameter specification.  
  
 `startOffset`  
 [in] The start offset for the variable. 這是選擇性參數。 If it is 0, this parameter is ignored and the variable is defined throughout the entire scope. If it is a nonzero value, the variable falls within the offsets of the current scope.  
  
 `endOffset`  
 [in] The end offset for the variable. 這是選擇性參數。 If it is 0, this parameter is ignored and the variable is defined throughout the entire scope. If it is a nonzero value, the variable falls within the offsets of the current scope.  
  
## <a name="return-value"></a>傳回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
