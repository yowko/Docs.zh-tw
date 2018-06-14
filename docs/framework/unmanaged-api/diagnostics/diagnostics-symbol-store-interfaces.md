---
title: 診斷符號存放區介面
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435808"
---
# <a name="diagnostics-symbol-store-interfaces"></a>診斷符號存放區介面
本主題描述 unmanaged 的介面，可讓編譯器產生供偵錯工具符號資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [IBindingDisplay 介面](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 提供方法，顯示執行中應用程式的目前繫結資訊。  
  
 [IDebugAutoAttach 介面](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 定義介面，伺服器叫用偵錯工具自動附加。  
  
 [INotifyConnection2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 宣告方法註冊及取消註冊連接的通知來源。  
  
 [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 宣告接收通知的方法。  
  
 [INotifySource2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 宣告設定通知篩選器的方法。  
  
 [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 提供 [編輯後繼續] 功能的資訊。  
  
 [ISymUnmanagedAsyncMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 這個介面是讀取補數[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)。  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 可讓選擇性的非同步方法資訊方法符號的定義。 必須使用開啟的方法 (也就是呼叫之間[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md))。  
  
 [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 表示 unmanaged 程式碼的符號繫結器。  
  
 [ISymUnmanagedBinder2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。  
  
 [ISymUnmanagedBinder3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。  
  
 [ISymUnmanagedConstant 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 存取未受管理的常數。  
  
 [ISymUnmanagedDispose 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 處置 unmanaged 資源。  
  
 [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 代表符號存放區所參考的文件。  
  
 [ISymUnmanagedDocumentWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 提供寫入至符號存放區所參考之文件的方法。  
  
 [ISymUnmanagedENCUpdate 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 提供方法讓 [編輯後繼續] 功能。  
  
 [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 代表符號存放區內的方法。  
  
 [ISymUnmanagedNamespace 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 代表命名空間。  
  
 [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 代表符號讀取器可存取文件、 方法和符號存放區內的變數。  
  
 [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 取得符號讀取器方法，指定方法語彙基元和編輯複製版本號碼。  
  
 [ISymUnmanagedReaderSymbolSearchInfo 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 提供方法，以取得符號搜尋資訊。  
  
 [ISymUnmanagedScope 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 表示在方法內的語彙範圍。  
  
 [ISymUnmanagedScope2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 代表語彙範圍內的方法，並擴充`ISymUnmanagedScope`介面與方法，以取得範圍內定義的常數的相關資訊...  
  
 [ISymUnmanagedSourceServerModule 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 提供模組中的來源伺服器資料。  
  
 [ISymUnmanagedSymbolSearchInfo 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 提供方法，以取得搜尋路徑的相關資訊。  
  
 [ISymUnmanagedVariable 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 表示變數，例如參數、 區域變數或欄位。  
  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。  
  
 [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。 擴充`ISymUnmanagedWriter`介面。  
  
 [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。 擴充`ISymUnmanagedWriter`介面。  
  
 [ISymUnmanagedWriter4 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 介面。  
  
 [ISymUnmanagedWriter5 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 介面。  
  
## <a name="related-sections"></a>相關章節  
 [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
