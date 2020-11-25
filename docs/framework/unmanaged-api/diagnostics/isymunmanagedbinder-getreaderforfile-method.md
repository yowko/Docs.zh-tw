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
ms.openlocfilehash: ac895032e70cf31532ab4c73409d6d750eae65df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706992"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile 方法

指定中繼資料介面和檔案名之後，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面，以讀取與模組相關聯的偵錯工具符號。  
  
 只有當程式資料庫位於可執行檔的旁邊時，此方法才會 (PDB) 檔中開啟該資料庫。 基於安全性考慮，已進行這種變更。 如果您需要更廣泛的 PDB 檔案搜尋，請使用 [ISymUnmanagedBinder2：： GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>參數  

 `importer`  
 在中繼資料匯入介面的指標。  
  
 `fileName`  
 在檔案名的指標。  
  
 `searchPath`  
 在搜尋路徑的指標。  
  
 `pRetVal`  
 擴展設定為傳回之 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面的指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)
- [GetReaderForFile2 方法](isymunmanagedbinder2-getreaderforfile2-method.md)
