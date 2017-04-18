---
title: "如何：在 Windows Form 應用程式中建立 HTML 文件檢視器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "文件檢視器"
  - "WebBrowser 控制項 [Windows Form], 建立 HTML 文件檢視器"
  - "Windows Form, 建立文件檢視器"
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：在 Windows Form 應用程式中建立 HTML 文件檢視器
您可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項來顯示和列印 HTML 文件，而不需要提供網際網路 Web 瀏覽器的完整功能。  當您想要充分利用 HTML 的格式化能力，但是不想要使用者載入任意的 Web 網頁 \(可能包含不受信任的 Web 控制項或疑似惡意的指令碼\) 時，這項功能就很有用。  您可能想要用這種方式來限制 <xref:System.Windows.Forms.WebBrowser> 控制項的功能，例如做為 HTML 電子郵件檢視器，或是在應用程式中提供 HTML 格式的說明。  
  
### 建立 HTML 文件檢視器  
  
1.  將 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> 屬性設定為 `false`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項開啟放在控制項上的檔案。  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  將 <xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性設定為所要顯示之初始檔案的位置。  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。  
  
-   `System` 和 `System.Windows.Forms` 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>   
 <xref:System.Windows.Forms.WebBrowser.Url%2A>   
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [WebBrowser 安全性](../../../../docs/framework/winforms/controls/webbrowser-security.md)   
 [如何：使用 WebBrowser 控制項巡覽至 URL](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [如何：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)