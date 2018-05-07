---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c84aceb0faabd879911e9595a7f3154065e2191
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法
傳回的陣列的方法，其中每個包含文件中指定位置的中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>參數  
 `document`  
 [in]指定的文件。  
  
 `line`  
 [in]指定的文件行。  
  
 `column`  
 [in]指定的文件的資料行。  
  
 `cMethod`  
 [in] `pRetVal` 陣列的大小。  
  
 `pcMethod`  
 [out]此變數會接收中傳回的元素數目的指標`pRetVal`陣列。  
  
 `pRetVal`  
 [out]陣列的指標，其中每個指向[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)物件，代表包含中斷點的方法。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
