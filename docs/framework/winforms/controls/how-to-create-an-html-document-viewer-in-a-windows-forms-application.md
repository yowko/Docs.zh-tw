---
title: 如何：在 Windows Forms 應用程式中建立 HTML 文件檢視器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 1330e20cc4fe7df86e51bebca28e4a71e3108673
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530539"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>如何：在 Windows Forms 應用程式中建立 HTML 文件檢視器
您可以使用<xref:System.Windows.Forms.WebBrowser>控制項以顯示和列印 HTML 文件，而不需提供網際網路網頁瀏覽器的完整功能。 當您想要利用的 HTML 格式的功能，但不是希望使用者載入任意網頁可能包含不受信任的 Web 控制項或潛在的惡意程式碼時，這非常有用。 您可能想要限制的能力<xref:System.Windows.Forms.WebBrowser>這種方式，例如，控制，當成 HTML 電子郵件檢視器使用，或提供您的應用程式中 HTML 格式的說明。  
  
### <a name="to-create-an-html-document-viewer"></a>若要建立 HTML 文件檢視器  
  
1.  設定<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>屬性`false`防止<xref:System.Windows.Forms.WebBrowser>控制項開啟放到它上面的檔案。  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  設定<xref:System.Windows.Forms.WebBrowser.Url%2A>要顯示的初始檔案位置的屬性。  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。  
  
-   `System` 和 `System.Windows.Forms` 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser 安全性](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [操作說明：使用 WebBrowser 控制項巡覽至 URL](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [操作說明：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
