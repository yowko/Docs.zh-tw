---
title: ISymUnmanagedWriter::DefineLocalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9466df3f6413f86eb8558f0037b96c254b2a2e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777335"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable 方法
在目前的語彙範圍中定義單一變數。 可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。 在此情況下，不過，值`startOffset`和`endOffset`參數不得重疊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 [in]指標`WCHAR`定義本機變數的名稱。  
  
 `attributes`  
 [in]本機變數的屬性。  
  
 `cSig`  
 [in]A`ULONG32`表示的大小，以位元組為單位，`signature`緩衝區。  
  
 `signature`  
 [in]區域變數簽章。  
  
 `addrKind`  
 [in]位址類型。  
  
 `addr1`  
 [in]參數規格的第一個位址。  
  
 `addr2`  
 [in]參數規格的第二個位址。  
  
 `addr3`  
 [in]參數規格的第三個位址。  
  
 `startOffset`  
 [in]變數的起始位移。 這個參數是選擇性的。 如果是 0，會忽略這個參數，並在整個範圍定義的變數。 如果它是非零值時，變數會落在目前的範圍的位移。  
  
 `endOffset`  
 [in]變數的結束位移。 這個參數是選擇性的。 如果是 0，會忽略這個參數，並在整個範圍定義的變數。 如果它是非零值時，變數會落在目前的範圍的位移。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
