---
title: "Debugging Your Visual Basic Application | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "debugging [Visual Basic], common tasks"
ms.assetid: 904760b8-9fe9-42a7-9d65-d93774253219
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Debugging Your Visual Basic Application
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

本頁面提供 [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)] 內建之偵錯功能的文件連結。  例如，您可以在偵錯工具中觀察應用程式的執行階段行為，尋找應用程式的語意錯誤。  
  
 您可以使用偵錯工具，檢查應用程式中的變數內容，而不需插入額外的呼叫以輸出值。  同樣地，可以在程式碼中插入中斷點，在指定的地方暫止執行。  
  
## 控制執行  
 下表會列出與執行控制有關的偵錯工作，並提供各個關聯的說明網頁的連結。  
  
|||  
|-|-|  
|若要|請參閱|  
|開始偵錯 Visual Studio 專案、附加至處理序、中斷程式碼、逐步執行程式碼、執行至游標處、執行至呼叫堆疊上的函式、設定下一個陳述式、逐步執行 Just My Code、停止偵錯、重新開始偵錯，或與偵錯處理序中斷連結。|[使用偵錯工具巡覽程式碼](/visual-studio/debugger/navigating-through-code-with-the-debugger)|  
|指定程式之發行版本和偵錯版本的組態。|[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)|  
|設定開始選項 \(命令列引數、工作目錄、遠端機器\)。|[NIB: How to: Set Start Options for Application Debugging](http://msdn.microsoft.com/zh-tw/ce792058-7bac-4dd6-858b-466e872687b8)|  
|在執行階段偵錯。|[逐步解說：在設計階段進行偵錯](../Topic/Walkthrough:%20Debugging%20at%20Design%20Time.md)|  
|啟用 Just\-in\-Time 偵錯，這項功能可在 Visual Studio 外執行的程式發生嚴重錯誤時，啟動 Visual Studio 偵錯工具。|[Just\-In\-Time 偵錯](/visual-studio/debugger/just-in-time-debugging-in-visual-studio)|  
|設定原始程式行、組譯碼指令和呼叫堆疊函式的中斷點。  指定條件、叫用次數和執行位置。|[使用中斷點](/visual-studio/debugger/using-breakpoints)|  
  
## 例外狀況處理  
 下表會列出與例外狀況處理有關的偵錯工作，並指出各個關聯的說明網頁。  
  
|||  
|-|-|  
|若要|請參閱|  
|在發生未處理的例外狀況時中斷。|[如何：發生使用者未處理的例外狀況時中斷](../Topic/How%20to:%20Break%20on%20User-Unhandled%20Exceptions.md)|  
|在擲回例外狀況時中斷。|[如何：當擲回例外狀況時中斷](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|在第一個可能發生的例外狀況時中斷。|[如何：當擲回例外狀況時中斷](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|使用例外狀況助理。|[How to: Correct Run\-Time Errors with the Exception Assistant](../Topic/How%20to:%20Correct%20Run-Time%20Errors%20with%20the%20Exception%20Assistant.md)|  
|加入新的例外狀況。|[如何：加入新例外狀況](../Topic/How%20to:%20Add%20New%20Exceptions.md)|  
|在擲回例外狀況之後繼續執行。|[例外狀況之後繼續執行](/visual-studio/debugger/continuing-execution-after-an-exception)|  
  
## 編輯後繼續  
 下表會列出與 \[編輯後繼續\] 有關的偵錯工作，並指出各個關聯的說明網頁。  
  
|||  
|-|-|  
|若要|請參閱|  
|關閉和開啟 \[編輯後繼續\]。|[如何：啟用和停用編輯後繼續](../Topic/How%20to:%20Enable%20and%20Disable%20Edit%20and%20Continue.md)|  
|停止 \[編輯後繼續\] 套用程式碼變更。|[如何：停止程式碼變更](../Topic/How%20to:%20Stop%20Code%20Changes.md)|  
|在中斷模式套用編輯。|[如何：以編輯後繼續在中斷模式套用編輯](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)|  
  
## 檢查偵錯資料  
 下表會列出與檢視偵錯資料有關的偵錯工作，並指出各個關聯的說明網頁。  
  
|||  
|-|-|  
|若要|請參閱|  
|使用 \[**暫存器**\] 視窗顯示暫存器內容。|[如何：使用暫存器視窗](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)|  
|使用 \[**呼叫堆疊**\] 視窗檢視目前在堆疊上的函式或程序呼叫。|[如何：使用呼叫堆疊視窗](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)|  
|使用 \[**反組譯碼**\] 視窗檢視對應到編譯器所建立之指令的組譯程式碼。|[如何：使用反組譯碼視窗](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md)|  
|使用 \[**模組**\] 視窗列出和描述程式所使用的模組。|[如何：使用模組視窗](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)|  
|使用 \[**指令碼總管**\] 視窗列出目前載入到程式中的指令碼檔。|[如何：檢視指令碼文件](../Topic/How%20to:%20View%20Script%20Documents.md)|  
|使用 \[**執行緒**\] 視窗檢查和控制程式中的執行緒。|[如何：使用執行緒視窗](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)|  
  
## 請參閱  
 [逐步解說：偵錯 Windows Form](../Topic/Walkthrough:%20Debugging%20a%20Windows%20Form.md)   
 [偵錯 Managed 程式碼](/visual-studio/debugger/debugging-managed-code)   
 [偵錯機器碼](/visual-studio/debugger/debugging-native-code)   
 [偵錯 Web 應用程式和指令碼](/visual-studio/debugger/debugging-web-applications-and-script)   
 [偵錯使用者介面參考](/visual-studio/debugger/debugging-user-interface-reference)   
 [偵錯設定和準備](/visual-studio/debugger/debugger-settings-and-preparation)   
 [偵錯工具基礎](/visual-studio/debugger/debugger-basics)   
 [使用偵錯工具巡覽程式碼](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [使用 IntelliTrace](/visual-studio/debugger/intellitrace)   
 [C\#、F\# 和 Visual Basic 專案類型](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [如何：以編輯後繼續在中斷模式套用編輯](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)