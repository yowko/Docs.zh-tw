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
ms.openlocfilehash: 7ae978f5d2c9f7e90f4549c15a3935b441eabf04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434003"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader 介面
表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|尋找檔。|  
|[GetDocuments 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|傳回符號存放區中定義之所有檔的陣列。|  
|[GetDocumentVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|取得指定檔的指定版本。|  
|[GetGlobalVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|傳回所有全域變數。|  
|[GetMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|取得符號讀取器方法，並指定方法 token。|  
|[GetMethodByVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|取得符號讀取器方法，並指定方法權杖和編輯和複製版本號碼。|  
|[GetMethodFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|傳回方法，其中包含檔中指定位置的中斷點。|  
|[GetMethodsFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|傳回方法的陣列，其中每一個都包含檔中指定位置的中斷點。|  
|[GetMethodVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|取得方法版本。|  
|[GetNamespaces 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|取得在這個符號存放區的全域範圍中定義的命名空間。|  
|[GetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|依據名稱取得自訂屬性。|  
|[GetSymbolStoreFileName 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|提供符號存放區的磁片檔案名。|  
|[GetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|傳回指定為模組之使用者進入點的方法（如果有的話）。|  
|[GetVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|傳回非區域變數，並指定其父系和名稱。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|使用與此讀取器相關聯的中繼資料匯入介面，以及模組的檔案名，初始化符號讀取器。|  
|[ReplaceSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|以差異符號存放區來取代現有的符號存放區。|  
|[UpdateSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|以差異符號存放區來更新現有的符號存放區。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
