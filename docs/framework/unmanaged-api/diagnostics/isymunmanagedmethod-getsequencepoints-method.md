---
title: ISymUnmanagedMethod::GetSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a35f35d7aea34c0ef08c30415fde75fe71e645
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints 方法
取得這個方法內的所有序列點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a>參數  
 `cPoints`  
 [in]A`ULONG32`大小`offsets`， `documents`， `lines`， `columns`， `endLines`，和`endColumns`陣列。  
  
 `pcPoints`  
 [out]指標`ULONG32`接收包含序列點所需的緩衝區的長度。  
  
 `offsets`  
 [in]陣列，用來儲存 Microsoft intermediate language (MSIL) 位移的起點的序列點的方法。  
  
 `documents`  
 [in]用來儲存所在的序列點所在文件陣列。  
  
 `lines`  
 [in]用來儲存中序列點所在文件行陣列。  
  
 `columns`  
 [in]用來儲存資料行中的序列點所在文件陣列。  
  
 `endLines`  
 [in]序列點結束處的文件行陣列。  
  
 `endColumns`  
 [in]序列點結束處的文件中的資料行陣列。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
