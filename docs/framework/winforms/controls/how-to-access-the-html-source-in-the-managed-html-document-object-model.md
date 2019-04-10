---
title: HOW TO：存取受控 HTML 文件物件模型中的 HTML 原始檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: f2306e3405aa0ff37060d987bdc82b58fbaa7784
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345556"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>HOW TO：存取受控 HTML 文件物件模型中的 HTML 原始檔
在第一次顯示目前的文件時，<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 控制項的 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 與 <xref:System.Windows.Forms.WebBrowser> 屬性會傳回其舊版的 HTML。 您若是使用方法與屬性呼叫 (例如 <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> 與 <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>) 修改頁面，這些變更將不會在您呼叫 <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 及 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 時出現。 若要取得 DOM 的最新 HTML 來源，您必須呼叫 HTML 元素的 <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> 屬性。  
  
 下列程序示範如何擷取動態來源，以及如何在個別的捷徑功能表中顯示該來源。  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>擷取具有 OuterHtml 屬性的動態來源  
  
1. 新建 Windows Forms 應用程式 開始使用單一<xref:System.Windows.Forms.Form>，並取名為`Form1`。  
  
2. 主機<xref:System.Windows.Forms.WebBrowser>控制在 Windows Forms 應用程式，並將它命名`WebBrowser1`。 如需詳細資訊，請參閱[如何：將 Web 瀏覽器功能加入至 Windows Forms 應用程式](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)。  
  
3. 建立第二個<xref:System.Windows.Forms.Form>呼叫的應用程式中`CodeForm`。  
  
4. 新增<xref:System.Windows.Forms.RichTextBox>若要控制`CodeForm`並設定其<xref:System.Windows.Forms.Control.Dock%2A>屬性設`Fill`。  
  
5. 在 建立公用屬性`CodeForm`稱為`Code`。  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6. 新增<xref:System.Windows.Forms.Button>控制項，名為`Button1`至您<xref:System.Windows.Forms.Form>，並監視<xref:System.Windows.Forms.Control.Click>事件。 如需監視事件的詳細資訊，請參閱[事件](../../../standard/events/index.md)。  
  
7. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 嘗試擷取之前，請務必先測試 <xref:System.Windows.Forms.WebBrowser.Document%2A> 的值。 在未完全載入目前的頁面之前，可能不會起始設定 <xref:System.Windows.Forms.WebBrowser.Document%2A> 或其一或多個子物件。  
  
## <a name="see-also"></a>另請參閱

- [使用 Managed HTML 文件物件模型](using-the-managed-html-document-object-model.md)
- [WebBrowser 控制項概觀](webbrowser-control-overview.md)
