---
title: 如何：取消資料流程區塊
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eece4992deecbf30299d6e9e96fa8c2faf16d3ab
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="1bc26-102">如何：取消資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="1bc26-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="1bc26-103">本文件示範如何在您的應用程式中啟用取消作業。</span><span class="sxs-lookup"><span data-stu-id="1bc26-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="1bc26-104">此範例會使用 Windows Forms 來顯示工作項目在資料流程管線中的作用位置，以及取消作業的效果。</span><span class="sxs-lookup"><span data-stu-id="1bc26-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="1bc26-105">若要建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="1bc26-105">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="1bc26-106">建立 C# 或 Visual Basic **Windows Forms 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="1bc26-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="1bc26-107">在下列步驟中，專案會命名為 `CancellationWinForms`。</span><span class="sxs-lookup"><span data-stu-id="1bc26-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="1bc26-108">在主要表單 Form1.cs (在 Visual Basic 中為 Form1.vb) 的表單設計工具上，新增 <xref:System.Windows.Forms.ToolStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bc26-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="1bc26-109">將 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bc26-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="1bc26-110">將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> 並將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為**新增工作項目**。</span><span class="sxs-lookup"><span data-stu-id="1bc26-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="1bc26-111">將第二個 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bc26-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="1bc26-112">將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 **Cancel**，然後將 <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> 屬性設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="1bc26-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="1bc26-113">將四個 <xref:System.Windows.Forms.ToolStripProgressBar> 物件加入 <xref:System.Windows.Forms.ToolStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bc26-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="1bc26-114">建立資料流程管線</span><span class="sxs-lookup"><span data-stu-id="1bc26-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="1bc26-115">本節說明如何建立資料流程管線，以處理工作項目並更新進度列。</span><span class="sxs-lookup"><span data-stu-id="1bc26-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="1bc26-116">建立資料流程管線</span><span class="sxs-lookup"><span data-stu-id="1bc26-116">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="1bc26-117">在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="1bc26-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="1bc26-118">確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)。</span><span class="sxs-lookup"><span data-stu-id="1bc26-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="1bc26-119">將 `WorkItem` 類別新增為 `Form1` 類別的內部類別。</span><span class="sxs-lookup"><span data-stu-id="1bc26-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="1bc26-120">將下列資料成員新增至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="1bc26-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="1bc26-121">將下列 `CreatePipeline` 方法新增至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="1bc26-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="1bc26-122">由於 `incrementProgress` 和 `decrementProgress`資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="1bc26-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="1bc26-123">為了要完成這項作業，在建構時這些物件會提供 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，而且其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性會設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1bc26-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1bc26-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。</span><span class="sxs-lookup"><span data-stu-id="1bc26-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="1bc26-125">由於 `Form1` 建構函式是從使用者介面執行緒呼叫，因此 `incrementProgress` 和 `decrementProgress` 資料流程區塊的動作也會在使用者介面執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="1bc26-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="1bc26-126">此範例在它建構管線成員時會設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1bc26-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="1bc26-127">因為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性會永久取消資料流程區塊執行，所以必須在使用者取消此作業，而後想要將更多工作項目新增至管線之後，重新建立整個管線。</span><span class="sxs-lookup"><span data-stu-id="1bc26-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="1bc26-128">如需示範取消資料流程區塊的替代方式，以便在取消作業後執行其他工作的範例，請參閱[逐步解說︰在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc26-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="1bc26-129">將資料流程管線連接至使用者介面</span><span class="sxs-lookup"><span data-stu-id="1bc26-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="1bc26-130">本節說明如何將資料流程管線連接至使用者介面。</span><span class="sxs-lookup"><span data-stu-id="1bc26-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="1bc26-131">建立管線以及將工作項目新增至管線都是由 [新增工作項目] 按鈕的事件處理常式所控制。</span><span class="sxs-lookup"><span data-stu-id="1bc26-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="1bc26-132">取消作業是由 [取消] 按鈕所起始。</span><span class="sxs-lookup"><span data-stu-id="1bc26-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="1bc26-133">當使用者按一下任一個按鈕時，會以非同步方式起始適當的動作。</span><span class="sxs-lookup"><span data-stu-id="1bc26-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="1bc26-134">將資料流程管線連接至使用者介面</span><span class="sxs-lookup"><span data-stu-id="1bc26-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="1bc26-135">在主要表單的表單設計工具上，為 [新增工作項目] 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1bc26-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="1bc26-136">實作 [新增工作項目] 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="1bc26-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="1bc26-137">在主要表單的表單設計工具上，為 [取消] 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1bc26-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="1bc26-138">實作 [取消] 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1bc26-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1bc26-139">範例</span><span class="sxs-lookup"><span data-stu-id="1bc26-139">Example</span></span>  
 <span data-ttu-id="1bc26-140">下列範例顯示 Form1.cs (在 Visual Basic 中為 Form1.vb) 的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="1bc26-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="1bc26-141">下圖顯示執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bc26-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="1bc26-142">![Windows Forms 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="1bc26-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="1bc26-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc26-143">See Also</span></span>  
 [<span data-ttu-id="1bc26-144">資料流程</span><span class="sxs-lookup"><span data-stu-id="1bc26-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
