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
ms.openlocfilehash: 60421d6ba634bd7b4107f1c9998fbbe158417c83
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423844"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a><span data-ttu-id="2330b-102">逐步解說：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="2330b-102">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>

<span data-ttu-id="2330b-103">如果您有會花費很長的時間才能完成，並停止回應或封鎖不想您的使用者介面 (UI)，您可以使用<xref:System.ComponentModel.BackgroundWorker>類別，以另一個執行緒上執行作業。</span><span class="sxs-lookup"><span data-stu-id="2330b-103">If you have an operation that will take a long time to complete, and you do not want your user interface (UI) to stop responding or to block, you can use the <xref:System.ComponentModel.BackgroundWorker> class to execute the operation on another thread.</span></span>

<span data-ttu-id="2330b-104">此逐步解說將說明如何使用<xref:System.ComponentModel.BackgroundWorker>類別執行耗費時間的計算，「 在背景中 」 時的使用者介面仍然能夠保持回應。</span><span class="sxs-lookup"><span data-stu-id="2330b-104">This walkthrough illustrates how to use the <xref:System.ComponentModel.BackgroundWorker> class to perform time-consuming computations "in the background," while the user interface remains responsive.</span></span>  <span data-ttu-id="2330b-105">當您進行逐步解說時，您必須讓應用程式以非同步方式計算 Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="2330b-105">When you are through, you will have an application that computes Fibonacci numbers asynchronously.</span></span> <span data-ttu-id="2330b-106">即使計算大量 Fibonacci 數字需要很長一段時間，主要 UI 執行緒不會受到此延遲的中斷，表單在計算期間仍然有回應。</span><span class="sxs-lookup"><span data-stu-id="2330b-106">Even though computing a large Fibonacci number can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculation.</span></span>

<span data-ttu-id="2330b-107">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="2330b-107">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="2330b-108">建立以 Windows 為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="2330b-108">Creating a Windows-based Application</span></span>

- <span data-ttu-id="2330b-109">建立<xref:System.ComponentModel.BackgroundWorker>在表單中</span><span class="sxs-lookup"><span data-stu-id="2330b-109">Creating a <xref:System.ComponentModel.BackgroundWorker> in Your Form</span></span>

- <span data-ttu-id="2330b-110">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="2330b-110">Adding Asynchronous Event Handlers</span></span>

- <span data-ttu-id="2330b-111">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="2330b-111">Adding Progress Reporting and Support for Cancellation</span></span>

<span data-ttu-id="2330b-112">如需在此範例中使用的程式碼的完整清單，請參閱[How to:實作使用背景作業的表單](how-to-implement-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="2330b-112">For a complete listing of the code used in this example, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>

## <a name="create-a-form-that-uses-a-background-operation"></a><span data-ttu-id="2330b-113">建立使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="2330b-113">Create a form that uses a background operation</span></span>

1. <span data-ttu-id="2330b-114">在 Visual Studio 中建立名為以 Windows 為基礎的應用程式專案`BackgroundWorkerExample`(**檔案** > **新增** > **專案** > **視覺化C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="2330b-114">In Visual Studio, create a Windows-based application project called `BackgroundWorkerExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="2330b-115">在 [方案總管]  中，以滑鼠右鍵按一下 [Form1]  ，然後從捷徑功能表選取 [重新命名]  。</span><span class="sxs-lookup"><span data-stu-id="2330b-115">In **Solution Explorer**, right-click **Form1** and select **Rename** from the shortcut menu.</span></span> <span data-ttu-id="2330b-116">將檔案名稱變更為 `FibonacciCalculator`。</span><span class="sxs-lookup"><span data-stu-id="2330b-116">Change the file name to `FibonacciCalculator`.</span></span> <span data-ttu-id="2330b-117">當系統詢問您是否要重新命名程式碼元素 '`Form1`' 的所有參考時，按一下 [是]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2330b-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`Form1`'.</span></span>

3. <span data-ttu-id="2330b-118">拖曳<xref:System.Windows.Forms.NumericUpDown>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="2330b-118">Drag a <xref:System.Windows.Forms.NumericUpDown> control from the **Toolbox** onto the form.</span></span> <span data-ttu-id="2330b-119">設定<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>屬性，以`1`並<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>屬性設`91`。</span><span class="sxs-lookup"><span data-stu-id="2330b-119">Set the <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> property to `1` and the <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> property to `91`.</span></span>

4. <span data-ttu-id="2330b-120">新增兩個<xref:System.Windows.Forms.Button>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="2330b-120">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span>

5. <span data-ttu-id="2330b-121">重新命名第一個<xref:System.Windows.Forms.Button>控制`startAsyncButton`並設定<xref:System.Windows.Forms.Control.Text%2A>屬性設`Start Async`。</span><span class="sxs-lookup"><span data-stu-id="2330b-121">Rename the first <xref:System.Windows.Forms.Button> control `startAsyncButton` and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Start Async`.</span></span> <span data-ttu-id="2330b-122">重新命名第二個<xref:System.Windows.Forms.Button>控制`cancelAsyncButton`，並將<xref:System.Windows.Forms.Control.Text%2A>屬性設`Cancel Async`。</span><span class="sxs-lookup"><span data-stu-id="2330b-122">Rename the second <xref:System.Windows.Forms.Button> control `cancelAsyncButton`, and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Cancel Async`.</span></span> <span data-ttu-id="2330b-123">設定其<xref:System.Windows.Forms.Control.Enabled%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="2330b-123">Set its <xref:System.Windows.Forms.Control.Enabled%2A> property to `false`.</span></span>

6. <span data-ttu-id="2330b-124">這兩個建立的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="2330b-124">Create an event handler for both of the <xref:System.Windows.Forms.Button> controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="2330b-125">如需詳細資訊，請參閱[如何：建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2330b-125">For details, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

7. <span data-ttu-id="2330b-126">拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至表單，並重新命名`resultLabel`。</span><span class="sxs-lookup"><span data-stu-id="2330b-126">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the form and rename it `resultLabel`.</span></span>

8. <span data-ttu-id="2330b-127">拖曳<xref:System.Windows.Forms.ProgressBar>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="2330b-127">Drag a <xref:System.Windows.Forms.ProgressBar> control from the **Toolbox** onto the form.</span></span>

## <a name="create-a-backgroundworker-with-the-designer"></a><span data-ttu-id="2330b-128">使用設計工具建立 BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="2330b-128">Create a BackgroundWorker with the Designer</span></span>

<span data-ttu-id="2330b-129">您可以建立<xref:System.ComponentModel.BackgroundWorker>非同步作業使用**Windows** **Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="2330b-129">You can create the <xref:System.ComponentModel.BackgroundWorker> for your asynchronous operation using the **Windows** **Forms Designer**.</span></span>

<span data-ttu-id="2330b-130">從**元件**索引標籤**工具箱**，拖曳<xref:System.ComponentModel.BackgroundWorker>拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="2330b-130">From the **Components** tab of the **Toolbox**, drag a <xref:System.ComponentModel.BackgroundWorker> onto the form.</span></span>

## <a name="add-asynchronous-event-handlers"></a><span data-ttu-id="2330b-131">新增非同步事件處理常式</span><span class="sxs-lookup"><span data-stu-id="2330b-131">Add asynchronous event handlers</span></span>

<span data-ttu-id="2330b-132">您現在已準備好新增事件處理常式<xref:System.ComponentModel.BackgroundWorker>元件的非同步事件。</span><span class="sxs-lookup"><span data-stu-id="2330b-132">You are now ready to add event handlers for the <xref:System.ComponentModel.BackgroundWorker> component's asynchronous events.</span></span> <span data-ttu-id="2330b-133">將會在背景執行的耗費時間作業 (計算 Fibonacci 數字)，會由其中一個事件處理常式呼叫。</span><span class="sxs-lookup"><span data-stu-id="2330b-133">The time-consuming operation that will run in the background, which computes Fibonacci numbers, is called by one of these event handlers.</span></span>

1. <span data-ttu-id="2330b-134">在 [**屬性**] 視窗中，使用<xref:System.ComponentModel.BackgroundWorker>元件保持選取，按一下 [**事件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2330b-134">In the **Properties** window, with the <xref:System.ComponentModel.BackgroundWorker> component still selected, click the **Events** button.</span></span> <span data-ttu-id="2330b-135">按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2330b-135">Double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span> <span data-ttu-id="2330b-136">如需如何使用事件處理常式的詳細資訊，請參閱[How to:建立使用設計工具的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2330b-136">For more information about how to use event handlers, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

2. <span data-ttu-id="2330b-137">在表單中，建立名為 `ComputeFibonacci` 的新方法。</span><span class="sxs-lookup"><span data-stu-id="2330b-137">Create a new method, called `ComputeFibonacci`, in your form.</span></span> <span data-ttu-id="2330b-138">這個方法會執行實際的工作，並且會在背景執行。</span><span class="sxs-lookup"><span data-stu-id="2330b-138">This method does the actual work, and it will run in the background.</span></span> <span data-ttu-id="2330b-139">此程式碼會示範 Fibonacci 演算法的遞迴實作，它非常沒有效率，對於較大的數字要耗費更長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="2330b-139">This code demonstrates the recursive implementation of the Fibonacci algorithm, which is notably inefficient, taking exponentially longer time to complete for larger numbers.</span></span> <span data-ttu-id="2330b-140">它在這裡是針對說明目的使用，以示範會導致應用程式長時間延遲的作業。</span><span class="sxs-lookup"><span data-stu-id="2330b-140">It is used here for illustrative purposes, to show an operation that can introduce long delays in your application.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]

3. <span data-ttu-id="2330b-141">在 <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式，將呼叫加入`ComputeFibonacci`方法。</span><span class="sxs-lookup"><span data-stu-id="2330b-141">In the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, add a call to the `ComputeFibonacci` method.</span></span> <span data-ttu-id="2330b-142">採取的第一個參數`ComputeFibonacci`從<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="2330b-142">Take the first parameter for `ComputeFibonacci` from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="2330b-143"><xref:System.ComponentModel.BackgroundWorker>和<xref:System.ComponentModel.DoWorkEventArgs>參數將稍後用於進度報告與取消支援。</span><span class="sxs-lookup"><span data-stu-id="2330b-143">The <xref:System.ComponentModel.BackgroundWorker> and <xref:System.ComponentModel.DoWorkEventArgs> parameters will be used later for progress reporting and cancellation support.</span></span> <span data-ttu-id="2330b-144">將指定的傳回值`ComputeFibonacci`要<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="2330b-144">Assign the return value from `ComputeFibonacci` to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="2330b-145">這個結果可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2330b-145">This result will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2330b-146"><xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式不會參考`backgroundWorker1`執行直接個體變數，因為這會結合此事件處理常式的特定執行個體<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="2330b-146">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler does not reference the `backgroundWorker1` instance variable directly, as this would couple this event handler to a specific instance of <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="2330b-147">相反地，參考<xref:System.ComponentModel.BackgroundWorker>，會引發這個事件從復原`sender`參數。</span><span class="sxs-lookup"><span data-stu-id="2330b-147">Instead, a reference to the <xref:System.ComponentModel.BackgroundWorker> that raised this event is recovered from the `sender` parameter.</span></span> <span data-ttu-id="2330b-148">當表單裝載一個以上時，這點很重要<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="2330b-148">This is important when the form hosts more than one <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="2330b-149">務必也沒有任何使用者介面中操作物件您<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2330b-149">It is also important not to manipulate any user-interface objects in your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="2330b-150">相反地，透過使用者介面通訊<xref:System.ComponentModel.BackgroundWorker>事件。</span><span class="sxs-lookup"><span data-stu-id="2330b-150">Instead, communicate to the user interface through the <xref:System.ComponentModel.BackgroundWorker> events.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]

4. <span data-ttu-id="2330b-151">在 `startAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，將會啟動非同步作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2330b-151">In the `startAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that starts the asynchronous operation.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]

5. <span data-ttu-id="2330b-152">在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式，指派的計算結果`resultLabel`控制項。</span><span class="sxs-lookup"><span data-stu-id="2330b-152">In the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler, assign the result of the calculation to the `resultLabel` control.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]

## <a name="adding-progress-reporting-and-support-for-cancellation"></a><span data-ttu-id="2330b-153">新增進度報告和支援取消作業</span><span class="sxs-lookup"><span data-stu-id="2330b-153">Adding Progress Reporting and Support for Cancellation</span></span>

<span data-ttu-id="2330b-154">對於需要長時間的非同步作業，通常會想要對使用者報告進度，並且允許使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="2330b-154">For asynchronous operations that will take a long time, it is often desirable to report progress to the user and to allow the user to cancel the operation.</span></span> <span data-ttu-id="2330b-155"><xref:System.ComponentModel.BackgroundWorker>類別會提供事件，可讓您的背景作業進行時公佈進度。</span><span class="sxs-lookup"><span data-stu-id="2330b-155">The <xref:System.ComponentModel.BackgroundWorker> class provides an event that allows you to post progress as your background operation proceeds.</span></span> <span data-ttu-id="2330b-156">它也提供旗標，可讓您的背景工作角色程式碼，來偵測呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>並且自行中斷。</span><span class="sxs-lookup"><span data-stu-id="2330b-156">It also provides a flag that allows your worker code to detect a call to <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> and interrupt itself.</span></span>

### <a name="implement-progress-reporting"></a><span data-ttu-id="2330b-157">實作進度報告</span><span class="sxs-lookup"><span data-stu-id="2330b-157">Implement progress reporting</span></span>

1. <span data-ttu-id="2330b-158">在 [屬性]  視窗中，選取 `backgroundWorker1`。</span><span class="sxs-lookup"><span data-stu-id="2330b-158">In the **Properties**, window, select `backgroundWorker1`.</span></span> <span data-ttu-id="2330b-159">設定<xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A>並<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性，以`true`。</span><span class="sxs-lookup"><span data-stu-id="2330b-159">Set the <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span>

2. <span data-ttu-id="2330b-160">宣告 `FibonacciCalculator` 表單中的兩個變數。</span><span class="sxs-lookup"><span data-stu-id="2330b-160">Declare two variables in the `FibonacciCalculator` form.</span></span> <span data-ttu-id="2330b-161">這些項目會用來追蹤進度。</span><span class="sxs-lookup"><span data-stu-id="2330b-161">These will be used to track progress.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]

3. <span data-ttu-id="2330b-162">加入 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2330b-162">Add an event handler for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="2330b-163">在 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式中，更新<xref:System.Windows.Forms.ProgressBar>具有<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>屬性<xref:System.ComponentModel.ProgressChangedEventArgs>參數。</span><span class="sxs-lookup"><span data-stu-id="2330b-163">In the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler, update the <xref:System.Windows.Forms.ProgressBar> with the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> property of the <xref:System.ComponentModel.ProgressChangedEventArgs> parameter.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]

### <a name="implement-support-for-cancellation"></a><span data-ttu-id="2330b-164">實作支援取消作業</span><span class="sxs-lookup"><span data-stu-id="2330b-164">Implement support for cancellation</span></span>

1. <span data-ttu-id="2330b-165">在 `cancelAsyncButton`控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，加入程式碼，取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="2330b-165">In the `cancelAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that cancels the asynchronous operation.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]

2. <span data-ttu-id="2330b-166">`ComputeFibonacci` 方法中的下列程式碼片段會報告進度和支援取消。</span><span class="sxs-lookup"><span data-stu-id="2330b-166">The following code fragments in the `ComputeFibonacci` method report progress and support cancellation.</span></span>

     [!code-cpp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]

## <a name="checkpoint"></a><span data-ttu-id="2330b-167">檢查點</span><span class="sxs-lookup"><span data-stu-id="2330b-167">Checkpoint</span></span>

<span data-ttu-id="2330b-168">此時，您可以編譯並執行 Fibonacci 計算機應用程式。</span><span class="sxs-lookup"><span data-stu-id="2330b-168">At this point, you can compile and run the Fibonacci Calculator application.</span></span>

<span data-ttu-id="2330b-169">按下**F5**編譯和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2330b-169">Press **F5** to compile and run the application.</span></span>

<span data-ttu-id="2330b-170">在背景執行計算時，您會看到<xref:System.Windows.Forms.ProgressBar>顯示計算完成的進度。</span><span class="sxs-lookup"><span data-stu-id="2330b-170">While the calculation is running in the background, you will see the <xref:System.Windows.Forms.ProgressBar> displaying the progress of the calculation toward completion.</span></span> <span data-ttu-id="2330b-171">您也可以取消暫止的作業。</span><span class="sxs-lookup"><span data-stu-id="2330b-171">You can also cancel the pending operation.</span></span>

<span data-ttu-id="2330b-172">對於小數字，計算應該非常快速，但是對於較大的數字，您應該會看到明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="2330b-172">For small numbers, the calculation should be very fast, but for larger numbers, you should see a noticeable delay.</span></span> <span data-ttu-id="2330b-173">如果您輸入的值為 30 或更大，您應該會看到幾秒鐘的延遲，取決於您的電腦速度。</span><span class="sxs-lookup"><span data-stu-id="2330b-173">If you enter a value of 30 or greater, you should see a delay of several seconds, depending on the speed of your computer.</span></span> <span data-ttu-id="2330b-174">對於大於 40 的值，可能需要數分鐘或數小時才能完成計算。</span><span class="sxs-lookup"><span data-stu-id="2330b-174">For values greater than 40, it may take minutes or hours to finish the calculation.</span></span> <span data-ttu-id="2330b-175">當計算機忙著計算大量 Fibonacci 數字時，請注意，您可以自由地到處移動表單、最小化、最大化，甚至是關閉表單。</span><span class="sxs-lookup"><span data-stu-id="2330b-175">While the calculator is busy computing a large Fibonacci number, notice that you can freely move the form around, minimize, maximize, and even dismiss it.</span></span> <span data-ttu-id="2330b-176">這是因為主要 UI 執行緒並沒有在等待計算完成。</span><span class="sxs-lookup"><span data-stu-id="2330b-176">This is because the main UI thread is not waiting for the calculation to finish.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2330b-177">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2330b-177">Next steps</span></span>

<span data-ttu-id="2330b-178">既然您已實作使用的表單<xref:System.ComponentModel.BackgroundWorker>元件來執行計算，在背景中，您可以探索非同步作業的其他可能性：</span><span class="sxs-lookup"><span data-stu-id="2330b-178">Now that you have implemented a form that uses a <xref:System.ComponentModel.BackgroundWorker> component to execute a computation in the background, you can explore other possibilities for asynchronous operations:</span></span>

- <span data-ttu-id="2330b-179">使用多個<xref:System.ComponentModel.BackgroundWorker>數個同時作業的物件。</span><span class="sxs-lookup"><span data-stu-id="2330b-179">Use multiple <xref:System.ComponentModel.BackgroundWorker> objects for several simultaneous operations.</span></span>

- <span data-ttu-id="2330b-180">若要偵錯多執行緒的應用程式，請參閱[How to:使用執行緒視窗](/visualstudio/debugger/how-to-use-the-threads-window)。</span><span class="sxs-lookup"><span data-stu-id="2330b-180">To debug your multithreaded application, see [How to: Use the Threads Window](/visualstudio/debugger/how-to-use-the-threads-window).</span></span>

- <span data-ttu-id="2330b-181">實作您自己的元件，支援非同步程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="2330b-181">Implement your own component that supports the asynchronous programming model.</span></span> <span data-ttu-id="2330b-182">如需詳細資訊，請參閱[事件架構非同步模式概觀](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2330b-182">For more information, see [Event-based Asynchronous Pattern Overview](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

    > [!CAUTION]
    > <span data-ttu-id="2330b-183">無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2330b-183">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="2330b-184">請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="2330b-184">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>

## <a name="see-also"></a><span data-ttu-id="2330b-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2330b-185">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [<span data-ttu-id="2330b-186">受控執行緒處理</span><span class="sxs-lookup"><span data-stu-id="2330b-186">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="2330b-187">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="2330b-187">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
- [<span data-ttu-id="2330b-188">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="2330b-188">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="2330b-189">如何：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="2330b-189">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="2330b-190">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="2330b-190">Walkthrough: Running an Operation in the Background</span></span>](walkthrough-running-an-operation-in-the-background.md)
- [<span data-ttu-id="2330b-191">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="2330b-191">BackgroundWorker Component</span></span>](backgroundworker-component.md)
