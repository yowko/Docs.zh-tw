---
title: 如何：將鍵盤輸入修改為標準控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: c109615b9a0eb61d18f7f44e3248d2b24934ee5f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184950"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="f9e2f-102">如何：將鍵盤輸入修改為標準控制項</span><span class="sxs-lookup"><span data-stu-id="f9e2f-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="f9e2f-103">Windows Form 提供使用和修改鍵盤輸入的功能。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="f9e2f-104">使用按鍵表示在方法或事件處理常式中處理按鍵，讓訊息佇列較後面的其他方法和事件不會收到按鍵值。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="f9e2f-105">修改按鍵表示修改按鍵的值，讓訊息佇列較後面的方法和事件處理常式會收到不同的按鍵值。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="f9e2f-106">本主題將示範如何完成這些工作。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="f9e2f-107">使用按鍵</span><span class="sxs-lookup"><span data-stu-id="f9e2f-107">To consume a key</span></span>  
  
-   <span data-ttu-id="f9e2f-108">在 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式中，將 <xref:System.Windows.Forms.KeyPressEventArgs> 類別的 <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="f9e2f-109">-或-</span><span class="sxs-lookup"><span data-stu-id="f9e2f-109">-or-</span></span>  
  
     <span data-ttu-id="f9e2f-110">在 <xref:System.Windows.Forms.Control.KeyDown> 事件處理常式中，將 <xref:System.Windows.Forms.KeyEventArgs> 類別的 <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9e2f-111">在 <xref:System.Windows.Forms.Control.KeyDown> 事件處理常式中設定 <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> 屬性，並不會防止引發目前按鍵的 <xref:System.Windows.Forms.Control.KeyPress> 和 <xref:System.Windows.Forms.Control.KeyUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="f9e2f-112">為了這個目的，請使用 <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="f9e2f-113">下列範例摘錄自 `switch` 陳述式，它會檢查 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式所收到之 <xref:System.Windows.Forms.KeyPressEventArgs> 的 <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="f9e2f-114">這個程式碼使用 'A' 和 'a' 字元按鍵。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="f9e2f-115">修改標準的字元按鍵</span><span class="sxs-lookup"><span data-stu-id="f9e2f-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="f9e2f-116">在 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式中，將 <xref:System.Windows.Forms.KeyPressEventArgs> 類別的 <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> 屬性設定為新的字元按鍵值。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="f9e2f-117">下列範例摘錄自 `switch` 陳述式，它會將 'B' 修改為 'A' 並將 'b' 修改為 'a'。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="f9e2f-118">請注意，<xref:System.Windows.Forms.KeyPressEventArgs> 參數的 <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> 屬性會設定為 `false`，因此新按鍵值會傳播給訊息佇列中的其他方法和事件。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="f9e2f-119">修改非字元按鍵</span><span class="sxs-lookup"><span data-stu-id="f9e2f-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="f9e2f-120">覆寫處理 Windows 訊息的 <xref:System.Windows.Forms.Control> 方法，偵測 WM_KEYDOWN 或 WM_SYSKEYDOWN 訊息，並將 <xref:System.Windows.Forms.Message> 參數的 <xref:System.Windows.Forms.Message.WParam%2A> 屬性設定為代表新非字元按鍵的 <xref:System.Windows.Forms.Keys> 值。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="f9e2f-121">下列程式碼範例示範如何覆寫控制項的 <xref:System.Windows.Forms.Control.PreProcessMessage%2A> 方法，以偵測按鍵 F1 至 F9，並將任何 F3 按鍵修改為 F1。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="f9e2f-122">如需詳細資訊<xref:System.Windows.Forms.Control>方法，您可以覆寫以攔截鍵盤訊息，請參閱[在 Windows Forms 應用程式中的使用者輸入](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)並[鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](../../../docs/framework/winforms/how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f9e2f-123">範例</span><span class="sxs-lookup"><span data-stu-id="f9e2f-123">Example</span></span>  
 <span data-ttu-id="f9e2f-124">下列程式碼範例是前面幾節中程式碼範例的完整應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="f9e2f-125">這個應用程式使用衍生自 <xref:System.Windows.Forms.TextBox> 類別的自訂控制項來使用和修改鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9e2f-126">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f9e2f-126">Compiling the Code</span></span>  
 <span data-ttu-id="f9e2f-127">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f9e2f-127">This example requires:</span></span>  
  
-   <span data-ttu-id="f9e2f-128">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f9e2f-129">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f9e2f-130">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f9e2f-131">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f9e2f-131">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e2f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9e2f-132">See Also</span></span>  
 [<span data-ttu-id="f9e2f-133">Windows Forms 應用程式中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="f9e2f-133">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="f9e2f-134">Windows Forms 應用程式中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="f9e2f-134">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="f9e2f-135">鍵盤輸入的運作方式</span><span class="sxs-lookup"><span data-stu-id="f9e2f-135">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)
