---
title: ISymUnmanagedBinder2::GetReaderForFile2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: e0fc6cf2a08de4a00cb8b7f98d3922df98f427c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706966"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 方法

指定中繼資料介面和檔案名之後，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面，以讀取與模組相關聯的偵錯工具符號。  
  
 這個方法可讓您更廣泛地搜尋程式資料庫 (PDB) 檔案，而不是 [ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>參數  

 `importer`  
 在中繼資料匯入介面的指標。  
  
 `fileName`  
 在檔案名的指標。  
  
 `searchPath`  
 在搜尋路徑的指標。  
  
 `searchPolicy`  
 在 [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) 列舉的值，這個值會指定在搜尋符號讀取器時要使用的原則。  
  
 `pRetVal`  
 擴展設定為傳回之 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面的指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="remarks"></a>備註  

 這個版本的方法可以在模組旁的區域內搜尋 PDB 檔案。 您可以藉由結合 [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)來控制搜尋原則。 例如， `AllowReferencePathAccess | AllowSymbolServerAccess` 會尋找可執行檔和符號伺服器上的 PDB，但不會查詢登錄或使用可執行檔中的路徑。 如果 `searchPath` 有提供參數，一律會搜尋這些目錄。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)
- [GetReaderForFile 方法](isymunmanagedbinder-getreaderforfile-method.md)
