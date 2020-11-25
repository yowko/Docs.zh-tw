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
ms.openlocfilehash: e376544a9d428ce5110a7e38b92a8e830f574664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725179"
---
# <a name="diagnostics-symbol-store-interfaces"></a>診斷符號存放區介面

本主題說明的非受控介面，可讓編譯器產生可供偵錯工具使用的符號資訊。  
  
## <a name="in-this-section"></a>本節內容  

 [IBindingDisplay 介面](ibindingdisplay-interface.md)  
 提供方法來顯示有關執行中應用程式的目前系結資訊。  
  
 [IDebugAutoAttach 介面](idebugautoattach-interface.md)  
 為伺服器叫用的偵錯工具自動附加定義介面。  
  
 [INotifyConnection2 介面](inotifyconnection2-interface.md)  
 宣告註冊和取消註冊連接通知來源的方法。  
  
 [INotifySink2 介面](inotifysink2-interface.md)  
 宣告接收通知的方法。  
  
 [INotifySource2 介面](inotifysource2-interface.md)  
 宣告用來設定通知篩選準則的方法。  
  
 [ISymENCUnmanagedMethod 介面](isymencunmanagedmethod-interface.md)  
 提供 [編輯後繼續] 功能的資訊。  
  
 [ISymUnmanagedAsyncMethod 介面](isymunmanagedasyncmethod-interface.md)  
 此介面是 [ISymUnmanagedAsyncMethodPropertiesWriter 介面](isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter 介面](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 允許為每個方法符號定義選擇性的非同步方法資訊。 必須與開啟的方法搭配使用 (也就是 [OpenMethod 方法](isymunmanagedwriter-openmethod-method.md)和 [CloseMethod 方法](isymunmanagedwriter-closemethod-method.md) 的呼叫之間) 。  
  
 [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)  
 代表非受控碼的符號繫結器。  
  
 [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)  
 代表非受控碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。  
  
 [ISymUnmanagedBinder3 介面](isymunmanagedbinder3-interface.md)  
 代表非受控碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。  
  
 [ISymUnmanagedConstant 介面](isymunmanagedconstant-interface.md)  
 提供非受控常數的存取權。  
  
 [ISymUnmanagedDispose 介面](isymunmanageddispose-interface.md)  
 處置未受管理的資源。  
  
 [ISymUnmanagedDocument 介面](isymunmanageddocument-interface.md)  
 代表符號存放區所參考的文件。  
  
 [ISymUnmanagedDocumentWriter 介面](isymunmanageddocumentwriter-interface.md)  
 提供寫入至符號存放區所參考之文件的方法。  
  
 [ISymUnmanagedENCUpdate 介面](isymunmanagedencupdate-interface.md)  
 提供 [編輯後繼續] 功能的方法。  
  
 [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)  
 代表符號存放區內的方法。  
  
 [ISymUnmanagedNamespace 介面](isymunmanagednamespace-interface.md)  
 代表命名空間。  
  
 [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)  
 代表可讓您存取符號存放區內文件、方法和變數的符號讀取器。  
  
 [ISymUnmanagedReader2 介面](isymunmanagedreader2-interface.md)  
 取得符號讀取器方法，指定方法 token 和編輯和複製版本號碼。  
  
 [ISymUnmanagedReaderSymbolSearchInfo 介面](isymunmanagedreadersymbolsearchinfo-interface.md)  
 提供可取得符號搜尋資訊的方法。  
  
 [ISymUnmanagedScope 介面](isymunmanagedscope-interface.md)  
 表示方法內的語彙範圍。  
  
 [ISymUnmanagedScope2 介面](isymunmanagedscope2-interface.md)  
 代表方法內的詞彙範圍，並 `ISymUnmanagedScope` 以取得範圍內所定義之常數相關資訊的方法來擴充介面。  
  
 [ISymUnmanagedSourceServerModule 介面](isymunmanagedsourceservermodule-interface.md)  
 提供模組的來源伺服器資料。  
  
 [ISymUnmanagedSymbolSearchInfo 介面](isymunmanagedsymbolsearchinfo-interface.md)  
 提供可取得搜尋路徑相關資訊的方法。  
  
 [ISymUnmanagedVariable 介面](isymunmanagedvariable-interface.md)  
 代表變數，例如參數、區域變數或欄位。  
  
 [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)  
 表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。  
  
 [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)  
 表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。 擴充 `ISymUnmanagedWriter` 介面。  
  
 [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)  
 表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。 擴充 `ISymUnmanagedWriter` 介面。  
  
 [ISymUnmanagedWriter4 介面](isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 介面。  
  
 [ISymUnmanagedWriter5 介面](isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 介面。  
  
## <a name="related-sections"></a>相關章節  

 [診斷符號存放區列舉](diagnostics-symbol-store-enumerations.md)  
  
 [診斷符號存放區結構](diagnostics-symbol-store-structures.md)  
  
 [偵錯](../debugging/index.md)
