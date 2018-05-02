---
title: 如何：在資料流程區塊中指定工作排程器
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 15b1168c34a22394424f250e8ab1887ec8ee1a5e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="17459-102">如何：在資料流程區塊中指定工作排程器</span><span class="sxs-lookup"><span data-stu-id="17459-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="17459-103">此文件將示範當您在應用程式中使用資料流程時，如何與特定工作排程器產生關聯。</span><span class="sxs-lookup"><span data-stu-id="17459-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="17459-104">這個範例會使用 Windows Form 應用程式中的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> 類別顯示讀取器工作何時為使用中，以及寫入器工作何時為使用中。</span><span class="sxs-lookup"><span data-stu-id="17459-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="17459-105">另外還會使用 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法讓資料流程區塊在使用者介面執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="17459-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="17459-106">若要建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="17459-106">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="17459-107">建立 Visual C# 或 Visual Basic **Windows Forms 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="17459-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="17459-108">在下列步驟中，專案會命名為 `WriterReadersWinForms`。</span><span class="sxs-lookup"><span data-stu-id="17459-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2.  <span data-ttu-id="17459-109">在主要表單 Form1.cs (在 Visual Basic 中為 Form1.vb) 的表單設計工具上，新增四個 <xref:System.Windows.Forms.CheckBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="17459-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="17459-110">將 `checkBox1` 的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為**讀取器 1**、`checkBox2` 的該屬性設為**讀取器 2**、`checkBox3` 的該屬性設為**讀取器 3**，以及 `checkBox4` 的該屬性設為**寫入器**。</span><span class="sxs-lookup"><span data-stu-id="17459-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="17459-111">將每個控制項的 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="17459-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3.  <span data-ttu-id="17459-112">將 <xref:System.Windows.Forms.Timer> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="17459-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="17459-113">將 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性設定為 `2500`。</span><span class="sxs-lookup"><span data-stu-id="17459-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="17459-114">加入資料流程功能</span><span class="sxs-lookup"><span data-stu-id="17459-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="17459-115">本節將說明如何建立參與應用程式的資料流程區塊，以及如何將每個區塊與工作排程器產生關聯。</span><span class="sxs-lookup"><span data-stu-id="17459-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="17459-116">若要將資料流程功能加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="17459-116">To Add Dataflow Functionality to the Application</span></span>  
  
1.  <span data-ttu-id="17459-117">在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="17459-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="17459-118">確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)。</span><span class="sxs-lookup"><span data-stu-id="17459-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="17459-119">將 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 資料成員加入至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="17459-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="17459-120">在 `Form1` 建構函式中，於呼叫 `InitializeComponent` 之後建立 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，用於切換 <xref:System.Windows.Forms.CheckBox> 物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="17459-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="17459-121">在 `Form1` 建構函式中，建立 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件和四個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，每個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件都有一個 <xref:System.Windows.Forms.CheckBox> 物件。</span><span class="sxs-lookup"><span data-stu-id="17459-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="17459-122">針對每個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件指定 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，並將其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性設定為讀取器的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> 屬性，以及寫入器的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="17459-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  <span data-ttu-id="17459-123">在 `Form1` 建構函式中，啟動 <xref:System.Windows.Forms.Timer> 物件。</span><span class="sxs-lookup"><span data-stu-id="17459-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  <span data-ttu-id="17459-124">在主要表單的表單設計工具上，為計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="17459-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8.  <span data-ttu-id="17459-125">實作計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件。</span><span class="sxs-lookup"><span data-stu-id="17459-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="17459-126">由於 `toggleCheckBox` 資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="17459-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="17459-127">為了要完成這項作業，在建構時這個物件會提供 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，而且其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性會設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="17459-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17459-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。</span><span class="sxs-lookup"><span data-stu-id="17459-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="17459-129">由於 `Form1` 建構函式是從使用者介面執行緒呼叫，因此 `toggleCheckBox` 資料流程區塊的動作也會在使用者介面執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="17459-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="17459-130">這個範例也會使用 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 類別讓某些資料流程區塊同時執行，以及讓另一個資料流程區塊相對於同一個 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件上執行的所有資料流程區塊獨佔執行。</span><span class="sxs-lookup"><span data-stu-id="17459-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="17459-131">當多個資料流程區塊共用某一項資源，而其中有些區塊需要獨佔存取該資源時，這項技術會很有用，因為它能讓您不必手動同步處理該資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="17459-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="17459-132">不必手動同步處理可讓程式碼更有效率。</span><span class="sxs-lookup"><span data-stu-id="17459-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17459-133">範例</span><span class="sxs-lookup"><span data-stu-id="17459-133">Example</span></span>  
 <span data-ttu-id="17459-134">下列範例顯示 Form1.cs (在 Visual Basic 中為 Form1.vb) 的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="17459-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="17459-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="17459-135">See Also</span></span>  
 [<span data-ttu-id="17459-136">資料流程</span><span class="sxs-lookup"><span data-stu-id="17459-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
