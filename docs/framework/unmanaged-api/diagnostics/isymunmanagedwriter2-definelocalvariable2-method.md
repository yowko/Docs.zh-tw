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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53f02499bbc64f1502951ff9fbf16a848e77f0ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 方法
在目前的語彙範圍中定義單一變數。 可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。 在此情況下，不過，值`startOffset`和`endOffset`參數不能重疊。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `name`  
 [in]本機變數的名稱。  
  
 `attributes`  
 [in]本機變數的屬性。  
  
 `sigToken`  
 [in]簽章的中繼資料語彙基元。  
  
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
 **標頭：**於 CorSym.idl  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
