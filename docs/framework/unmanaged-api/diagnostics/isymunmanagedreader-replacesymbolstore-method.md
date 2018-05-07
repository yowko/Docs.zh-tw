---
title: ISymUnmanagedReader::ReplaceSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03607cf96d73e96eef63fe62b86b50be02f34421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore 方法
以差異符號存放區來取代現有的符號存放區。 這個方法是類似於[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法，不同之處在於指定的差異做為完全取代，而非更新。  
  
> [!NOTE]
>  您必須指定其中`filename`或`pIStream`參數不可同時為兩者。 如果`filename`指定，則使用該檔案中的符號，符號存放區將會更新。 如果`pIStream`指定，則會更新存放區，以從資料<xref:System.Runtime.InteropServices.ComTypes.IStream>。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 [in]包含符號存放區的檔案名稱。  
  
 `pIStream`  
 [in]檔案資料流，做為替代`filename`參數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
