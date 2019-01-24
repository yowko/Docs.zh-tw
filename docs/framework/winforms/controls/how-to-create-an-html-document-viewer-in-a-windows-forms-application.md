---
title: HOW TO：建立 Windows Forms 應用程式中的 HTML 文件檢視器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 83a29af28f5e58b75377805e443eb92cee39e272
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643698"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="8308c-102">HOW TO：建立 Windows Forms 應用程式中的 HTML 文件檢視器</span><span class="sxs-lookup"><span data-stu-id="8308c-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="8308c-103">您可以使用<xref:System.Windows.Forms.WebBrowser>控制項來顯示和列印 HTML 文件，而不需提供網際網路網頁瀏覽器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="8308c-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="8308c-104">當您想要利用 HTML 格式化功能，但不是希望使用者載入任意的網頁可能包含不受信任的 Web 控制項或潛在的惡意指令碼時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="8308c-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="8308c-105">您可能想要限制的功能<xref:System.Windows.Forms.WebBrowser>以這種方式，例如，控制，使用它作為 HTML 電子郵件檢視器，或提供您的應用程式中 HTML 格式的說明。</span><span class="sxs-lookup"><span data-stu-id="8308c-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="8308c-106">若要建立 HTML 文件檢視器</span><span class="sxs-lookup"><span data-stu-id="8308c-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="8308c-107">設定<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>屬性，以`false`若要避免<xref:System.Windows.Forms.WebBrowser>控制項開啟放到它上面的檔案。</span><span class="sxs-lookup"><span data-stu-id="8308c-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="8308c-108">設定<xref:System.Windows.Forms.WebBrowser.Url%2A>屬性顯示的初始檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="8308c-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8308c-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8308c-109">Compiling the Code</span></span>  
 <span data-ttu-id="8308c-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8308c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8308c-111">名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="8308c-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="8308c-112">`System` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8308c-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8308c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8308c-113">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="8308c-114">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="8308c-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="8308c-115">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="8308c-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)
- [<span data-ttu-id="8308c-116">如何：瀏覽至 URL，以使用 WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="8308c-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="8308c-117">如何：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="8308c-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
