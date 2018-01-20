---
title: "逐步解說：實作使用背景作業的表單"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaee6f1d650e6af57ab05ad56b5578e094ee50ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a><span data-ttu-id="20279-102">逐步解說：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="20279-102">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>
<span data-ttu-id="20279-103">如果您有要花費很長的時間才能完成，作業和不想使用者介面 (UI) 停止回應或 「 擱置 」，您可以使用<xref:System.ComponentModel.BackgroundWorker>類別，以另一個執行緒上執行作業。</span><span class="sxs-lookup"><span data-stu-id="20279-103">If you have an operation that will take a long time to complete, and you do not want your user interface (UI) to stop responding or "hang," you can use the <xref:System.ComponentModel.BackgroundWorker> class to execute the operation on another thread.</span></span>  
  
 <span data-ttu-id="20279-104">這個逐步解說將說明如何使用<xref:System.ComponentModel.BackgroundWorker>類別來執行耗時的計算，「 在背景中 」 時的使用者介面仍然能夠保持回應。</span><span class="sxs-lookup"><span data-stu-id="20279-104">This walkthrough illustrates how to use the <xref:System.ComponentModel.BackgroundWorker> class to perform time-consuming computations "in the background," while the user interface remains responsive.</span></span>  <span data-ttu-id="20279-105">當您進行逐步解說時，您必須讓應用程式以非同步方式計算 Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="20279-105">When you are through, you will have an application that computes Fibonacci numbers asynchronously.</span></span> <span data-ttu-id="20279-106">即使計算大量 Fibonacci 數字需要很長一段時間，主要 UI 執行緒不會受到此延遲的中斷，表單在計算期間仍然有回應。</span><span class="sxs-lookup"><span data-stu-id="20279-106">Even though computing a large Fibonacci number can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculation.</span></span>  
  
 <span data-ttu-id="20279-107">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="20279-107">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="20279-108">建立以 Windows 為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="20279-108">Creating a Windows-based Application</span></span>  
  
-   <span data-ttu-id="20279-109">建立<xref:System.ComponentModel.BackgroundWorker>表單中</span><span class="sxs-lookup"><span data-stu-id="20279-109">Creating a <xref:System.ComponentModel.BackgroundWorker> in Your Form</span></span>  
  
-   <span data-ttu-id="20279-110">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="20279-110">Adding Asynchronous Event Handlers</span></span>  
  
-   <span data-ttu-id="20279-111">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="20279-111">Adding Progress Reporting and Support for Cancellation</span></span>  
  
 <span data-ttu-id="20279-112">如需此範例中使用之程式碼的完整清單，請參閱[如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="20279-112">For a complete listing of the code used in this example, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20279-113">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="20279-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="20279-114">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="20279-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="20279-115">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="20279-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="20279-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="20279-116">Creating the Project</span></span>  
 <span data-ttu-id="20279-117">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="20279-117">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a><span data-ttu-id="20279-118">若要實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="20279-118">To create a form that uses a background operation</span></span>  
  
1.  <span data-ttu-id="20279-119">建立以 Windows 為基礎的應用程式專案，名為 `BackgroundWorkerExample`。</span><span class="sxs-lookup"><span data-stu-id="20279-119">Create a Windows-based application project called `BackgroundWorkerExample`.</span></span> <span data-ttu-id="20279-120">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="20279-120">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="20279-121">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1]，然後從捷徑功能表選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="20279-121">In **Solution Explorer**, right-click **Form1** and select **Rename** from the shortcut menu.</span></span> <span data-ttu-id="20279-122">將檔案名稱變更為 `FibonacciCalculator`。</span><span class="sxs-lookup"><span data-stu-id="20279-122">Change the file name to `FibonacciCalculator`.</span></span> <span data-ttu-id="20279-123">當系統詢問您是否要重新命名程式碼元素 '`Form1`' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="20279-123">Click the **Yes** button when you are asked if you want to rename all references to the code element '`Form1`'.</span></span>  
  
3.  <span data-ttu-id="20279-124">拖曳<xref:System.Windows.Forms.NumericUpDown>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="20279-124">Drag a <xref:System.Windows.Forms.NumericUpDown> control from the **Toolbox** onto the form.</span></span> <span data-ttu-id="20279-125">設定<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>屬性`1`和<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>屬性`91`。</span><span class="sxs-lookup"><span data-stu-id="20279-125">Set the <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> property to `1` and the <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> property to `91`.</span></span>  
  
4.  <span data-ttu-id="20279-126">加入兩個<xref:System.Windows.Forms.Button>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="20279-126">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span>  
  
5.  <span data-ttu-id="20279-127">重新命名的第一個<xref:System.Windows.Forms.Button>控制項`startAsyncButton`並設定<xref:System.Windows.Forms.Control.Text%2A>屬性`Start Async`。</span><span class="sxs-lookup"><span data-stu-id="20279-127">Rename the first <xref:System.Windows.Forms.Button> control `startAsyncButton` and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Start Async`.</span></span> <span data-ttu-id="20279-128">重新命名第二個<xref:System.Windows.Forms.Button>控制項`cancelAsyncButton`，並設定<xref:System.Windows.Forms.Control.Text%2A>屬性`Cancel Async`。</span><span class="sxs-lookup"><span data-stu-id="20279-128">Rename the second <xref:System.Windows.Forms.Button> control `cancelAsyncButton`, and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Cancel Async`.</span></span> <span data-ttu-id="20279-129">設定其<xref:System.Windows.Forms.Control.Enabled%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="20279-129">Set its <xref:System.Windows.Forms.Control.Enabled%2A> property to `false`.</span></span>  
  
6.  <span data-ttu-id="20279-130">建立事件處理常式的兩個<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="20279-130">Create an event handler for both of the <xref:System.Windows.Forms.Button> controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="20279-131">如需詳細資訊，請參閱[如何：使用設計工具建立事件處理常式](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)。</span><span class="sxs-lookup"><span data-stu-id="20279-131">For details, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
7.  <span data-ttu-id="20279-132">拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單並將它重新命名`resultLabel`。</span><span class="sxs-lookup"><span data-stu-id="20279-132">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the form and rename it `resultLabel`.</span></span>  
  
8.  <span data-ttu-id="20279-133">拖曳<xref:System.Windows.Forms.ProgressBar>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="20279-133">Drag a <xref:System.Windows.Forms.ProgressBar> control from the **Toolbox** onto the form.</span></span>  
  
## <a name="creating-a-backgroundworker-in-your-form"></a><span data-ttu-id="20279-134">在您的表單中建立 BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="20279-134">Creating a BackgroundWorker in Your Form</span></span>  
 <span data-ttu-id="20279-135">您可以建立<xref:System.ComponentModel.BackgroundWorker>用於您的非同步作業使用**Windows** **Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="20279-135">You can create the <xref:System.ComponentModel.BackgroundWorker> for your asynchronous operation using the **Windows** **Forms Designer**.</span></span>  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a><span data-ttu-id="20279-136">若要使用設計工具建立 BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="20279-136">To create a BackgroundWorker with the Designer</span></span>  
  
-   <span data-ttu-id="20279-137">從**元件** 索引標籤**工具箱**，拖曳<xref:System.ComponentModel.BackgroundWorker>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="20279-137">From the **Components** tab of the **Toolbox**, drag a <xref:System.ComponentModel.BackgroundWorker> onto the form.</span></span>  
  
## <a name="adding-asynchronous-event-handlers"></a><span data-ttu-id="20279-138">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="20279-138">Adding Asynchronous Event Handlers</span></span>  
 <span data-ttu-id="20279-139">現在您已經可以加入事件處理常式<xref:System.ComponentModel.BackgroundWorker>元件的非同步事件。</span><span class="sxs-lookup"><span data-stu-id="20279-139">You are now ready to add event handlers for the <xref:System.ComponentModel.BackgroundWorker> component's asynchronous events.</span></span> <span data-ttu-id="20279-140">將會在背景執行的耗費時間作業 (計算 Fibonacci 數字)，會由其中一個事件處理常式呼叫。</span><span class="sxs-lookup"><span data-stu-id="20279-140">The time-consuming operation that will run in the background, which computes Fibonacci numbers, is called by one of these event handlers.</span></span>  
  
#### <a name="to-implement-asynchronous-event-handlers"></a><span data-ttu-id="20279-141">若要實作非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="20279-141">To implement asynchronous event handlers</span></span>  
  
1.  <span data-ttu-id="20279-142">在**屬性**視窗中，與<xref:System.ComponentModel.BackgroundWorker>元件仍選取，按一下**事件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="20279-142">In the **Properties** window, with the <xref:System.ComponentModel.BackgroundWorker> component still selected, click the **Events** button.</span></span> <span data-ttu-id="20279-143">按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="20279-143">Double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span> <span data-ttu-id="20279-144">如需如何建立事件處理常式的詳細資訊，請參閱[如何：使用設計工具建立事件處理常式](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)。</span><span class="sxs-lookup"><span data-stu-id="20279-144">For more information about how to use event handlers, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
2.  <span data-ttu-id="20279-145">在表單中，建立名為 `ComputeFibonacci` 的新方法。</span><span class="sxs-lookup"><span data-stu-id="20279-145">Create a new method, called `ComputeFibonacci`, in your form.</span></span> <span data-ttu-id="20279-146">這個方法會執行實際的工作，並且會在背景執行。</span><span class="sxs-lookup"><span data-stu-id="20279-146">This method does the actual work, and it will run in the background.</span></span> <span data-ttu-id="20279-147">此程式碼會示範 Fibonacci 演算法的遞迴實作，它非常沒有效率，對於較大的數字要耗費更長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="20279-147">This code demonstrates the recursive implementation of the Fibonacci algorithm, which is notably inefficient, taking exponentially longer time to complete for larger numbers.</span></span> <span data-ttu-id="20279-148">它在這裡是針對說明目的使用，以示範會導致應用程式長時間延遲的作業。</span><span class="sxs-lookup"><span data-stu-id="20279-148">It is used here for illustrative purposes, to show an operation that can introduce long delays in your application.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  <span data-ttu-id="20279-149">在<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式，將呼叫加入`ComputeFibonacci`方法。</span><span class="sxs-lookup"><span data-stu-id="20279-149">In the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, add a call to the `ComputeFibonacci` method.</span></span> <span data-ttu-id="20279-150">採取的第一個參數`ComputeFibonacci`從<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="20279-150">Take the first parameter for `ComputeFibonacci` from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="20279-151"><xref:System.ComponentModel.BackgroundWorker>和<xref:System.ComponentModel.DoWorkEventArgs>參數將會稍後會用來進行報告和取消支援。</span><span class="sxs-lookup"><span data-stu-id="20279-151">The <xref:System.ComponentModel.BackgroundWorker> and <xref:System.ComponentModel.DoWorkEventArgs> parameters will be used later for progress reporting and cancellation support.</span></span> <span data-ttu-id="20279-152">從傳回的值指派`ComputeFibonacci`至<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="20279-152">Assign the return value from `ComputeFibonacci` to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="20279-153">此結果可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="20279-153">This result will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20279-154"><xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式未參考`backgroundWorker1`執行直接個體變數，因為這會結合此事件處理常式的特定執行個體<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="20279-154">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler does not reference the `backgroundWorker1` instance variable directly, as this would couple this event handler to a specific instance of <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="20279-155">相反地，參考<xref:System.ComponentModel.BackgroundWorker>，會引發這個事件從復原`sender`參數。</span><span class="sxs-lookup"><span data-stu-id="20279-155">Instead, a reference to the <xref:System.ComponentModel.BackgroundWorker> that raised this event is recovered from the `sender` parameter.</span></span> <span data-ttu-id="20279-156">表單裝載一個以上時，這是重要<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="20279-156">This is important when the form hosts more than one <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="20279-157">也很重要不到操作中的任何使用者介面物件您<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="20279-157">It is also important not to manipulate any user-interface objects in your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="20279-158">相反地，透過使用者介面通訊<xref:System.ComponentModel.BackgroundWorker>事件。</span><span class="sxs-lookup"><span data-stu-id="20279-158">Instead, communicate to the user interface through the <xref:System.ComponentModel.BackgroundWorker> events.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  <span data-ttu-id="20279-159">在`startAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，加入會啟動非同步作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="20279-159">In the `startAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that starts the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  <span data-ttu-id="20279-160">在<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式，指派至計算結果的`resultLabel`控制項。</span><span class="sxs-lookup"><span data-stu-id="20279-160">In the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler, assign the result of the calculation to the `resultLabel` control.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a><span data-ttu-id="20279-161">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="20279-161">Adding Progress Reporting and Support for Cancellation</span></span>  
 <span data-ttu-id="20279-162">對於需要長時間的非同步作業，通常會想要對使用者報告進度，並且允許使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="20279-162">For asynchronous operations that will take a long time, it is often desirable to report progress to the user and to allow the user to cancel the operation.</span></span> <span data-ttu-id="20279-163"><xref:System.ComponentModel.BackgroundWorker>類別會提供可讓您為您的背景作業會繼續進行張貼進度事件。</span><span class="sxs-lookup"><span data-stu-id="20279-163">The <xref:System.ComponentModel.BackgroundWorker> class provides an event that allows you to post progress as your background operation proceeds.</span></span> <span data-ttu-id="20279-164">它也提供旗標，可讓您的背景工作程式碼來偵測呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>及插斷本身。</span><span class="sxs-lookup"><span data-stu-id="20279-164">It also provides a flag that allows your worker code to detect a call to <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> and interrupt itself.</span></span>  
  
#### <a name="to-implement-progress-reporting"></a><span data-ttu-id="20279-165">若要實作進度報告</span><span class="sxs-lookup"><span data-stu-id="20279-165">To implement progress reporting</span></span>  
  
1.  <span data-ttu-id="20279-166">在 [屬性] 視窗中，選取 `backgroundWorker1`。</span><span class="sxs-lookup"><span data-stu-id="20279-166">In the **Properties**, window, select `backgroundWorker1`.</span></span> <span data-ttu-id="20279-167">設定<xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A>和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="20279-167">Set the <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span>  
  
2.  <span data-ttu-id="20279-168">宣告 `FibonacciCalculator` 表單中的兩個變數。</span><span class="sxs-lookup"><span data-stu-id="20279-168">Declare two variables in the `FibonacciCalculator` form.</span></span> <span data-ttu-id="20279-169">這些項目會用來追蹤進度。</span><span class="sxs-lookup"><span data-stu-id="20279-169">These will be used to track progress.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  <span data-ttu-id="20279-170">加入 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="20279-170">Add an event handler for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="20279-171">在<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式、 更新<xref:System.Windows.Forms.ProgressBar>與<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>屬性<xref:System.ComponentModel.ProgressChangedEventArgs>參數。</span><span class="sxs-lookup"><span data-stu-id="20279-171">In the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler, update the <xref:System.Windows.Forms.ProgressBar> with the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> property of the <xref:System.ComponentModel.ProgressChangedEventArgs> parameter.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a><span data-ttu-id="20279-172">若要實作支援取消作業</span><span class="sxs-lookup"><span data-stu-id="20279-172">To implement support for cancellation</span></span>  
  
1.  <span data-ttu-id="20279-173">在`cancelAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，加入程式碼可取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="20279-173">In the `cancelAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that cancels the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  <span data-ttu-id="20279-174">`ComputeFibonacci` 方法中的下列程式碼片段會報告進度和支援取消。</span><span class="sxs-lookup"><span data-stu-id="20279-174">The following code fragments in the `ComputeFibonacci` method report progress and support cancellation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a><span data-ttu-id="20279-175">檢查點</span><span class="sxs-lookup"><span data-stu-id="20279-175">Checkpoint</span></span>  
 <span data-ttu-id="20279-176">此時，您可以編譯並執行 Fibonacci 計算機應用程式。</span><span class="sxs-lookup"><span data-stu-id="20279-176">At this point, you can compile and run the Fibonacci Calculator application.</span></span>  
  
#### <a name="to-test-your-project"></a><span data-ttu-id="20279-177">若要測試專案</span><span class="sxs-lookup"><span data-stu-id="20279-177">To test your project</span></span>  
  
-   <span data-ttu-id="20279-178">按 F5 編譯和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="20279-178">Press F5 to compile and run the application.</span></span>  
  
     <span data-ttu-id="20279-179">在背景執行計算時，您會看到<xref:System.Windows.Forms.ProgressBar>顯示完成計算的進度。</span><span class="sxs-lookup"><span data-stu-id="20279-179">While the calculation is running in the background, you will see the <xref:System.Windows.Forms.ProgressBar> displaying the progress of the calculation toward completion.</span></span> <span data-ttu-id="20279-180">您也可以取消暫止的作業。</span><span class="sxs-lookup"><span data-stu-id="20279-180">You can also cancel the pending operation.</span></span>  
  
     <span data-ttu-id="20279-181">對於小數字，計算應該非常快速，但是對於較大的數字，您應該會看到明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="20279-181">For small numbers, the calculation should be very fast, but for larger numbers, you should see a noticeable delay.</span></span> <span data-ttu-id="20279-182">如果您輸入的值為 30 或更大，您應該會看到幾秒鐘的延遲，取決於您的電腦速度。</span><span class="sxs-lookup"><span data-stu-id="20279-182">If you enter a value of 30 or greater, you should see a delay of several seconds, depending on the speed of your computer.</span></span> <span data-ttu-id="20279-183">對於大於 40 的值，可能需要數分鐘或數小時才能完成計算。</span><span class="sxs-lookup"><span data-stu-id="20279-183">For values greater than 40, it may take minutes or hours to finish the calculation.</span></span> <span data-ttu-id="20279-184">當計算機忙著計算大量 Fibonacci 數字時，請注意，您可以自由地到處移動表單、最小化、最大化，甚至是關閉表單。</span><span class="sxs-lookup"><span data-stu-id="20279-184">While the calculator is busy computing a large Fibonacci number, notice that you can freely move the form around, minimize, maximize, and even dismiss it.</span></span> <span data-ttu-id="20279-185">這是因為主要 UI 執行緒並沒有在等待計算完成。</span><span class="sxs-lookup"><span data-stu-id="20279-185">This is because the main UI thread is not waiting for the calculation to finish.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="20279-186">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20279-186">Next Steps</span></span>  
 <span data-ttu-id="20279-187">既然您已實作使用的表單<xref:System.ComponentModel.BackgroundWorker>元件來執行計算，在背景中，您可以瀏覽其他非同步作業的可能性：</span><span class="sxs-lookup"><span data-stu-id="20279-187">Now that you have implemented a form that uses a <xref:System.ComponentModel.BackgroundWorker> component to execute a computation in the background, you can explore other possibilities for asynchronous operations:</span></span>  
  
-   <span data-ttu-id="20279-188">使用多個<xref:System.ComponentModel.BackgroundWorker>數個同時作業的物件。</span><span class="sxs-lookup"><span data-stu-id="20279-188">Use multiple <xref:System.ComponentModel.BackgroundWorker> objects for several simultaneous operations.</span></span>  
  
-   <span data-ttu-id="20279-189">若要針對多執行緒應用程式進行偵錯，請參閱[如何：使用執行緒視窗](/visualstudio/debugger/how-to-use-the-threads-window)。</span><span class="sxs-lookup"><span data-stu-id="20279-189">To debug your multithreaded application, see [How to: Use the Threads Window](/visualstudio/debugger/how-to-use-the-threads-window).</span></span>  
  
-   <span data-ttu-id="20279-190">實作您自己的元件，支援非同步程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="20279-190">Implement your own component that supports the asynchronous programming model.</span></span> <span data-ttu-id="20279-191">如需詳細資訊，請參閱[事件架構非同步模式概觀](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="20279-191">For more information, see [Event-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="20279-192">無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="20279-192">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="20279-193">請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="20279-193">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20279-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="20279-194">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="20279-195">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="20279-195">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="20279-196">元件中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="20279-196">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="20279-197">不在組建中： Visual Basic 中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="20279-197">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="20279-198">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="20279-198">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="20279-199">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="20279-199">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [<span data-ttu-id="20279-200">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="20279-200">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
