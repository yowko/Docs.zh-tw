---
title: ISymUnmanagedBinder3::GetReaderFromCallback 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9487cf89d87b5f373302dc49a08c4fabb719e746
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940006"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback 方法
可讓使用者實作，或可能是提供透過回呼`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`從記憶體中取得的偵錯資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `importer`  
 [in]中繼資料匯入介面指標。  
  
 `fileName`  
 [in]檔案名稱指標。  
  
 `searchPath`  
 [in]加入搜尋路徑的指標。  
  
 `searchPolicy`  
 [in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要在進行搜尋的符號讀取器時使用的原則。  
  
 `callback`  
 [in]回呼函式的指標。  
  
 `pRetVal`  
 [out]設定指標所傳回[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym.idl  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedBinder3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
