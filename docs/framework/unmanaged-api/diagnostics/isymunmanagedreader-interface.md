---
title: "ISymUnmanagedReader 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader 介面
代表符號讀取器可存取文件、 方法和符號存放區內的變數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|尋找文件。|  
|[GetDocuments 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|傳回定義在符號存放區中的所有文件的陣列。|  
|[GetDocumentVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|取得指定的文件指定的版本。|  
|[GetGlobalVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|傳回所有的全域變數。|  
|[GetMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|取得符號讀取器方法，指定方法語彙基元。|  
|[GetMethodByVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|取得符號讀取器方法，指定方法語彙基元和編輯複製版本號碼。|  
|[GetMethodFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|傳回包含中斷點的文件中指定位置的方法。|  
|[GetMethodsFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|傳回的陣列的方法，其中每個包含文件中指定位置的中斷點。|  
|[GetMethodVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|取得方法的版本。|  
|[GetNamespaces 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|取得在這個符號存放區內的全域範圍定義的命名空間。|  
|[GetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|取得其名稱為基礎的自訂屬性。|  
|[GetSymbolStoreFileName 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|提供符號存放區的磁碟上檔案名稱。|  
|[GetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|傳回指定為模組的使用者進入點方法，如果有的話。|  
|[GetVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|傳回非本機變數，指定其父系和名稱。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|初始化這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面的符號讀取器。|  
|[ReplaceSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|以差異符號存放區來取代現有的符號存放區。|  
|[UpdateSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|以差異符號存放區來更新現有的符號存放區。|  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
