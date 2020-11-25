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
ms.openlocfilehash: b8b9f8e63a0b52dde0e814f53cfc75e6f6d48e78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723021"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable 方法

在目前的語彙範圍中定義單一變數。 您可以針對相同名稱的變數多次呼叫這個方法，該變數在整個範圍中有多個主主。 但是在此情況下，和參數的值 `startOffset` 不能重 `endOffset` 迭。  
  
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
 在的指標 `WCHAR` ，定義本機變數名稱。  
  
 `attributes`  
 在本機變數屬性。  
  
 `cSig`  
 在， `ULONG32` 表示緩衝區的大小（以位元組為單位） `signature` 。  
  
 `signature`  
 在本機變數簽章。  
  
 `addrKind`  
 在網址類別型。  
  
 `addr1`  
 在參數規格的第一個位址。  
  
 `addr2`  
 在參數規格的第二個位址。  
  
 `addr3`  
 在參數規格的第三個位址。  
  
 `startOffset`  
 在變數的起始位移。 這是選擇性參數。 如果為0，則會忽略此參數，並在整個範圍中定義變數。 如果是非零值，則變數會落在目前範圍的位移內。  
  
 `endOffset`  
 在變數的結束位移。 這是選擇性參數。 如果為0，則會忽略此參數，並在整個範圍中定義變數。 如果是非零值，則變數會落在目前範圍的位移內。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable 方法](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 方法](isymunmanagedwriter2-definelocalvariable2-method.md)
