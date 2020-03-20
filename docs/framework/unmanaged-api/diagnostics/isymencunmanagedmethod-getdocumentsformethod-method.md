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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176626"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethod 方法
獲取此方法中具有行的文檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a>參數  
 `cDocs`  
 [在]指向 的緩衝區的長度`pcDocs`。  
  
 `pcDocs`  
 [出]指向 的指標`ULONG32`，該指標接收包含文檔所需的緩衝區的大小（以字元表示）。  
  
 `documents`  
 [在]包含文檔的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，S_OK;否則，錯誤代碼。  
  
## <a name="requirements"></a>需求  
 **標題：** 科西姆.伊德爾，科西姆.h  
  
## <a name="see-also"></a>另請參閱

- [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
