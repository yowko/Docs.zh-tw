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
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448533"
---
# <a name="diagnostics-symbol-store-interfaces"></a>診斷符號存放區介面
本主題描述可讓編譯器產生可供偵錯工具使用之符號資訊的非受控介面。  
  
## <a name="in-this-section"></a>本節內容  
 [IBindingDisplay 介面](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 提供方法，顯示有關執行中應用程式的目前系結資訊。  
  
 [IDebugAutoAttach 介面](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 定義伺服器叫用的偵錯工具自動附加的介面。  
  
 [INotifyConnection2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 宣告註冊和取消註冊連接通知來源的方法。  
  
 [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 宣告接收器通知的方法。  
  
 [INotifySource2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 宣告用於設定通知篩選準則的方法。  
  
 [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 提供 [編輯後繼續] 功能的資訊。  
  
 [ISymUnmanagedAsyncMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 針對每個方法符號，允許定義選擇性的非同步方法資訊。 必須搭配已開啟的方法使用（也就是在呼叫[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)之間）。  
  
 [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 表示非受控程式碼的符號系結器。  
  
 [ISymUnmanagedBinder2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。  
  
 [ISymUnmanagedBinder3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。  
  
 [ISymUnmanagedConstant 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 提供非受控常數的存取權。  
  
 [ISymUnmanagedDispose 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 處置非受控資源。  
  
 [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 代表符號存放區所參考的文件。  
  
 [ISymUnmanagedDocumentWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 提供寫入至符號存放區所參考之文件的方法。  
  
 [ISymUnmanagedENCUpdate 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 提供編輯後繼續功能的方法。  
  
 [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 表示符號存放區中的方法。  
  
 [ISymUnmanagedNamespace 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 代表命名空間。  
  
 [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。  
  
 [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 取得指定方法 token 和編輯和複製版本號碼的符號讀取器方法。  
  
 [ISymUnmanagedReaderSymbolSearchInfo 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 提供取得符號搜尋資訊的方法。  
  
 [ISymUnmanagedScope 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 表示方法內的詞法範圍。  
  
 [ISymUnmanagedScope2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 表示方法內的詞法範圍，並使用可取得範圍內所定義常數相關資訊的方法來擴充 `ISymUnmanagedScope` 介面。  
  
 [ISymUnmanagedSourceServerModule 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 提供模組的來源伺服器資料。  
  
 [ISymUnmanagedSymbolSearchInfo 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 提供取得搜尋路徑相關資訊的方法。  
  
 [ISymUnmanagedVariable 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 表示變數，例如參數、本機變數或欄位。  
  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。  
  
 [ISymUnmanagedWriter2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。 擴充 `ISymUnmanagedWriter` 介面。  
  
 [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。 擴充 `ISymUnmanagedWriter` 介面。  
  
 [ISymUnmanagedWriter4 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 介面。  
  
 [ISymUnmanagedWriter5 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 介面。  
  
## <a name="related-sections"></a>相關章節  
 [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
