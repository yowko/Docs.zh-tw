---
title: 在 Windows Forms 應用程式中建立 HTML 檔案檢視器
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732841"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>如何：在 Windows Forms 應用程式中建立 HTML 文件檢視器
您可以使用 [<xref:System.Windows.Forms.WebBrowser>] 控制項來顯示和列印 HTML 檔案，而不需提供網際網路網頁瀏覽器的完整功能。 當您想要利用 HTML 的格式設定功能，但不想讓使用者載入可能包含不受信任的 Web 控制項或潛在惡意腳本程式碼的任意網頁時，這會很有用。 您可能想要以這種方式限制 <xref:System.Windows.Forms.WebBrowser> 控制項的功能，例如，將它當做 HTML 電子郵件檢視器使用，或是在應用程式中提供 HTML 格式的說明。  
  
### <a name="to-create-an-html-document-viewer"></a>若要建立 HTML 檔案檢視器  
  
1. 將 [<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>] 屬性設定為 [`false`]，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項開啟放在其上的檔案。  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. 將 [<xref:System.Windows.Forms.WebBrowser.Url%2A>] 屬性設定為要顯示之初始檔案的位置。  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。  
  
- `System` 和 `System.Windows.Forms` 組件的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser 控制項概觀](webbrowser-control-overview.md)
- [WebBrowser 安全性](webbrowser-security.md)
- [操作說明：使用 WebBrowser 控制項巡覽至 URL](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [操作說明：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
