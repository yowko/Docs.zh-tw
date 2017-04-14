---
title: "WebBrowser 控制項概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WebBrowser"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Web 網頁, 在應用程式中顯示"
  - "WebBrowser 控制項 [Windows Form], 關於"
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# WebBrowser 控制項概觀
<xref:System.Windows.Forms.WebBrowser> 控制項提供 WebBrowser ActiveX 控制項的 Managed 包裝函式。  Managed 包裝函式可以讓您在 Windows Form 用戶端應用程式中顯示 Web 網頁。  您可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項在應用程式中複製 Internet Explorer Web 瀏覽功能，或停用預設 Internet Explorer 功能並將控制項做為簡易的 HTML 文件檢視器。  您也可以使用此控制項，將 DHTML 使用者介面項目加入至表單，並隱藏項目實際上是裝載在 <xref:System.Windows.Forms.WebBrowser> 控制項中的事實。  這項處理方法讓您完美地將 Web 控制項和 Windows Form 控制項結合到單一的應用程式中。  
  
## 常用的屬性、方法和事件  
 <xref:System.Windows.Forms.WebBrowser> 控制項有數個屬性、方法和事件，可用來實作 Internet Explorer 的控制項。  例如，您可以使用 `Navigate` 方法來實作網址列，使用 `GoBack`、`GoForward`、`Stop` 和 `Refresh` 方法來實作工具列上的巡覽按鈕。  可以處理 `Navigated` 事件，使用 `Url` 屬性的值來更新網址列，使用 `DocumentTitle` 屬性的值來更新標題列。  
  
 如果您想要在應用程式中產生自己的網頁內容，可以設定 `DocumentText` 屬性。  如果您熟悉 HTML 文件物件模型 \(DOM\)，也可以透過 `Document` 屬性來處理目前的 Web 網頁內容。  您可以使用這個屬性來儲存和修改記憶體中的文件，而不必在檔案之間巡覽。  
  
 `Document` 屬性也讓您從用戶端應用程式程式碼呼叫在 Web 網頁指令碼中實作的方法。  若要從指令碼存取用戶端應用程式，請設定 `ObjectForScripting` 屬性。  指令碼可以將您指定的物件當做 `window.external` 物件來存取。  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性|取得物件，以對目前 Web 網頁的 HTML 文件物件模型 \(DOM\) 提供 Managed 存取。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件|當 Web 網頁結束載入時發生。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性|取得或設定目前 Web 網頁的 HTML 內容。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 屬性|取得目前 Web 網頁的標題。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|巡覽至記錄中的上一頁。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|巡覽至記錄的下一頁。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|巡覽至指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> 事件|在巡覽開始之前發生，讓動作可以取消。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性|取得或設定物件，Web 網頁指令碼可以用來與應用程式通訊。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|列印目前的 Web 網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重新載入目前的 Web 網頁。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|中止目前的巡覽，並停止動態網頁項目 \(例如音效和動畫\)。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性|取得或設定目前 Web 網頁的 URL。  設定這個屬性，會將控制項巡覽至新的 URL。|  
  
## 請參閱  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>   
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>   
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>   
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>   
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>   
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserReadyState>   
 <xref:System.Windows.Forms.WebBrowserRefreshOption>   
 [如何：使用 WebBrowser 控制項巡覽至 URL](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [如何：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)   
 [如何：將 Web 瀏覽器功能加入至 Windows Form 應用程式](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)   
 [如何：在 Windows Form 應用程式中建立 HTML 文件檢視器](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)   
 [如何：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)   
 [WebBrowser 安全性](../../../../docs/framework/winforms/controls/webbrowser-security.md)