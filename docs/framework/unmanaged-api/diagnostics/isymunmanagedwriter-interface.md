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
ms.openlocfilehash: fddfd2a163f6e6513b648ee0b724c0b5bd54c81a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722930"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 介面

表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](isymunmanagedwriter-abort-method.md)|關閉符號寫入器，而不將符號認可到符號存放區。|  
|[Close 方法](isymunmanagedwriter-close-method.md)|將符號認可到符號存放區之後，關閉符號寫入器。|  
|[CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)|關閉目前的方法。 關閉方法之後，就無法在其中定義任何符號。|  
|[CloseNamespace 方法](isymunmanagedwriter-closenamespace-method.md)|關閉最近開啟的命名空間。|  
|[CloseScope 方法](isymunmanagedwriter-closescope-method.md)|關閉目前的語彙範圍。|  
|[DefineConstant 方法](isymunmanagedwriter-defineconstant-method.md)|定義常數值的名稱。|  
|[DefineDocument 方法](isymunmanagedwriter-definedocument-method.md)|定義來源文件。|  
|[DefineField 方法](isymunmanagedwriter-definefield-method.md)|定義不在方法內的單一變數。|  
|[DefineGlobalVariable 方法](isymunmanagedwriter-defineglobalvariable-method.md)|定義單一全域變數。|  
|[DefineLocalVariable 方法](isymunmanagedwriter-definelocalvariable-method.md)|在目前的語彙範圍中定義單一變數。|  
|[DefineParameter 方法](isymunmanagedwriter-defineparameter-method.md)|定義目前方法中的單一參數。|  
|[DefineSequencePoints 方法](isymunmanagedwriter-definesequencepoints-method.md)|在目前的方法內定義一組序列點。|  
|[GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md)|傳回編譯器在可攜式可執行檔 (PE) 檔標頭中寫入 debug directory 專案所需的資訊。|  
|[Initialize 方法](isymunmanagedwriter-initialize-method.md)|設定與這個寫入器相關聯的中繼資料發射器介面，並設定將用來寫入偵錯工具符號的輸出檔名稱。|  
|[Initialize2 方法](isymunmanagedwriter-initialize2-method.md)|設定與這個寫入器相關聯的中繼資料發射器介面、設定要寫入偵錯工具符號的輸出檔名稱，以及將程式資料庫的最終位置設定 (PDB) 檔。|  
|[OpenMethod 方法](isymunmanagedwriter-openmethod-method.md)|開啟用來發出符號資訊的方法。|  
|[OpenNamespace 方法](isymunmanagedwriter-opennamespace-method.md)|開啟新的命名空間。|  
|[OpenScope 方法](isymunmanagedwriter-openscope-method.md)|開啟目前方法中的新語彙範圍。|  
|[RemapToken 方法](isymunmanagedwriter-remaptoken-method.md)|通知符號寫入器，元資料標記已在發出中繼資料時重新對應。|  
|[SetMethodSourceRange 方法](isymunmanagedwriter-setmethodsourcerange-method.md)|指定原始程式檔內方法的實際開頭和結尾。|  
|[SetScopeRange 方法](isymunmanagedwriter-setscoperange-method.md)|定義指定語彙範圍的位移範圍。|  
|[SetSymAttribute 方法](isymunmanagedwriter-setsymattribute-method.md)|根據名稱定義自訂屬性。|  
|[SetUserEntryPoint 方法](isymunmanagedwriter-setuserentrypoint-method.md)|指定使用者定義的方法，此為此模組的進入點。|  
|[UsingNamespace 方法](isymunmanagedwriter-usingnamespace-method.md)|指定在目前開啟的詞彙範圍內使用指定的完整命名空間名稱。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)
