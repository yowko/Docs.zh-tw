---
title: "ISymUnmanagedWriter::DefineLocalVariable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e454aa2c2dd8ceb8f8dbbc03bdd1e70e8a800de2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable 方法
在目前的語彙範圍中定義單一變數。 可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。 在此情況下，不過，值`startOffset`和`endOffset`參數不能重疊。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `name`  
 [in]指標`WCHAR`定義本機變數的名稱。  
  
 `attributes`  
 [in]本機變數的屬性。  
  
 `cSig`  
 [in]A`ULONG32`指出的大小，以位元組為單位，`signature`緩衝區。  
  
 `signature`  
 [in]區域變數簽章。  
  
 `addrKind`  
 [in]地址類型。  
  
 `addr1`  
 [in]參數規格的第一個位址。  
  
 `addr2`  
 [in]參數規格的第二個位址。  
  
 `addr3`  
 [in]參數規格的第三個位址。  
  
 `startOffset`  
 [in]變數的起始位移。 這是選擇性參數。 如果是 0，會忽略這個參數，並會在整個範圍中定義變數。 如果它是非零值，變數會落在目前範圍的位移之內。  
  
 `endOffset`  
 [in]變數的結束位移。 這是選擇性參數。 如果是 0，會忽略這個參數，並會在整個範圍中定義變數。 如果它是非零值，變數會落在目前範圍的位移之內。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [DefineLocalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
