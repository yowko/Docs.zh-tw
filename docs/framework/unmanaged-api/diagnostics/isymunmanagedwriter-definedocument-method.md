---
title: ISymUnmanagedWriter::DefineDocument 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615224"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument 方法
定義來源文件。 系統會提供已知語言、廠商和檔案類型的 Guid。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `url`  
 在的指標 `WCHAR` ，定義可識別檔的統一資源定位器（URL）。  
  
 `language`  
 在定義檔語言之 GUID 的指標。  
  
 `languageVendor`  
 在GUID 的指標，定義檔語言的廠商身分識別。  
  
 `documentType`  
 在定義檔案類型之 GUID 的指標。  
  
 `pRetVal`  
 脫銷傳回之[ISymUnmanagedWriter](isymunmanagedwriter-interface.md)介面的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
