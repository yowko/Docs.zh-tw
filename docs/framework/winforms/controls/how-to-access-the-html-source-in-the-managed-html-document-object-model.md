---
title: "如何：存取 Managed HTML 文件物件模型中的 HTML 原始檔"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ef9839029e1c60cbc0d713e8982baa5708a281f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>如何：存取 Managed HTML 文件物件模型中的 HTML 原始檔
在第一次顯示目前的文件時，<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 控制項的 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 與 <xref:System.Windows.Forms.WebBrowser> 屬性會傳回其舊版的 HTML。 您若是使用方法與屬性呼叫 (例如 <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> 與 <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>) 修改頁面，這些變更將不會在您呼叫 <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 及 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 時出現。 若要取得 DOM 的最新 HTML 來源，您必須呼叫 HTML 元素的 <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> 屬性。  
  
 下列程序示範如何擷取動態來源，以及如何在個別的捷徑功能表中顯示該來源。  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>擷取具有 OuterHtml 屬性的動態來源  
  
1.  新建 Windows Forms 應用程式 啟動與單一<xref:System.Windows.Forms.Form>，並呼叫它`Form1`。  
  
2.  主機<xref:System.Windows.Forms.WebBrowser>控制在您的 Windows Form 應用程式，並將其命名`WebBrowser1`。 如需詳細資訊，請參閱[如何： 加入 Web 瀏覽器功能加入 Windows Form 應用程式](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)。  
  
3.  建立第二個<xref:System.Windows.Forms.Form>呼叫的應用程式中`CodeForm`。  
  
4.  新增<xref:System.Windows.Forms.RichTextBox>控制權傳輸至`CodeForm`並設定其<xref:System.Windows.Forms.Control.Dock%2A>屬性`Fill`。  
  
5.  建立的公用屬性上`CodeForm`呼叫`Code`。  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  新增<xref:System.Windows.Forms.Button>控制項，名為`Button1`到您<xref:System.Windows.Forms.Form>，並監視<xref:System.Windows.Forms.Control.Click>事件。 如需監視事件的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)。  
  
7.  將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 嘗試擷取之前，請務必先測試 <xref:System.Windows.Forms.WebBrowser.Document%2A> 的值。 在未完全載入目前的頁面之前，可能不會起始設定 <xref:System.Windows.Forms.WebBrowser.Document%2A> 或其一或多個子物件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Managed HTML 文件物件模型](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
