---
title: "如何：變更 Managed HTML 文件物件模型中的項目樣式"
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
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3726ccdebf310d831fb0d7ea21fab011293f6d99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="3b2ba-102">如何：變更 Managed HTML 文件物件模型中的項目樣式</span><span class="sxs-lookup"><span data-stu-id="3b2ba-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="3b2ba-103">您可以使用 html 樣式以控制文件和其項目的外觀。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="3b2ba-104"><xref:System.Windows.Forms.HtmlDocument>和<xref:System.Windows.Forms.HtmlElement>支援<xref:System.Windows.Forms.HtmlElement.Style%2A>採用下列格式的樣式字串的屬性：</span><span class="sxs-lookup"><span data-stu-id="3b2ba-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="3b2ba-105">以下是`DIV`與設定要以粗體顯示的 新細明體和所有文字的字型樣式字串：</span><span class="sxs-lookup"><span data-stu-id="3b2ba-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="3b2ba-106">與處理使用的樣式問題<xref:System.Windows.Forms.HtmlElement.Style%2A>屬性是，它可以證明麻煩加入和移除字串中的個別樣式設定。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="3b2ba-107">例如，它就會變成複雜的程序，為您呈現上一個斜體文字，每當使用者將游標置於`DIV`，並關閉當游標離開斜體`DIV`。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="3b2ba-108">如果您需要管理大量的這種方式中的樣式，時間就會成為問題。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="3b2ba-109">下列程序包含程式碼可讓您輕鬆地管理 HTML 文件和項目上的樣式。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="3b2ba-110">此程序需要您了解如何在 Windows Form，例如建立新的專案，以及將控制項加入表單中執行基本工作。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="3b2ba-111">處理 Windows Form 應用程式中的樣式變更</span><span class="sxs-lookup"><span data-stu-id="3b2ba-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="3b2ba-112">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="3b2ba-113">建立新的類別檔案，結尾適用於您的程式語言的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="3b2ba-114">複製`StyleGenerator`類別檔中，類別本主題的範例 > 一節中的程式碼，並儲存程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="3b2ba-115">將下列 HTML 儲存到名為 Test.htm 的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-115">Save the following HTML to a file named Test.htm.</span></span>  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  <span data-ttu-id="3b2ba-116">新增<xref:System.Windows.Forms.WebBrowser>控制項，名為`webBrowser1`加入主要表單的專案。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="3b2ba-117">將下列程式碼加入至您的專案程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3b2ba-118">請確認`webBrowser1_DocumentCompleted`事件處理常式設定為接聽程式<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="3b2ba-119">在[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，按兩下<xref:System.Windows.Forms.WebBrowser>控制; 請在文字編輯器中，接聽程式以程式設計方式設定。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-119">In [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="3b2ba-120">執行專案。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-120">Run the project.</span></span> <span data-ttu-id="3b2ba-121">執行您的資料指標在第一個`DIV`觀察程式碼的效果。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b2ba-122">範例</span><span class="sxs-lookup"><span data-stu-id="3b2ba-122">Example</span></span>  
 <span data-ttu-id="3b2ba-123">下列程式碼範例顯示的完整程式碼`StyleGenerator`類別，它會剖析現有的樣式值，支援加入、 變更，並移除樣式，並傳回新的樣式值，變更要求。</span><span class="sxs-lookup"><span data-stu-id="3b2ba-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3b2ba-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b2ba-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
