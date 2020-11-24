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
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675863"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader 介面

代表可讓您存取符號存放區內文件、方法和變數的符號讀取器。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument 方法](isymunmanagedreader-getdocument-method.md)|尋找檔。|  
|[GetDocuments 方法](isymunmanagedreader-getdocuments-method.md)|傳回符號存放區中定義的所有檔的陣列。|  
|[GetDocumentVersion 方法](isymunmanagedreader-getdocumentversion-method.md)|取得指定之檔的指定版本。|  
|[GetGlobalVariables 方法](isymunmanagedreader-getglobalvariables-method.md)|傳回所有全域變數。|  
|[GetMethod 方法](isymunmanagedreader-getmethod-method.md)|取得符號讀取器方法（指定方法標記）。|  
|[GetMethodByVersion 方法](isymunmanagedreader-getmethodbyversion-method.md)|取得符號讀取器方法，指定方法 token 和編輯和複製版本號碼。|  
|[GetMethodFromDocumentPosition 方法](isymunmanagedreader-getmethodfromdocumentposition-method.md)|傳回方法，這個方法會在檔中的指定位置包含中斷點。|  
|[GetMethodsFromDocumentPosition 方法](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|傳回方法的陣列，其中每一個都包含檔中指定位置的中斷點。|  
|[GetMethodVersion 方法](isymunmanagedreader-getmethodversion-method.md)|取得方法版本。|  
|[GetNamespaces 方法](isymunmanagedreader-getnamespaces-method.md)|取得在此符號存放區內的全域範圍中定義的命名空間。|  
|[GetSymAttribute 方法](isymunmanagedreader-getsymattribute-method.md)|根據名稱，取得自訂屬性。|  
|[GetSymbolStoreFileName 方法](isymunmanagedreader-getsymbolstorefilename-method.md)|提供符號存放區的磁片上檔案名。|  
|[GetUserEntryPoint 方法](isymunmanagedreader-getuserentrypoint-method.md)|傳回指定為模組的使用者進入點的方法（如果有的話）。|  
|[GetVariables 方法](isymunmanagedreader-getvariables-method.md)|傳回非區域變數，並指定其父系和名稱。|  
|[Initialize 方法](isymunmanagedreader-initialize-method.md)|使用這個讀取器將與其相關聯的中繼資料匯入工具介面，以及模組的檔案名，初始化符號讀取器。|  
|[ReplaceSymbolStore 方法](isymunmanagedreader-replacesymbolstore-method.md)|以差異符號存放區來取代現有的符號存放區。|  
|[UpdateSymbolStore 方法](isymunmanagedreader-updatesymbolstore-method.md)|以差異符號存放區來更新現有的符號存放區。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 介面](isymunmanagedreader2-interface.md)
