---
title: "如何：存取 Managed HTML 文件物件模型中的 HTML 原始檔 | Microsoft Docs"
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
  - "HTML, 在 Windows Form 中存取"
  - "Managed HTML DOM"
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：存取 Managed HTML 文件物件模型中的 HTML 原始檔
在第一次顯示目前的文件時，<xref:System.Windows.Forms.WebBrowser> 控制項的 <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 與 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性會傳回其舊版的 HTML。  您若是使用方法與屬性呼叫 \(例如 <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> 與 <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>\) 修改頁面，這些變更將不會在您呼叫 <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 及 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 時出現。  若要取得 DOM 的最新 HTML 來源，您必須呼叫 HTML 元素的 <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> 屬性。  
  
 下列程序示範如何擷取動態來源，以及如何在個別的捷徑功能表中顯示該來源。  
  
### 擷取具有 OuterHtml 屬性的動態來源  
  
1.  新建 Windows Forms 應用程式  先建立第一個 <xref:System.Windows.Forms.Form>，並將其命名為 `Form1`。  
  
2.  在您的 Windows Forms 應用程式上執行 <xref:System.Windows.Forms.WebBrowser> 控制項，並將其命名為 `WebBrowser1`。  如需詳細資訊，請參閱[如何：將 Web 瀏覽器功能加入至 Windows Form 應用程式](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)。  
  
3.  在應用程式中建立第二個 <xref:System.Windows.Forms.Form>，並將其命名為 `CodeForm`。  
  
4.  將 <xref:System.Windows.Forms.RichTextBox> 控制項加入 `CodeForm`，並將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 `Fill`。  
  
5.  建立 `CodeForm` 的公用屬性，並命名為 `Code`。  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  將名稱為 `Button1` 的 <xref:System.Windows.Forms.Button> 控制項加入您的 <xref:System.Windows.Forms.Form>，並監視 <xref:System.Windows.Forms.Control.Click> 事件。  如需監視事件的詳細資料，請參閱 [事件](../../../../docs/standard/events/index.md)。  
  
7.  將下列程式碼加入 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## 穩固程式設計  
 嘗試擷取之前，請務必先測試 <xref:System.Windows.Forms.WebBrowser.Document%2A> 的值。  在未完全載入目前的頁面之前，可能不會起始設定 <xref:System.Windows.Forms.WebBrowser.Document%2A> 或其一或多個子物件。  
  
## 請參閱  
 [使用 Managed HTML 文件物件模型](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)   
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)