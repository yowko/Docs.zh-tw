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
ms.openlocfilehash: 8f0bbd26bde562df5482d167c9d2775e01426f55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610050"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 介面
表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](isymunmanagedwriter-abort-method.md)|關閉符號寫入器，而不將符號認可到符號存放區。|  
|[Close 方法](isymunmanagedwriter-close-method.md)|將符號認可到符號存放區之後，關閉符號寫入器。|  
|[CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)|關閉目前的方法。 關閉方法後，就不能在其中定義更多符號。|  
|[CloseNamespace 方法](isymunmanagedwriter-closenamespace-method.md)|關閉最近開啟的命名空間。|  
|[CloseScope 方法](isymunmanagedwriter-closescope-method.md)|關閉目前的語彙範圍。|  
|[DefineConstant 方法](isymunmanagedwriter-defineconstant-method.md)|定義常數值的名稱。|  
|[DefineDocument 方法](isymunmanagedwriter-definedocument-method.md)|定義來源文件。|  
|[DefineField 方法](isymunmanagedwriter-definefield-method.md)|定義不在方法內的單一變數。|  
|[DefineGlobalVariable 方法](isymunmanagedwriter-defineglobalvariable-method.md)|定義單一全域變數。|  
|[DefineLocalVariable 方法](isymunmanagedwriter-definelocalvariable-method.md)|在目前的語彙範圍中定義單一變數。|  
|[DefineParameter 方法](isymunmanagedwriter-defineparameter-method.md)|定義目前方法中的單一參數。|  
|[DefineSequencePoints 方法](isymunmanagedwriter-definesequencepoints-method.md)|在目前的方法內定義一組序列點。|  
|[GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md)|傳回編譯器在可移植執行檔（PE）檔案標頭中寫入 debug 目錄專案所需的資訊。|  
|[Initialize 方法](isymunmanagedwriter-initialize-method.md)|設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。|  
|[Initialize2 方法](isymunmanagedwriter-initialize2-method.md)|設定與此寫入器相關聯的中繼資料發射器介面，設定要寫入偵錯工具符號的輸出檔案名，並設定程式資料庫（PDB）檔案的最終位置。|  
|[OpenMethod 方法](isymunmanagedwriter-openmethod-method.md)|開啟用來發出符號資訊的方法。|  
|[OpenNamespace 方法](isymunmanagedwriter-opennamespace-method.md)|開啟新的命名空間。|  
|[OpenScope 方法](isymunmanagedwriter-openscope-method.md)|開啟目前方法中的新語彙範圍。|  
|[RemapToken 方法](isymunmanagedwriter-remaptoken-method.md)|通知符號寫入器，元資料標記在發出中繼資料時已重新對應。|  
|[SetMethodSourceRange 方法](isymunmanagedwriter-setmethodsourcerange-method.md)|指定原始程式檔內方法的實際開頭和結尾。|  
|[SetScopeRange 方法](isymunmanagedwriter-setscoperange-method.md)|定義指定語彙範圍的位移範圍。|  
|[SetSymAttribute 方法](isymunmanagedwriter-setsymattribute-method.md)|根據名稱定義自訂屬性。|  
|[SetUserEntryPoint 方法](isymunmanagedwriter-setuserentrypoint-method.md)|指定使用者定義的方法，這是此模組的進入點。|  
|[UsingNamespace 方法](isymunmanagedwriter-usingnamespace-method.md)|指定在目前開啟的詞法範圍內使用指定的完整命名空間名稱。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)
