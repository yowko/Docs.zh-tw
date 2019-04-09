---
title: ISymUnmanagedReader 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147208"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader 介面
表示符號讀取器可存取文件、 方法和符號存放區內的變數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|尋找文件。|  
|[GetDocuments 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|傳回定義在符號存放區中的所有文件的陣列。|  
|[GetDocumentVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|取得指定的文件的指定的版本。|  
|[GetGlobalVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|傳回所有全域變數。|  
|[GetMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|取得符號讀取器方法，指定方法的語彙基元。|  
|[GetMethodByVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|取得符號讀取器方法，指定方法的語彙基元和編輯複製版本號碼。|  
|[GetMethodFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|傳回包含文件中指定位置的中斷點的方法。|  
|[GetMethodsFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|傳回的陣列的方法，其中每一個包含文件中指定位置的中斷點。|  
|[GetMethodVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|取得方法的版本。|  
|[GetNamespaces 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|取得在這個符號存放區內的全域範圍中定義的命名空間。|  
|[GetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|取得自訂屬性，根據其名稱。|  
|[GetSymbolStoreFileName 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|提供符號存放區的磁碟上檔案名稱。|  
|[GetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|如果有的話，會傳回已指定為模組的使用者進入點方法。|  
|[GetVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|傳回非本機變數中，指定其父系和名稱。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|初始化符號讀取器，這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面。|  
|[ReplaceSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|以差異符號存放區來取代現有的符號存放區。|  
|[UpdateSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|以差異符號存放區來更新現有的符號存放區。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
