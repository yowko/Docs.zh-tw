---
title: "如何： 從命令列建立 Windows Forms 應用程式"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="46072-102">如何： 從命令列建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="46072-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="46072-103">下列程序說明若要從命令列建立及執行 Windows Forms 應用程式，所必須完成的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="46072-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="46072-104">在 Visual Studio 中，對這些程序有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="46072-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="46072-105">另請參閱[逐步解說： 建立簡單的 Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\))。</span><span class="sxs-lookup"><span data-stu-id="46072-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="46072-106">程序</span><span class="sxs-lookup"><span data-stu-id="46072-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="46072-107">建立表單</span><span class="sxs-lookup"><span data-stu-id="46072-107">To create the form</span></span>  
  
1.  <span data-ttu-id="46072-108">在空的程式碼檔案中，輸入下列匯入或使用陳述式：</span><span class="sxs-lookup"><span data-stu-id="46072-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="46072-109">宣告繼承自表單類別且名為 `Form1` 的類別。</span><span class="sxs-lookup"><span data-stu-id="46072-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="46072-110">建立 `Form1` 的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="46072-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="46072-111">您在後續的程序中，會將更多程式碼加入建構函式中。</span><span class="sxs-lookup"><span data-stu-id="46072-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="46072-112">將 `Main` 方法加入類別中。</span><span class="sxs-lookup"><span data-stu-id="46072-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="46072-113">將 <xref:System.STAThreadAttribute> 套用至 `Main` 方法，以指定您的 Windows Form 應用程式是單一執行緒的 Apartment。</span><span class="sxs-lookup"><span data-stu-id="46072-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="46072-114">呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>，為您的應用程式提供 Windows XP 外觀。</span><span class="sxs-lookup"><span data-stu-id="46072-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="46072-115">建立表單的執行個體，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="46072-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="46072-116">編譯和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="46072-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="46072-117">在 .NET Framework 命令提示字元中，巡覽至您建立 `Form1` 類別的目錄。</span><span class="sxs-lookup"><span data-stu-id="46072-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="46072-118">編譯表單。</span><span class="sxs-lookup"><span data-stu-id="46072-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="46072-119">如果您使用的 C#，輸入：`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="46072-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="46072-120">如果您使用 Visual Basic 中，類型：`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="46072-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="46072-121">在命令提示字元中，輸入：`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="46072-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="46072-122">加入控制項和處理事件</span><span class="sxs-lookup"><span data-stu-id="46072-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="46072-123">先前的程序步驟示範只是如何建立可編譯和執行的基本 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="46072-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="46072-124">下一個程序將會說明如何建立控制項並將其加入表單，以及處理控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="46072-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="46072-125">如需您可以加入 Windows Form 控制項的相關資訊，請參閱[Windows Form 控制項](../../../docs/framework/winforms/controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="46072-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="46072-126">除了了解如何建立 Windows Forms 應用程式，您還應該了解以事件為基礎的程式設計，以及如何處理使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="46072-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="46072-127">如需詳細資訊，請參閱[建立 Windows Form 中的事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)，和[處理使用者輸入](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="46072-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="46072-128">宣告按鈕控制項及處理其 Click 事件</span><span class="sxs-lookup"><span data-stu-id="46072-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="46072-129">宣告名為 `button1` 的按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="46072-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="46072-130">在建構函式中，建立按鈕，並設定其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="46072-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="46072-131">將按鈕加入表單中。</span><span class="sxs-lookup"><span data-stu-id="46072-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="46072-132">下列程式碼範例會示範如何宣告按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="46072-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="46072-133">建立方法來處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="46072-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="46072-134">在 Click 事件處理常式中，顯示含有 "Hello World" 訊息的 <xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="46072-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="46072-135">下列程式碼範例會示範如何處理按鈕控制項的 Click 事件。</span><span class="sxs-lookup"><span data-stu-id="46072-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="46072-136">使 <xref:System.Windows.Forms.Control.Click> 事件與您建立的方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="46072-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="46072-137">下列程式碼範例會示範如何將事件與方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="46072-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="46072-138">依照先前程序的說明，編譯及執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="46072-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46072-139">範例</span><span class="sxs-lookup"><span data-stu-id="46072-139">Example</span></span>  
 <span data-ttu-id="46072-140">下列程式碼範例是先前程序的完整範例。</span><span class="sxs-lookup"><span data-stu-id="46072-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46072-141">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="46072-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="46072-142">若要編譯程式碼，請遵循前面說明如何編譯及執行應用程式之程序中的指示。</span><span class="sxs-lookup"><span data-stu-id="46072-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46072-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46072-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="46072-144">變更 Windows Forms 的外觀</span><span class="sxs-lookup"><span data-stu-id="46072-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="46072-145">增強 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="46072-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="46072-146">Windows Forms 使用者入門</span><span class="sxs-lookup"><span data-stu-id="46072-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
