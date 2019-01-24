---
title: HOW TO：變更 Managed 的 HTML 文件物件模型中的項目樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 0db67936e368c1cb6d942b348ebacd87b6127e19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579377"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="4e804-102">HOW TO：變更 Managed 的 HTML 文件物件模型中的項目樣式</span><span class="sxs-lookup"><span data-stu-id="4e804-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="4e804-103">您可以使用在 HTML 中的樣式，來控制文件和其項目的外觀。</span><span class="sxs-lookup"><span data-stu-id="4e804-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="4e804-104"><xref:System.Windows.Forms.HtmlDocument> 並<xref:System.Windows.Forms.HtmlElement>支援<xref:System.Windows.Forms.HtmlElement.Style%2A>採用下列格式的樣式字串屬性：</span><span class="sxs-lookup"><span data-stu-id="4e804-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="4e804-105">以下是`DIV`字型設定為要以粗體顯示的 新細明體和所有文字的樣式字串：</span><span class="sxs-lookup"><span data-stu-id="4e804-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="4e804-106">操作使用的樣式問題<xref:System.Windows.Forms.HtmlElement.Style%2A>屬性是，它可以證明難以加入和移除字串中的個別的樣式設定。</span><span class="sxs-lookup"><span data-stu-id="4e804-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="4e804-107">例如，它會變得複雜的程序，為您呈現先前斜體文字，每當使用者將游標置於`DIV`，並採取關閉當游標離開斜體`DIV`。</span><span class="sxs-lookup"><span data-stu-id="4e804-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="4e804-108">如果您需要處理大量的這種方式中的樣式，時間就會成為問題。</span><span class="sxs-lookup"><span data-stu-id="4e804-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="4e804-109">下列程序包含您可用來輕鬆地操作 HTML 文件和項目樣式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e804-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="4e804-110">在程序需要您知道如何執行基本工作，在 Windows Forms 中，例如建立新的專案，以及將控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="4e804-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="4e804-111">處理 Windows Forms 應用程式中的樣式變更</span><span class="sxs-lookup"><span data-stu-id="4e804-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="4e804-112">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="4e804-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="4e804-113">建立新的類別檔案，以適合您的程式語言的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4e804-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="4e804-114">複製`StyleGenerator`類別檔中，類別在本主題的範例 > 一節中的程式碼，並儲存程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e804-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="4e804-115">將下列 HTML 儲存到名為 Test.htm 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e804-115">Save the following HTML to a file named Test.htm.</span></span>  
  
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
  
5.  <span data-ttu-id="4e804-116">新增<xref:System.Windows.Forms.WebBrowser>控制項，名為`webBrowser1`至主要表單的專案。</span><span class="sxs-lookup"><span data-stu-id="4e804-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="4e804-117">將下列程式碼新增至您的專案程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="4e804-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4e804-118">請確認`webBrowser1_DocumentCompleted`事件處理常式設定為接聽程式<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="4e804-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="4e804-119">在 Visual Studio 中，按兩下<xref:System.Windows.Forms.WebBrowser>控制; 請在文字編輯器中，設定接聽程式以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="4e804-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="4e804-120">執行專案。</span><span class="sxs-lookup"><span data-stu-id="4e804-120">Run the project.</span></span> <span data-ttu-id="4e804-121">執行您的資料指標在第一個`DIV`觀察程式碼的效果。</span><span class="sxs-lookup"><span data-stu-id="4e804-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e804-122">範例</span><span class="sxs-lookup"><span data-stu-id="4e804-122">Example</span></span>  
 <span data-ttu-id="4e804-123">下列程式碼範例顯示的完整程式碼`StyleGenerator`類別，它會剖析現有的樣式值，支援加入、 變更和移除設定的樣式，並傳回新的樣式值，變更要求。</span><span class="sxs-lookup"><span data-stu-id="4e804-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4e804-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e804-124">See also</span></span>
- <xref:System.Windows.Forms.HtmlElement>
