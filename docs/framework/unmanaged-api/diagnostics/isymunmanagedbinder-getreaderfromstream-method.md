---
title: ISymUnmanagedBinder::GetReaderFromStream 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 955a2b63c457342d6aa31755ce42e989cc791e5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776848"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream 方法
提供中繼資料介面並包含符號存放區的資料流，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)指定的符號存放區的結構，將讀取偵錯符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `importer`  
 [in]中繼資料匯入介面指標。  
  
 `pstream`  
 [in]包含符號存放區的資料流指標。  
  
 `pRetVal`  
 [out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
