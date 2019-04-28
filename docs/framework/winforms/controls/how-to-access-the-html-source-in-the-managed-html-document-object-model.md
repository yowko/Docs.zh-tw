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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011264"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="0f652-102">HOW TO：存取受控 HTML 文件物件模型中的 HTML 原始檔</span><span class="sxs-lookup"><span data-stu-id="0f652-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="0f652-103">在第一次顯示目前的文件時，<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 控制項的 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 與 <xref:System.Windows.Forms.WebBrowser> 屬性會傳回其舊版的 HTML。</span><span class="sxs-lookup"><span data-stu-id="0f652-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="0f652-104">您若是使用方法與屬性呼叫 (例如 <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> 與 <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>) 修改頁面，這些變更將不會在您呼叫 <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> 及 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 時出現。</span><span class="sxs-lookup"><span data-stu-id="0f652-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="0f652-105">若要取得 DOM 的最新 HTML 來源，您必須呼叫 HTML 元素的 <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f652-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="0f652-106">下列程序示範如何擷取動態來源，以及如何在個別的捷徑功能表中顯示該來源。</span><span class="sxs-lookup"><span data-stu-id="0f652-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="0f652-107">擷取具有 OuterHtml 屬性的動態來源</span><span class="sxs-lookup"><span data-stu-id="0f652-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1. <span data-ttu-id="0f652-108">新建 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="0f652-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="0f652-109">開始使用單一<xref:System.Windows.Forms.Form>，並取名為`Form1`。</span><span class="sxs-lookup"><span data-stu-id="0f652-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2. <span data-ttu-id="0f652-110">主機<xref:System.Windows.Forms.WebBrowser>控制在 Windows Forms 應用程式，並將它命名`WebBrowser1`。</span><span class="sxs-lookup"><span data-stu-id="0f652-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="0f652-111">如需詳細資訊，請參閱[如何：將 Web 瀏覽器功能加入至 Windows Forms 應用程式](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f652-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3. <span data-ttu-id="0f652-112">建立第二個<xref:System.Windows.Forms.Form>呼叫的應用程式中`CodeForm`。</span><span class="sxs-lookup"><span data-stu-id="0f652-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4. <span data-ttu-id="0f652-113">新增<xref:System.Windows.Forms.RichTextBox>若要控制`CodeForm`並設定其<xref:System.Windows.Forms.Control.Dock%2A>屬性設`Fill`。</span><span class="sxs-lookup"><span data-stu-id="0f652-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5. <span data-ttu-id="0f652-114">在 建立公用屬性`CodeForm`稱為`Code`。</span><span class="sxs-lookup"><span data-stu-id="0f652-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6. <span data-ttu-id="0f652-115">新增<xref:System.Windows.Forms.Button>控制項，名為`Button1`至您<xref:System.Windows.Forms.Form>，並監視<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="0f652-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="0f652-116">如需監視事件的詳細資訊，請參閱[事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0f652-116">For details on monitoring events, see [Events](../../../standard/events/index.md).</span></span>  
  
7. <span data-ttu-id="0f652-117">將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0f652-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0f652-118">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0f652-118">Robust Programming</span></span>  
 <span data-ttu-id="0f652-119">嘗試擷取之前，請務必先測試 <xref:System.Windows.Forms.WebBrowser.Document%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="0f652-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="0f652-120">在未完全載入目前的頁面之前，可能不會起始設定 <xref:System.Windows.Forms.WebBrowser.Document%2A> 或其一或多個子物件。</span><span class="sxs-lookup"><span data-stu-id="0f652-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f652-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f652-121">See also</span></span>

- [<span data-ttu-id="0f652-122">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="0f652-122">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
- [<span data-ttu-id="0f652-123">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0f652-123">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
