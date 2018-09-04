---
title: 逐步解說：在背景執行作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 09019f24248985c0a1057873f0226ee69a30ca9d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562954"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="40450-102">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="40450-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="40450-103">如果您有要花費較長時間才能完成的作業，但您不想導致使用者介面發生延遲，就可以使用 <xref:System.ComponentModel.BackgroundWorker> 類別在另一個執行緒上執行該作業。</span><span class="sxs-lookup"><span data-stu-id="40450-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="40450-104">如需在此範例中使用的程式碼的完整清單，請參閱 <<c0> [ 如何： 在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。</span><span class="sxs-lookup"><span data-stu-id="40450-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40450-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="40450-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="40450-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="40450-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="40450-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="40450-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="40450-108">若要在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="40450-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="40450-109">與您在 Windows Form 設計工具中的表單，將兩個<xref:System.Windows.Forms.Button>控制項從**工具箱**到表單，並再把`Name`和<xref:System.Windows.Forms.Control.Text%2A>根據下表按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="40450-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="40450-110">按鈕</span><span class="sxs-lookup"><span data-stu-id="40450-110">Button</span></span>|<span data-ttu-id="40450-111">名稱</span><span class="sxs-lookup"><span data-stu-id="40450-111">Name</span></span>|<span data-ttu-id="40450-112">Text</span><span class="sxs-lookup"><span data-stu-id="40450-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="40450-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="40450-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="40450-114">**取消**</span><span class="sxs-lookup"><span data-stu-id="40450-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="40450-115">開啟**工具箱**，按一下**元件**索引標籤，然後再拖曳<xref:System.ComponentModel.BackgroundWorker>元件拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="40450-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="40450-116">`backgroundWorker1`元件會出現在**元件匣**。</span><span class="sxs-lookup"><span data-stu-id="40450-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="40450-117">在 **屬性**視窗中，將<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="40450-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="40450-118">在 **屬性**視窗中，按一下**事件**按鈕，然後再連按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="40450-119">插入您耗費時間的程式碼插入<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="40450-120">擷取作業所需的任何參數<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>參數。</span><span class="sxs-lookup"><span data-stu-id="40450-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="40450-121">若要計算的結果指派<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="40450-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="40450-122">這是將可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="40450-123">插入程式碼來擷取在您作業的結果<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="40450-124">實作 `TimeConsumingOperation` 方法。</span><span class="sxs-lookup"><span data-stu-id="40450-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="40450-125">在 Windows Form 設計工具中，按兩下`startButton`來建立<xref:System.Windows.Forms.Control.Click>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="40450-126">呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>方法中的<xref:System.Windows.Forms.Control.Click>事件處理常式`startButton`。</span><span class="sxs-lookup"><span data-stu-id="40450-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="40450-127">在 Windows Form 設計工具中，按兩下`cancelButton`來建立<xref:System.Windows.Forms.Control.Click>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="40450-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="40450-128">呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法中的<xref:System.Windows.Forms.Control.Click>事件處理常式`cancelButton`。</span><span class="sxs-lookup"><span data-stu-id="40450-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="40450-129">在檔案頂端，匯入 System.ComponentModel 和 System.Threading 命名空間。</span><span class="sxs-lookup"><span data-stu-id="40450-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="40450-130">按下 F6 以建置方案，，然後按 CTRL-F5 執行應用程式偵錯工具之外。</span><span class="sxs-lookup"><span data-stu-id="40450-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40450-131">如果您按 F5 執行應用程式在偵錯工具，在引發例外狀況`TimeConsumingOperation`方法會攔截到並顯示偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="40450-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="40450-132">當您執行偵錯工具中，外部應用程式時<xref:System.ComponentModel.BackgroundWorker>處理例外狀況，並快取中<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>屬性<xref:System.ComponentModel.RunWorkerCompletedEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="40450-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="40450-133">按一下 **開始**按鈕以執行非同步作業，，然後按一下**取消**按鈕以停止執行中的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="40450-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="40450-134">每個作業的結果會顯示於 <xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="40450-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="40450-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="40450-135">Next Steps</span></span>  
  
-   <span data-ttu-id="40450-136">實作非同步作業進行時，報告進度的表單。</span><span class="sxs-lookup"><span data-stu-id="40450-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="40450-137">如需詳細資訊，請參閱 <<c0> [ 如何： 實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="40450-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="40450-138">實作元件支援非同步模式的類別。</span><span class="sxs-lookup"><span data-stu-id="40450-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="40450-139">如需詳細資訊，請參閱 <<c0> [ 實作事件架構非同步模式](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="40450-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40450-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40450-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="40450-141">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="40450-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="40450-142">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="40450-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="40450-143">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="40450-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
