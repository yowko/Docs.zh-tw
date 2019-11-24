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
Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Finds a document.|  
|[GetDocuments 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Returns an array of all the documents defined in the symbol store.|  
|[GetDocumentVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Gets the specified version of the specified document.|  
|[GetGlobalVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Returns all global variables.|  
|[GetMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Gets a symbol reader method, given a method token.|  
|[GetMethodByVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Gets a symbol reader method, given a method token and an edit-and-copy version number.|  
|[GetMethodFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Returns the method that contains the breakpoint at the given position in a document.|  
|[GetMethodsFromDocumentPosition 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Returns an array of methods, each of which contains the breakpoint at the given position in a document.|  
|[GetMethodVersion 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Gets the method version.|  
|[GetNamespaces 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Gets the namespaces defined at global scope within this symbol store.|  
|[GetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Gets a custom attribute based upon its name.|  
|[GetSymbolStoreFileName 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Provides the on-disk file name of the symbol store.|  
|[GetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Returns the method that was specified as the user entry point for the module, if any.|  
|[GetVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Return a non-local variable, given its parent and name.|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.|  
|[ReplaceSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|以差異符號存放區來取代現有的符號存放區。|  
|[UpdateSymbolStore 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|以差異符號存放區來更新現有的符號存放區。|  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
