---
title: 存取 Managed HTML 文件物件模型中的框架
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: b1a858e88ff27de19e2ebbd69c14060813873c13
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308483"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a><span data-ttu-id="ff369-102">存取 Managed HTML 文件物件模型中的框架</span><span class="sxs-lookup"><span data-stu-id="ff369-102">Accessing Frames in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="ff369-103">某些 HTML 文件包含*框架*，或可以保存自己的相異 HTML 文件的 windows。</span><span class="sxs-lookup"><span data-stu-id="ff369-103">Some HTML documents are composed out of *frames*, or windows that can hold their own distinct HTML documents.</span></span> <span data-ttu-id="ff369-104">使用框架可讓您輕鬆地建立 HTML 網頁，該 HTML 網頁的其中一個或多個頁面片段維持靜態，例如導覽列，而其他框架則不斷變更其內容。</span><span class="sxs-lookup"><span data-stu-id="ff369-104">Using frames makes it easy to create HTML pages in which one or more pieces of the page remain static, such as a navigation bar, while other frames constantly change their content.</span></span>  
  
 <span data-ttu-id="ff369-105">HTML 作者可以用兩種方法之一來建立框架：</span><span class="sxs-lookup"><span data-stu-id="ff369-105">HTML authors can create frames in one of two ways:</span></span>  
  
-   <span data-ttu-id="ff369-106">使用 `FRAMESET` 和 `FRAME` 標記，這會建立固定的視窗。</span><span class="sxs-lookup"><span data-stu-id="ff369-106">Using the `FRAMESET` and `FRAME` tags, which create fixed windows.</span></span>  
  
 <span data-ttu-id="ff369-107">-或-</span><span class="sxs-lookup"><span data-stu-id="ff369-107">-or-</span></span>  
  
-   <span data-ttu-id="ff369-108">使用 `IFRAME` 標記，這會建立可以在執行階段中重新定位的浮動視窗。</span><span class="sxs-lookup"><span data-stu-id="ff369-108">Using the `IFRAME` tag, which creates a floating window that can be repositioned at run time.</span></span>  
  
1.  <span data-ttu-id="ff369-109">因為框架包含 HTML 文件，它們會在文件物件模型 (DOM) 中顯示為視窗項目和框架項目。</span><span class="sxs-lookup"><span data-stu-id="ff369-109">Because frames contain HTML documents, they are represented in the Document Object Model (DOM) as both window elements and frame elements.</span></span>  
  
2.  <span data-ttu-id="ff369-110">當您使用 <xref:System.Windows.Forms.HtmlWindow> 的框架集合存取 `FRAME` 或 `IFRAME` 標記時，您會擷取對應至框架的視窗項目。</span><span class="sxs-lookup"><span data-stu-id="ff369-110">When you access a `FRAME` or `IFRAME` tag by using the Frames collection of <xref:System.Windows.Forms.HtmlWindow>, you are retrieving the window element corresponding to the frame.</span></span> <span data-ttu-id="ff369-111">這代表框架的所有動態屬性，例如其目前的 URL、文件及大小。</span><span class="sxs-lookup"><span data-stu-id="ff369-111">This represents all of the frame's dynamic properties, such as its current URL, document, and size.</span></span>  
  
3.  <span data-ttu-id="ff369-112">當您使用 <xref:System.Windows.Forms.HtmlWindow> 的 <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> 屬性、<xref:System.Windows.Forms.HtmlElement.Children%2A> 集合，或例如 <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> 或 <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> 等方法存取 `FRAME` 或 `IFRAME` 標記時，您會擷取框架項目。</span><span class="sxs-lookup"><span data-stu-id="ff369-112">When you access a `FRAME` or `IFRAME` tag by using the <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> property of <xref:System.Windows.Forms.HtmlWindow>, the <xref:System.Windows.Forms.HtmlElement.Children%2A> collection, or methods such as <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> or <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, you are retrieving the frame element.</span></span> <span data-ttu-id="ff369-113">這代表框架的靜態屬性，包括在原始 HTML 檔案中指定的 URL。</span><span class="sxs-lookup"><span data-stu-id="ff369-113">This represents the static properties of the frame, including the URL specified in the original HTML file.</span></span>  
  
## <a name="frames-and-security"></a><span data-ttu-id="ff369-114">框架和安全性</span><span class="sxs-lookup"><span data-stu-id="ff369-114">Frames and Security</span></span>  
 <span data-ttu-id="ff369-115">框架的存取之所以複雜，managed 的 HTML DOM 實作稱為安全性量值的事實*跨框架指令碼安全性*。</span><span class="sxs-lookup"><span data-stu-id="ff369-115">Access to frames is complicated by the fact that the managed HTML DOM implements a security measure known as *cross-frame scripting security*.</span></span> <span data-ttu-id="ff369-116">如果文件包含 `FRAMESET` 與不同網域中的兩個或更多 `FRAME`，這些 `FRAME` 無法彼此互動。</span><span class="sxs-lookup"><span data-stu-id="ff369-116">If a document contains a `FRAMESET` with two or more `FRAME`s in different domains, these `FRAME`s cannot interact with one another.</span></span> <span data-ttu-id="ff369-117">亦即`FRAME`顯示內容，從您的網站無法存取中的資訊`FRAME`這類裝載協力廠商網站`http://www.adatum.com/`。</span><span class="sxs-lookup"><span data-stu-id="ff369-117">In other words, a `FRAME` that displays content from your Web site cannot access information in a `FRAME` that hosts a third-party site such as `http://www.adatum.com/`.</span></span> <span data-ttu-id="ff369-118">此安全性實作是屬於 <xref:System.Windows.Forms.HtmlWindow> 類別的層級。</span><span class="sxs-lookup"><span data-stu-id="ff369-118">This security is implemented at the level of the <xref:System.Windows.Forms.HtmlWindow> class.</span></span> <span data-ttu-id="ff369-119">您可以取得關於裝載另一個網站之 `FRAME` 的一般資訊，例如它的 URL，但您將無法存取其 <xref:System.Windows.Forms.HtmlWindow.Document%2A> 或變更其裝載 `FRAME` 或 `IFRAME` 的大小或位置。</span><span class="sxs-lookup"><span data-stu-id="ff369-119">You can obtain general information about a `FRAME` hosting another Web site, such as its URL, but you will be unable to access its <xref:System.Windows.Forms.HtmlWindow.Document%2A> or change the size or location of its hosting `FRAME` or `IFRAME`.</span></span>  
  
 <span data-ttu-id="ff369-120">此規則也適用於以 <xref:System.Windows.Forms.HtmlWindow.Open%2A> 和 <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> 方法開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="ff369-120">This rule also applies to windows that you open using the <xref:System.Windows.Forms.HtmlWindow.Open%2A> and <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> methods.</span></span> <span data-ttu-id="ff369-121">如果您開啟的視窗位於與 <xref:System.Windows.Forms.WebBrowser> 控制項中裝載頁面不同的網域，則您將無法移動該視窗，或檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="ff369-121">If the window you open is in a different domain from the page hosted in the <xref:System.Windows.Forms.WebBrowser> control, you will not be able to move that window or examine its contents.</span></span> <span data-ttu-id="ff369-122">如果您使用 <xref:System.Windows.Forms.WebBrowser> 控制項來顯示與用來部署 Windows Form 應用程式的網站不同的網站，也會強制這些限制。</span><span class="sxs-lookup"><span data-stu-id="ff369-122">These restrictions are also enforced if you use the <xref:System.Windows.Forms.WebBrowser> control to display a Web site that is different from the Web site used to deploy your Windows Forms-based application.</span></span> <span data-ttu-id="ff369-123">如果您使用 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 部署技術，從網站 A 安裝應用程式，而且您使用 <xref:System.Windows.Forms.WebBrowser> 來顯示網站 B，則您將無法存取網站 B 的資料。</span><span class="sxs-lookup"><span data-stu-id="ff369-123">If you use [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] deployment technology to install your application from Web site A, and you use the <xref:System.Windows.Forms.WebBrowser> to display Web site B, you will not be able to access Web site B's data.</span></span>  
  
 <span data-ttu-id="ff369-124">如需有關跨網站指令碼的詳細資訊，請參閱[關於跨框架指令碼和安全性](https://msdn.microsoft.com/library/ms533028.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ff369-124">For more information about cross-site scripting, see [About Cross-Frame Scripting and Security](https://msdn.microsoft.com/library/ms533028.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff369-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff369-125">See Also</span></span>  
 [<span data-ttu-id="ff369-126">框架項目&#124;框架物件</span><span class="sxs-lookup"><span data-stu-id="ff369-126">FRAME Element &#124; frame Object</span></span>](https://msdn.microsoft.com/library/ms535250.aspx)  
 [<span data-ttu-id="ff369-127">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="ff369-127">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
