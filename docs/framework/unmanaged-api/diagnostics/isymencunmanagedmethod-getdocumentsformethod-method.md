---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b329d096a23df673de038036fa5ea196cbe0eac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736067"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethod 方法
取得這個方法有幾行中的文件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a>參數  
 `cDocs`  
 [in]所指向緩衝區的長度`pcDocs`。  
  
 `pcDocs`  
 [out]指標`ULONG32`接收大小，以字元為單位，包含文件所需的緩衝區。  
  
 `documents`  
 [in]包含文件的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，出現錯誤代碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
