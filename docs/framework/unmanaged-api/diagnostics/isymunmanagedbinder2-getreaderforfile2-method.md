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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cea8a322fab6ef76873e668c622ac63e3a3f2862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 方法
提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的介面。  
  
 這個方法提供程式資料庫 (PDB) 檔比更廣泛的搜尋[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `importer`  
 [in]中繼資料匯入介面指標。  
  
 `fileName`  
 [in]指向的檔案名稱。  
  
 `searchPath`  
 [in]加入搜尋路徑中的指標。  
  
 `searchPolicy`  
 [in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要進行搜尋的符號讀取器時使用的原則。  
  
 `pRetVal`  
 [out]設定的指標所傳回 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="remarks"></a>備註  
 這個版本的方法可以搜尋 PDB 檔案的旁邊，模組以外的區域。 搜尋原則可以控制結合[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)。 例如，`AllowReferencePathAccess | AllowSymbolServerAccess`尋找 PDB 旁的可執行檔和符號伺服器上，但不會查詢登錄或可執行檔中使用的路徑。 如果`searchPath`提供參數，則一律會搜尋這些目錄。  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedBinder2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [GetReaderForFile 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
