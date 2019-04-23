---
title: HOW TO：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: cf1391e88c03095e0851d75ae6d50f8e809d13e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295610"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="d7363-102">HOW TO：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊</span><span class="sxs-lookup"><span data-stu-id="d7363-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="d7363-103">您可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項，將現有的動態 HTML (DHTML) Web 應用程式程式碼加入至 Windows Form 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7363-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="d7363-104">這適用於投資了大量的開發時間在建立 DHTML 控制項，而且您想要利用 Windows Form 的豐富使用者介面功能而又不需要重新撰寫現有程式碼的情況。</span><span class="sxs-lookup"><span data-stu-id="d7363-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="d7363-105"><xref:System.Windows.Forms.WebBrowser> 控制項可讓您實作用戶端應用程式程式碼與網頁指令碼程式碼之間的雙向通訊，這是透過 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 和 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d7363-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="d7363-106">此外，您可以設定 <xref:System.Windows.Forms.WebBrowser> 控制，好讓您的 Web 控制項與應用程式表單上其他控制項順暢地混合，隱藏其 DHTML 實作。</span><span class="sxs-lookup"><span data-stu-id="d7363-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="d7363-107">若要順暢地混合控制項，請格式化所顯示的頁面，以便其背景色彩和視覺化樣式符合表單的其餘部分，並使用 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A><xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> 和 <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> 屬性停用標準瀏覽器功能。</span><span class="sxs-lookup"><span data-stu-id="d7363-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="d7363-108">在 Windows Form 應用程式中內嵌 DHTML</span><span class="sxs-lookup"><span data-stu-id="d7363-108">To embed DHTML in your Windows Forms application</span></span>  
  
1. <span data-ttu-id="d7363-109">將 <xref:System.Windows.Forms.WebBrowser> 控制項的 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> 屬性設為 `false`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項開啟放到它上面的檔案。</span><span class="sxs-lookup"><span data-stu-id="d7363-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2. <span data-ttu-id="d7363-110">將控制項的 <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> 屬性設為 `false`，以防止使用者在 <xref:System.Windows.Forms.WebBrowser> 控制項上按一下滑鼠右鍵時顯示其捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="d7363-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3. <span data-ttu-id="d7363-111">將控制項的 <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> 屬性設為 `false`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項回應快速鍵。</span><span class="sxs-lookup"><span data-stu-id="d7363-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4. <span data-ttu-id="d7363-112">設定表單建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理常式中的 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d7363-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="d7363-113">下列程式碼會使用指令碼物件本身的表單類別。</span><span class="sxs-lookup"><span data-stu-id="d7363-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7363-114">元件物件模型 (COM) 必須能夠存取指令碼物件。</span><span class="sxs-lookup"><span data-stu-id="d7363-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="d7363-115">若要讓 COM 可看見表單，請將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性加入到您的表單類別。</span><span class="sxs-lookup"><span data-stu-id="d7363-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5. <span data-ttu-id="d7363-116">在您指令碼程式碼將使用的應用程式程式碼中實作公用屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="d7363-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="d7363-117">比方說，如果指令碼物件使用表單類別，請將下列程式碼加入至表單類別。</span><span class="sxs-lookup"><span data-stu-id="d7363-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6. <span data-ttu-id="d7363-118">在指令碼程式碼中使用 `window.external` 物件來存取指定物件的公用屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="d7363-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="d7363-119">下列 HTML 程式碼示範如何按一下按鈕以在指令碼物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d7363-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="d7363-120">將此程式碼複製到您使用控制項 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法載入的 HTML 文件的 BODY 項目，或是您指派給控制項 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性的 HTML 文件的 BODY 項目。</span><span class="sxs-lookup"><span data-stu-id="d7363-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7. <span data-ttu-id="d7363-121">實作您應用程式程式碼將使用之指令碼中的函式。</span><span class="sxs-lookup"><span data-stu-id="d7363-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="d7363-122">下列 HTML SCRIPT 項目提供範例函式。</span><span class="sxs-lookup"><span data-stu-id="d7363-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="d7363-123">將此程式碼複製到您使用控制項 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法載入的 HTML 文件的 HEAD 項目，或是您指派給控制項 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性的 HTML 文件的 HEAD 項目。</span><span class="sxs-lookup"><span data-stu-id="d7363-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8. <span data-ttu-id="d7363-124">使用 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性來從用戶端應用程式程式碼存取指令碼。</span><span class="sxs-lookup"><span data-stu-id="d7363-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="d7363-125">例如，將下列程式碼加入至按鈕 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7363-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="d7363-126">當您完成偵錯您 DHTML 時，請將控制項的 <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> 屬性設為 `true`，以防止 <xref:System.Windows.Forms.WebBrowser> 控制項顯示指令碼問題的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d7363-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="d7363-127">範例</span><span class="sxs-lookup"><span data-stu-id="d7363-127">Example</span></span>  
 <span data-ttu-id="d7363-128">下列完整程式碼範例提供示範應用程式，您可以用它來了解這項功能。</span><span class="sxs-lookup"><span data-stu-id="d7363-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="d7363-129">HTML 程式碼會透過 <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性載入至 <xref:System.Windows.Forms.WebBrowser> 控制項，而不會從個別的 HTML 檔案載入。</span><span class="sxs-lookup"><span data-stu-id="d7363-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7363-130">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d7363-130">Compiling the Code</span></span>  
 <span data-ttu-id="d7363-131">此程式碼需要：</span><span class="sxs-lookup"><span data-stu-id="d7363-131">This code requires:</span></span>  
  
-   <span data-ttu-id="d7363-132">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d7363-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d7363-133">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="d7363-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d7363-134">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d7363-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7363-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7363-135">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d7363-136">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="d7363-136">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
