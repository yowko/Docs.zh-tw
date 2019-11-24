---
title: ISymUnmanagedWriter 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427932"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 介面
Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Closes the symbol writer without committing the symbols to the symbol store.|  
|[Close 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Closes the symbol writer after committing the symbols to the symbol store.|  
|[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|關閉目前的方法。 Once a method is closed, no more symbols can be defined within it.|  
|[CloseNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Closes the most recently opened namespace.|  
|[CloseScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|關閉目前的語彙範圍。|  
|[DefineConstant 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Defines a name for a constant value.|  
|[DefineDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|定義來源文件。|  
|[DefineField 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Defines a single variable that is not within a method.|  
|[DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Defines a single global variable.|  
|[DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|在目前的語彙範圍中定義單一變數。|  
|[DefineParameter 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Defines a single parameter in the current method.|  
|[DefineSequencePoints 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|在目前的方法內定義一組序列點。|  
|[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.|  
|[Initialize2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.|  
|[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Opens a method into which symbol information is emitted.|  
|[OpenNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|開啟新的命名空間。|  
|[OpenScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|開啟目前方法中的新語彙範圍。|  
|[RemapToken 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.|  
|[SetMethodSourceRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Specifies the true start and end of a method within a source file.|  
|[SetScopeRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|定義指定語彙範圍的位移範圍。|  
|[SetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Defines a custom attribute based upon its name.|  
|[SetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Specifies the user-defined method that is the entry point for this module.|  
|[UsingNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.|  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
