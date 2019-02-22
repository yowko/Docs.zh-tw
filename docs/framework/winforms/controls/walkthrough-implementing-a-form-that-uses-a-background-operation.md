---
title: 逐步解說：實作使用背景作業的表單
ms.date: 03/30/2017
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
ms.openlocfilehash: 042861b2d79d0b638600a5463673fb922f3b4881
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664389"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a><span data-ttu-id="98093-102">逐步解說：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="98093-102">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>
<span data-ttu-id="98093-103">如果您有會花費很長的時間才能完成，且不想您的使用者介面 (UI) 停止回應或 「 擱置 」，您可以使用<xref:System.ComponentModel.BackgroundWorker>類別，以另一個執行緒上執行作業。</span><span class="sxs-lookup"><span data-stu-id="98093-103">If you have an operation that will take a long time to complete, and you do not want your user interface (UI) to stop responding or "hang," you can use the <xref:System.ComponentModel.BackgroundWorker> class to execute the operation on another thread.</span></span>  
  
 <span data-ttu-id="98093-104">此逐步解說將說明如何使用<xref:System.ComponentModel.BackgroundWorker>類別執行耗費時間的計算，「 在背景中 」 時的使用者介面仍然能夠保持回應。</span><span class="sxs-lookup"><span data-stu-id="98093-104">This walkthrough illustrates how to use the <xref:System.ComponentModel.BackgroundWorker> class to perform time-consuming computations "in the background," while the user interface remains responsive.</span></span>  <span data-ttu-id="98093-105">當您進行逐步解說時，您必須讓應用程式以非同步方式計算 Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="98093-105">When you are through, you will have an application that computes Fibonacci numbers asynchronously.</span></span> <span data-ttu-id="98093-106">即使計算大量 Fibonacci 數字需要很長一段時間，主要 UI 執行緒不會受到此延遲的中斷，表單在計算期間仍然有回應。</span><span class="sxs-lookup"><span data-stu-id="98093-106">Even though computing a large Fibonacci number can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculation.</span></span>  
  
 <span data-ttu-id="98093-107">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="98093-107">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="98093-108">建立以 Windows 為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="98093-108">Creating a Windows-based Application</span></span>  
  
-   <span data-ttu-id="98093-109">建立<xref:System.ComponentModel.BackgroundWorker>在表單中</span><span class="sxs-lookup"><span data-stu-id="98093-109">Creating a <xref:System.ComponentModel.BackgroundWorker> in Your Form</span></span>  
  
-   <span data-ttu-id="98093-110">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="98093-110">Adding Asynchronous Event Handlers</span></span>  
  
-   <span data-ttu-id="98093-111">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="98093-111">Adding Progress Reporting and Support for Cancellation</span></span>  
  
 <span data-ttu-id="98093-112">如需在此範例中使用的程式碼的完整清單，請參閱[How to:實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="98093-112">For a complete listing of the code used in this example, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98093-113">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="98093-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="98093-114">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="98093-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="98093-115">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="98093-115">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="98093-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="98093-116">Creating the Project</span></span>  
 <span data-ttu-id="98093-117">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="98093-117">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a><span data-ttu-id="98093-118">若要實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="98093-118">To create a form that uses a background operation</span></span>  
  
1.  <span data-ttu-id="98093-119">建立以 Windows 為基礎的應用程式專案，稱為`BackgroundWorkerExample`(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="98093-119">Create a Windows-based application project called `BackgroundWorkerExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="98093-120">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1]，然後從捷徑功能表選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="98093-120">In **Solution Explorer**, right-click **Form1** and select **Rename** from the shortcut menu.</span></span> <span data-ttu-id="98093-121">將檔案名稱變更為 `FibonacciCalculator`。</span><span class="sxs-lookup"><span data-stu-id="98093-121">Change the file name to `FibonacciCalculator`.</span></span> <span data-ttu-id="98093-122">當系統詢問您是否要重新命名程式碼元素 '`Form1`' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="98093-122">Click the **Yes** button when you are asked if you want to rename all references to the code element '`Form1`'.</span></span>  
  
3.  <span data-ttu-id="98093-123">拖曳<xref:System.Windows.Forms.NumericUpDown>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="98093-123">Drag a <xref:System.Windows.Forms.NumericUpDown> control from the **Toolbox** onto the form.</span></span> <span data-ttu-id="98093-124">設定<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>屬性，以`1`並<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>屬性設`91`。</span><span class="sxs-lookup"><span data-stu-id="98093-124">Set the <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> property to `1` and the <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> property to `91`.</span></span>  
  
4.  <span data-ttu-id="98093-125">新增兩個<xref:System.Windows.Forms.Button>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="98093-125">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span>  
  
5.  <span data-ttu-id="98093-126">重新命名第一個<xref:System.Windows.Forms.Button>控制`startAsyncButton`並設定<xref:System.Windows.Forms.Control.Text%2A>屬性設`Start Async`。</span><span class="sxs-lookup"><span data-stu-id="98093-126">Rename the first <xref:System.Windows.Forms.Button> control `startAsyncButton` and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Start Async`.</span></span> <span data-ttu-id="98093-127">重新命名第二個<xref:System.Windows.Forms.Button>控制`cancelAsyncButton`，並將<xref:System.Windows.Forms.Control.Text%2A>屬性設`Cancel Async`。</span><span class="sxs-lookup"><span data-stu-id="98093-127">Rename the second <xref:System.Windows.Forms.Button> control `cancelAsyncButton`, and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Cancel Async`.</span></span> <span data-ttu-id="98093-128">設定其<xref:System.Windows.Forms.Control.Enabled%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="98093-128">Set its <xref:System.Windows.Forms.Control.Enabled%2A> property to `false`.</span></span>  
  
6.  <span data-ttu-id="98093-129">這兩個建立的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="98093-129">Create an event handler for both of the <xref:System.Windows.Forms.Button> controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="98093-130">如需詳細資訊，請參閱[如何：建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="98093-130">For details, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>  
  
7.  <span data-ttu-id="98093-131">拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單，並重新命名`resultLabel`。</span><span class="sxs-lookup"><span data-stu-id="98093-131">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the form and rename it `resultLabel`.</span></span>  
  
8.  <span data-ttu-id="98093-132">拖曳<xref:System.Windows.Forms.ProgressBar>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="98093-132">Drag a <xref:System.Windows.Forms.ProgressBar> control from the **Toolbox** onto the form.</span></span>  
  
## <a name="creating-a-backgroundworker-in-your-form"></a><span data-ttu-id="98093-133">在您的表單中建立 BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="98093-133">Creating a BackgroundWorker in Your Form</span></span>  
 <span data-ttu-id="98093-134">您可以建立<xref:System.ComponentModel.BackgroundWorker>非同步作業使用**Windows** **Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="98093-134">You can create the <xref:System.ComponentModel.BackgroundWorker> for your asynchronous operation using the **Windows** **Forms Designer**.</span></span>  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a><span data-ttu-id="98093-135">若要使用設計工具建立 BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="98093-135">To create a BackgroundWorker with the Designer</span></span>  
  
-   <span data-ttu-id="98093-136">從**元件**索引標籤**工具箱**，拖曳<xref:System.ComponentModel.BackgroundWorker>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="98093-136">From the **Components** tab of the **Toolbox**, drag a <xref:System.ComponentModel.BackgroundWorker> onto the form.</span></span>  
  
## <a name="adding-asynchronous-event-handlers"></a><span data-ttu-id="98093-137">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="98093-137">Adding Asynchronous Event Handlers</span></span>  
 <span data-ttu-id="98093-138">您現在已準備好新增事件處理常式<xref:System.ComponentModel.BackgroundWorker>元件的非同步事件。</span><span class="sxs-lookup"><span data-stu-id="98093-138">You are now ready to add event handlers for the <xref:System.ComponentModel.BackgroundWorker> component's asynchronous events.</span></span> <span data-ttu-id="98093-139">將會在背景執行的耗費時間作業 (計算 Fibonacci 數字)，會由其中一個事件處理常式呼叫。</span><span class="sxs-lookup"><span data-stu-id="98093-139">The time-consuming operation that will run in the background, which computes Fibonacci numbers, is called by one of these event handlers.</span></span>  
  
#### <a name="to-implement-asynchronous-event-handlers"></a><span data-ttu-id="98093-140">若要實作非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="98093-140">To implement asynchronous event handlers</span></span>  
  
1.  <span data-ttu-id="98093-141">在 [**屬性**] 視窗中，使用<xref:System.ComponentModel.BackgroundWorker>元件保持選取，按一下 [**事件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="98093-141">In the **Properties** window, with the <xref:System.ComponentModel.BackgroundWorker> component still selected, click the **Events** button.</span></span> <span data-ttu-id="98093-142">按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98093-142">Double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span> <span data-ttu-id="98093-143">如需如何使用事件處理常式的詳細資訊，請參閱[How to:建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="98093-143">For more information about how to use event handlers, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="98093-144">在表單中，建立名為 `ComputeFibonacci` 的新方法。</span><span class="sxs-lookup"><span data-stu-id="98093-144">Create a new method, called `ComputeFibonacci`, in your form.</span></span> <span data-ttu-id="98093-145">這個方法會執行實際的工作，並且會在背景執行。</span><span class="sxs-lookup"><span data-stu-id="98093-145">This method does the actual work, and it will run in the background.</span></span> <span data-ttu-id="98093-146">此程式碼會示範 Fibonacci 演算法的遞迴實作，它非常沒有效率，對於較大的數字要耗費更長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="98093-146">This code demonstrates the recursive implementation of the Fibonacci algorithm, which is notably inefficient, taking exponentially longer time to complete for larger numbers.</span></span> <span data-ttu-id="98093-147">它在這裡是針對說明目的使用，以示範會導致應用程式長時間延遲的作業。</span><span class="sxs-lookup"><span data-stu-id="98093-147">It is used here for illustrative purposes, to show an operation that can introduce long delays in your application.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  <span data-ttu-id="98093-148">在 <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式，將呼叫加入`ComputeFibonacci`方法。</span><span class="sxs-lookup"><span data-stu-id="98093-148">In the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, add a call to the `ComputeFibonacci` method.</span></span> <span data-ttu-id="98093-149">採取的第一個參數`ComputeFibonacci`從<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="98093-149">Take the first parameter for `ComputeFibonacci` from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="98093-150"><xref:System.ComponentModel.BackgroundWorker>和<xref:System.ComponentModel.DoWorkEventArgs>參數將稍後用於進度報告與取消支援。</span><span class="sxs-lookup"><span data-stu-id="98093-150">The <xref:System.ComponentModel.BackgroundWorker> and <xref:System.ComponentModel.DoWorkEventArgs> parameters will be used later for progress reporting and cancellation support.</span></span> <span data-ttu-id="98093-151">將指定的傳回值`ComputeFibonacci`要<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="98093-151">Assign the return value from `ComputeFibonacci` to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="98093-152">這個結果可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98093-152">This result will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="98093-153"><xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式不會參考`backgroundWorker1`執行直接個體變數，因為這會結合此事件處理常式的特定執行個體<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="98093-153">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler does not reference the `backgroundWorker1` instance variable directly, as this would couple this event handler to a specific instance of <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="98093-154">相反地，參考<xref:System.ComponentModel.BackgroundWorker>，會引發這個事件從復原`sender`參數。</span><span class="sxs-lookup"><span data-stu-id="98093-154">Instead, a reference to the <xref:System.ComponentModel.BackgroundWorker> that raised this event is recovered from the `sender` parameter.</span></span> <span data-ttu-id="98093-155">當表單裝載一個以上時，這點很重要<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="98093-155">This is important when the form hosts more than one <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="98093-156">務必也沒有任何使用者介面中操作物件您<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98093-156">It is also important not to manipulate any user-interface objects in your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="98093-157">相反地，透過使用者介面通訊<xref:System.ComponentModel.BackgroundWorker>事件。</span><span class="sxs-lookup"><span data-stu-id="98093-157">Instead, communicate to the user interface through the <xref:System.ComponentModel.BackgroundWorker> events.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  <span data-ttu-id="98093-158">在 `startAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，將會啟動非同步作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="98093-158">In the `startAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that starts the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  <span data-ttu-id="98093-159">在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式，指派的計算結果`resultLabel`控制項。</span><span class="sxs-lookup"><span data-stu-id="98093-159">In the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler, assign the result of the calculation to the `resultLabel` control.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a><span data-ttu-id="98093-160">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="98093-160">Adding Progress Reporting and Support for Cancellation</span></span>  
 <span data-ttu-id="98093-161">對於需要長時間的非同步作業，通常會想要對使用者報告進度，並且允許使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="98093-161">For asynchronous operations that will take a long time, it is often desirable to report progress to the user and to allow the user to cancel the operation.</span></span> <span data-ttu-id="98093-162"><xref:System.ComponentModel.BackgroundWorker>類別會提供事件，可讓您的背景作業進行時公佈進度。</span><span class="sxs-lookup"><span data-stu-id="98093-162">The <xref:System.ComponentModel.BackgroundWorker> class provides an event that allows you to post progress as your background operation proceeds.</span></span> <span data-ttu-id="98093-163">它也提供旗標，可讓您的背景工作角色程式碼，來偵測呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>並且自行中斷。</span><span class="sxs-lookup"><span data-stu-id="98093-163">It also provides a flag that allows your worker code to detect a call to <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> and interrupt itself.</span></span>  
  
#### <a name="to-implement-progress-reporting"></a><span data-ttu-id="98093-164">若要實作進度報告</span><span class="sxs-lookup"><span data-stu-id="98093-164">To implement progress reporting</span></span>  
  
1.  <span data-ttu-id="98093-165">在 [屬性] 視窗中，選取 `backgroundWorker1`。</span><span class="sxs-lookup"><span data-stu-id="98093-165">In the **Properties**, window, select `backgroundWorker1`.</span></span> <span data-ttu-id="98093-166">設定<xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A>並<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性，以`true`。</span><span class="sxs-lookup"><span data-stu-id="98093-166">Set the <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span>  
  
2.  <span data-ttu-id="98093-167">宣告 `FibonacciCalculator` 表單中的兩個變數。</span><span class="sxs-lookup"><span data-stu-id="98093-167">Declare two variables in the `FibonacciCalculator` form.</span></span> <span data-ttu-id="98093-168">這些項目會用來追蹤進度。</span><span class="sxs-lookup"><span data-stu-id="98093-168">These will be used to track progress.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  <span data-ttu-id="98093-169">加入 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98093-169">Add an event handler for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="98093-170">在 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式中，更新<xref:System.Windows.Forms.ProgressBar>具有<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>屬性<xref:System.ComponentModel.ProgressChangedEventArgs>參數。</span><span class="sxs-lookup"><span data-stu-id="98093-170">In the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler, update the <xref:System.Windows.Forms.ProgressBar> with the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> property of the <xref:System.ComponentModel.ProgressChangedEventArgs> parameter.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a><span data-ttu-id="98093-171">若要實作支援取消作業</span><span class="sxs-lookup"><span data-stu-id="98093-171">To implement support for cancellation</span></span>  
  
1.  <span data-ttu-id="98093-172">在 `cancelAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，加入程式碼，取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="98093-172">In the `cancelAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that cancels the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  <span data-ttu-id="98093-173">`ComputeFibonacci` 方法中的下列程式碼片段會報告進度和支援取消。</span><span class="sxs-lookup"><span data-stu-id="98093-173">The following code fragments in the `ComputeFibonacci` method report progress and support cancellation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a><span data-ttu-id="98093-174">檢查點</span><span class="sxs-lookup"><span data-stu-id="98093-174">Checkpoint</span></span>  
 <span data-ttu-id="98093-175">此時，您可以編譯並執行 Fibonacci 計算機應用程式。</span><span class="sxs-lookup"><span data-stu-id="98093-175">At this point, you can compile and run the Fibonacci Calculator application.</span></span>  
  
#### <a name="to-test-your-project"></a><span data-ttu-id="98093-176">若要測試專案</span><span class="sxs-lookup"><span data-stu-id="98093-176">To test your project</span></span>  
  
-   <span data-ttu-id="98093-177">按 F5 編譯和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="98093-177">Press F5 to compile and run the application.</span></span>  
  
     <span data-ttu-id="98093-178">在背景執行計算時，您會看到<xref:System.Windows.Forms.ProgressBar>顯示計算完成的進度。</span><span class="sxs-lookup"><span data-stu-id="98093-178">While the calculation is running in the background, you will see the <xref:System.Windows.Forms.ProgressBar> displaying the progress of the calculation toward completion.</span></span> <span data-ttu-id="98093-179">您也可以取消暫止的作業。</span><span class="sxs-lookup"><span data-stu-id="98093-179">You can also cancel the pending operation.</span></span>  
  
     <span data-ttu-id="98093-180">對於小數字，計算應該非常快速，但是對於較大的數字，您應該會看到明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="98093-180">For small numbers, the calculation should be very fast, but for larger numbers, you should see a noticeable delay.</span></span> <span data-ttu-id="98093-181">如果您輸入的值為 30 或更大，您應該會看到幾秒鐘的延遲，取決於您的電腦速度。</span><span class="sxs-lookup"><span data-stu-id="98093-181">If you enter a value of 30 or greater, you should see a delay of several seconds, depending on the speed of your computer.</span></span> <span data-ttu-id="98093-182">對於大於 40 的值，可能需要數分鐘或數小時才能完成計算。</span><span class="sxs-lookup"><span data-stu-id="98093-182">For values greater than 40, it may take minutes or hours to finish the calculation.</span></span> <span data-ttu-id="98093-183">當計算機忙著計算大量 Fibonacci 數字時，請注意，您可以自由地到處移動表單、最小化、最大化，甚至是關閉表單。</span><span class="sxs-lookup"><span data-stu-id="98093-183">While the calculator is busy computing a large Fibonacci number, notice that you can freely move the form around, minimize, maximize, and even dismiss it.</span></span> <span data-ttu-id="98093-184">這是因為主要 UI 執行緒並沒有在等待計算完成。</span><span class="sxs-lookup"><span data-stu-id="98093-184">This is because the main UI thread is not waiting for the calculation to finish.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="98093-185">後續步驟</span><span class="sxs-lookup"><span data-stu-id="98093-185">Next Steps</span></span>  
 <span data-ttu-id="98093-186">既然您已實作使用的表單<xref:System.ComponentModel.BackgroundWorker>元件來執行計算，在背景中，您可以探索非同步作業的其他可能性：</span><span class="sxs-lookup"><span data-stu-id="98093-186">Now that you have implemented a form that uses a <xref:System.ComponentModel.BackgroundWorker> component to execute a computation in the background, you can explore other possibilities for asynchronous operations:</span></span>  
  
-   <span data-ttu-id="98093-187">使用多個<xref:System.ComponentModel.BackgroundWorker>數個同時作業的物件。</span><span class="sxs-lookup"><span data-stu-id="98093-187">Use multiple <xref:System.ComponentModel.BackgroundWorker> objects for several simultaneous operations.</span></span>  
  
-   <span data-ttu-id="98093-188">若要偵錯多執行緒的應用程式，請參閱[How to:使用執行緒視窗](/visualstudio/debugger/how-to-use-the-threads-window)。</span><span class="sxs-lookup"><span data-stu-id="98093-188">To debug your multithreaded application, see [How to: Use the Threads Window](/visualstudio/debugger/how-to-use-the-threads-window).</span></span>  
  
-   <span data-ttu-id="98093-189">實作您自己的元件，支援非同步程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="98093-189">Implement your own component that supports the asynchronous programming model.</span></span> <span data-ttu-id="98093-190">如需詳細資訊，請參閱[事件架構非同步模式概觀](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="98093-190">For more information, see [Event-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="98093-191">無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="98093-191">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="98093-192">請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="98093-192">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98093-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98093-193">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [<span data-ttu-id="98093-194">受控執行緒處理</span><span class="sxs-lookup"><span data-stu-id="98093-194">Managed Threading</span></span>](../../../../docs/standard/threading/index.md)
- [<span data-ttu-id="98093-195">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="98093-195">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
- [<span data-ttu-id="98093-196">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="98093-196">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="98093-197">如何：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="98093-197">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="98093-198">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="98093-198">Walkthrough: Running an Operation in the Background</span></span>](walkthrough-running-an-operation-in-the-background.md)
- [<span data-ttu-id="98093-199">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="98093-199">BackgroundWorker Component</span></span>](backgroundworker-component.md)
