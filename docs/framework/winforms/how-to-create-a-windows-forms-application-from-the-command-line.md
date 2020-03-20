---
title: 從命令列創建 Windows 表單應用程式
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181992"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="c26bd-102">如何：從命令列創建 Windows 表單應用程式</span><span class="sxs-lookup"><span data-stu-id="c26bd-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="c26bd-103">下列程序說明若要從命令列建立及執行 Windows Forms 應用程式，所必須完成的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="c26bd-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="c26bd-104">在 Visual Studio 中，對這些程序有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="c26bd-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="c26bd-105">另請參閱[演練：在 WPF 中託管 Windows 表單控制項](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="c26bd-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="c26bd-106">程序</span><span class="sxs-lookup"><span data-stu-id="c26bd-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="c26bd-107">建立表單</span><span class="sxs-lookup"><span data-stu-id="c26bd-107">To create the form</span></span>  
  
1. <span data-ttu-id="c26bd-108">在空代碼檔中，鍵入以下`Imports`或`using`語句：</span><span class="sxs-lookup"><span data-stu-id="c26bd-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="c26bd-109">聲明從 Form`Form1`類繼承的名為的類：</span><span class="sxs-lookup"><span data-stu-id="c26bd-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="c26bd-110">為`Form1`創建 無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="c26bd-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="c26bd-111">您在後續的程序中，會將更多程式碼加入建構函式中。</span><span class="sxs-lookup"><span data-stu-id="c26bd-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="c26bd-112">將 `Main` 方法加入類別中。</span><span class="sxs-lookup"><span data-stu-id="c26bd-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="c26bd-113">將<xref:System.STAThreadAttribute>應用 到`Main`C# 方法以指定 Windows 表單應用程式是單線程單元。</span><span class="sxs-lookup"><span data-stu-id="c26bd-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="c26bd-114">（在 Visual Basic 中不需要該屬性，因為預設情況下，使用 Visual Basic 開發的 Windows 表單應用程式使用單線程單元模型。</span><span class="sxs-lookup"><span data-stu-id="c26bd-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="c26bd-115">調用<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>以將作業系統樣式應用於應用程式。</span><span class="sxs-lookup"><span data-stu-id="c26bd-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="c26bd-116">建立表單的執行個體，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="c26bd-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="c26bd-117">編譯和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c26bd-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="c26bd-118">在 .NET Framework 命令提示字元中，巡覽至您建立 `Form1` 類別的目錄。</span><span class="sxs-lookup"><span data-stu-id="c26bd-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="c26bd-119">編譯表單。</span><span class="sxs-lookup"><span data-stu-id="c26bd-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="c26bd-120">如果使用 C#，則鍵入：`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="c26bd-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="c26bd-121">如果使用 Visual Basic，則鍵入：`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="c26bd-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="c26bd-122">在命令提示字元中，輸入：`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="c26bd-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="c26bd-123">添加控制項和處理事件</span><span class="sxs-lookup"><span data-stu-id="c26bd-123">Adding a control and handling an event</span></span>

<span data-ttu-id="c26bd-124">先前的程序步驟示範只是如何建立可編譯和執行的基本 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="c26bd-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="c26bd-125">下一個程序將會說明如何建立控制項並將其加入表單，以及處理控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="c26bd-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="c26bd-126">有關可添加到 Windows 表單的控制項的詳細資訊，請參閱[Windows 表單控制項](./controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c26bd-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="c26bd-127">除了了解如何建立 Windows Forms 應用程式，您還應該了解以事件為基礎的程式設計，以及如何處理使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="c26bd-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="c26bd-128">有關詳細資訊，請參閱在[Windows 表單 中創建事件處理常式](creating-event-handlers-in-windows-forms.md)[和處理使用者輸入](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="c26bd-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="c26bd-129">宣告按鈕控制項及處理其 Click 事件</span><span class="sxs-lookup"><span data-stu-id="c26bd-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="c26bd-130">宣告名為 `button1` 的按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="c26bd-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="c26bd-131">在建構函式中，建立按鈕，並設定其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c26bd-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="c26bd-132">將按鈕加入表單中。</span><span class="sxs-lookup"><span data-stu-id="c26bd-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="c26bd-133">以下代碼示例演示如何聲明按鈕控制項：</span><span class="sxs-lookup"><span data-stu-id="c26bd-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="c26bd-134">建立方法來處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="c26bd-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="c26bd-135">在 Click 事件處理常式中，顯示含有 "Hello World" 訊息的 <xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="c26bd-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="c26bd-136">以下代碼示例演示如何處理按鈕控制項的按一下事件：</span><span class="sxs-lookup"><span data-stu-id="c26bd-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="c26bd-137">使 <xref:System.Windows.Forms.Control.Click> 事件與您建立的方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c26bd-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="c26bd-138">下列程式碼範例會示範如何將事件與方法產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c26bd-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="c26bd-139">依照先前程序的說明，編譯及執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c26bd-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c26bd-140">範例</span><span class="sxs-lookup"><span data-stu-id="c26bd-140">Example</span></span>  

<span data-ttu-id="c26bd-141">以下代碼示例是前面過程的完整示例：</span><span class="sxs-lookup"><span data-stu-id="c26bd-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c26bd-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c26bd-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="c26bd-143">變更 Windows Forms 的外觀</span><span class="sxs-lookup"><span data-stu-id="c26bd-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="c26bd-144">增強 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="c26bd-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="c26bd-145">Windows Forms 使用者入門</span><span class="sxs-lookup"><span data-stu-id="c26bd-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
