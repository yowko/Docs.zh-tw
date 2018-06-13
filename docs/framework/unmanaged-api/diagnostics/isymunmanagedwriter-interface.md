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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86aa8d3d23d82d51cfe4e6ce6b15b554704ad41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435468"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 介面
代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|關閉不符號認可到符號存放區的符號寫入器。|  
|[Close 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|關閉後認可到符號存放區的符號的符號寫入器。|  
|[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|關閉目前的方法。 一旦關閉方法，可以不定義任何符號，於其中。|  
|[CloseNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|關閉最近開啟的命名空間。|  
|[CloseScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|關閉目前的語彙範圍。|  
|[DefineConstant 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|定義常數值的名稱。|  
|[DefineDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|定義來源文件。|  
|[DefineField 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|定義單一變數不是在方法中。|  
|[DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|定義單一的全域變數。|  
|[DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|在目前的語彙範圍中定義單一變數。|  
|[DefineParameter 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|定義目前方法中的單一參數。|  
|[DefineSequencePoints 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|在目前的方法內定義一組序列點。|  
|[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|傳回編譯器在可攜式執行檔 (PE) 標頭寫入偵錯目錄項目所需的資訊。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|設定與這個寫入器將會在相關的中繼資料發出器介面，並將偵錯符號寫入的輸出檔名稱。|  
|[Initialize2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|設定與此寫入器將相關聯的中繼資料發出器介面，設定要偵錯符號都會寫入，且設定的程式資料庫 (PDB) 檔的最後一個位置的輸出檔案名稱。|  
|[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|開啟的符號資訊就會發出的方法。|  
|[OpenNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|開啟新的命名空間。|  
|[OpenScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|開啟目前方法中的新語彙範圍。|  
|[RemapToken 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|通知中繼資料語彙基元已重新對應，因為中繼資料已發出符號寫入器。|  
|[SetMethodSourceRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|指定的則為 true 的開始和結束的原始程式檔內的方法。|  
|[SetScopeRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|定義指定語彙範圍的位移範圍。|  
|[SetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|定義自訂屬性，根據它的名稱。|  
|[SetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|指定的使用者定義的方法，是針對此模組的進入點。|  
|[UsingNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|指定確認目前開啟的語彙範圍內使用指定的完整命名空間名稱。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
