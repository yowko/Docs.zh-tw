---
title: "如何：在 Windows Forms 應用程式中建立 HTML 文件檢視器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58f964be53c6ddb8abf0af539b773344ce09d948
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="08184-102">如何：在 Windows Forms 應用程式中建立 HTML 文件檢視器</span><span class="sxs-lookup"><span data-stu-id="08184-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="08184-103">您可以使用<xref:System.Windows.Forms.WebBrowser>控制項以顯示和列印 HTML 文件，而不需提供網際網路網頁瀏覽器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="08184-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="08184-104">當您想要利用的 HTML 格式的功能，但不是希望使用者載入任意網頁可能包含不受信任的 Web 控制項或潛在的惡意程式碼時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="08184-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="08184-105">您可能想要限制的能力<xref:System.Windows.Forms.WebBrowser>這種方式，例如，控制，當成 HTML 電子郵件檢視器使用，或提供您的應用程式中 HTML 格式的說明。</span><span class="sxs-lookup"><span data-stu-id="08184-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="08184-106">若要建立 HTML 文件檢視器</span><span class="sxs-lookup"><span data-stu-id="08184-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="08184-107">設定<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>屬性`false`防止<xref:System.Windows.Forms.WebBrowser>控制項開啟放到它上面的檔案。</span><span class="sxs-lookup"><span data-stu-id="08184-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="08184-108">設定<xref:System.Windows.Forms.WebBrowser.Url%2A>要顯示的初始檔案位置的屬性。</span><span class="sxs-lookup"><span data-stu-id="08184-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08184-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="08184-109">Compiling the Code</span></span>  
 <span data-ttu-id="08184-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="08184-110">This example requires:</span></span>  
  
-   <span data-ttu-id="08184-111">名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="08184-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="08184-112">`System` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="08184-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08184-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="08184-113">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [<span data-ttu-id="08184-114">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="08184-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="08184-115">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="08184-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [<span data-ttu-id="08184-116">操作說明：使用 WebBrowser 控制項巡覽至 URL</span><span class="sxs-lookup"><span data-stu-id="08184-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [<span data-ttu-id="08184-117">操作說明：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="08184-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
