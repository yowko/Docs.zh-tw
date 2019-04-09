---
title: ISymUnmanagedBinder::GetReaderForFile 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0414cadca910f3290f96a841e3f807f0de469606
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145960"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile 方法
提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的介面。  
  
 這個方法會開啟程式資料庫 (PDB) 檔案，才可執行檔的檔案旁邊。 這項變更已基於安全性考量。 如果您需要更廣泛的搜尋，對 PDB 檔案時，使用[ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `importer`  
 [in]中繼資料匯入介面指標。  
  
 `fileName`  
 [in]檔案名稱指標。  
  
 `searchPath`  
 [in]加入搜尋路徑的指標。  
  
 `pRetVal`  
 [out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [GetReaderForFile2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
