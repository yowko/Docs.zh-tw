---
title: "如何：寫入訊息至資料流程區塊及讀取資料流程區塊中的訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf609a8c350a44fc802cce0ec10693431bbf4f42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a><span data-ttu-id="aa2f5-102">如何：寫入訊息至資料流程區塊及讀取資料流程區塊中的訊息</span><span class="sxs-lookup"><span data-stu-id="aa2f5-102">How to: Write Messages to and Read Messages from a Dataflow Block</span></span>
<span data-ttu-id="aa2f5-103">本文件將說明如何使用 TPL 資料流程程式庫，在資料流程區塊中寫物和讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-103">This document describes how to use the TPL Dataflow Library to write messages to and read messages from a dataflow block.</span></span> <span data-ttu-id="aa2f5-104">TPL 資料流程程式庫提供了在資料流程區塊中寫入和讀取訊息的同步和非同步方法。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-104">The TPL Dataflow Library provides both synchronous and asynchronous methods for writing messages to and reading messages from a dataflow block.</span></span> <span data-ttu-id="aa2f5-105">本文件將使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-105">This document uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="aa2f5-106"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別會緩衝訊息，並且同時做為訊息來源和訊息目標。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-106">The <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class buffers messages and behaves as both a message source and as a message target.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="aa2f5-107">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-107">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="aa2f5-108">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-108">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a><span data-ttu-id="aa2f5-109">在資料流程區塊中同步寫入和讀取</span><span class="sxs-lookup"><span data-stu-id="aa2f5-109">Writing to and Reading from a Dataflow Block Synchronously</span></span>  
 <span data-ttu-id="aa2f5-110">下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 資料流程區塊，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法從同一個物件讀取。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-110">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method to write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dataflow block and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method to read from the same object.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 <span data-ttu-id="aa2f5-111">您也可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從資料流程區塊中讀取，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-111">You can also use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read from a dataflow block, as shown in the following example.</span></span> <span data-ttu-id="aa2f5-112"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不會封鎖目前執行緒，當您偶爾輪詢資料時很有用。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-112">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method does not block the current thread and is useful when you occasionally poll for data.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <span data-ttu-id="aa2f5-113">由於 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法會同步執行，因此先前範例中的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件會在第二個迴圈讀取資料前接收所有資料。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-113">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method acts synchronously, the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in the previous examples receives all data before the second loop reads data.</span></span> <span data-ttu-id="aa2f5-114">下列範例會使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 擴充第一個範例，以並行方式讀取和寫入訊息區塊。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-114">The following example extends the first example by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> to read from and write to the message block concurrently.</span></span> <span data-ttu-id="aa2f5-115">由於 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 會以並行方式執行動作，因此值不會依照特定順序寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件中。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-115">Because <xref:System.Threading.Tasks.Parallel.Invoke%2A> performs actions concurrently, the values are not written to the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in any specific order.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a><span data-ttu-id="aa2f5-116">在資料流程區塊中非同步寫入和讀取</span><span class="sxs-lookup"><span data-stu-id="aa2f5-116">Writing to and Reading from a Dataflow Block Asynchronously</span></span>  
 <span data-ttu-id="aa2f5-117">下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法以非同步方式寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法以非同步方式從同一個物件讀取。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-117">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method to asynchronously write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method to asynchronously read from the same object.</span></span> <span data-ttu-id="aa2f5-118">這個範例會使用 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 運算子 (在 Visual Basic 中為 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) 以非同步方式對目標區塊傳送和讀取資料。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-118">This example uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously send data to and read data from the target block.</span></span> <span data-ttu-id="aa2f5-119">當您必須讓資料流程區塊延後訊息時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-119">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method is useful when you must enable a dataflow block to postpone messages.</span></span> <span data-ttu-id="aa2f5-120">當您想要在有資料可用時處理資料時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-120">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method is useful when you want to act on data when that data becomes available.</span></span> <span data-ttu-id="aa2f5-121">如需訊息如何在訊息區塊之間傳播的詳細資訊，請參閱[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)中的＜訊息傳遞＞一節。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-121">For more information about how messages propagate among message blocks, see the section Message Passing in [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a><span data-ttu-id="aa2f5-122">完整範例</span><span class="sxs-lookup"><span data-stu-id="aa2f5-122">A Complete Example</span></span>  
 <span data-ttu-id="aa2f5-123">下列範例將示範本文件的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-123">The following example shows the complete code for this document.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa2f5-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="aa2f5-124">Compiling the Code</span></span>  
 <span data-ttu-id="aa2f5-125">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowReadWrite.cs` 的檔案中 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為 `DataflowReadWrite.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-125">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReadWrite.cs` (`DataflowReadWrite.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="aa2f5-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**</span><span class="sxs-lookup"><span data-stu-id="aa2f5-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="aa2f5-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**</span><span class="sxs-lookup"><span data-stu-id="aa2f5-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aa2f5-128">後續步驟</span><span class="sxs-lookup"><span data-stu-id="aa2f5-128">Next Steps</span></span>  
 <span data-ttu-id="aa2f5-129">這個範例將示範如何直接讀取和寫入訊息區塊。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-129">This example shows how to read from and write to a message block directly.</span></span> <span data-ttu-id="aa2f5-130">您也可以連接資料流程區塊組成「管線」，這是資料流程區塊的線性序列，或是組成「網路」，這是資料流程區塊的圖形。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-130">You can also connect dataflow blocks to form *pipelines*, which are linear sequences of dataflow blocks, or *networks*, which are graphs of dataflow blocks.</span></span> <span data-ttu-id="aa2f5-131">在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-131">In a pipeline or network, sources asynchronously propagate data to targets as that data becomes available.</span></span> <span data-ttu-id="aa2f5-132">如需建立基本資料流程管線的範例，請參閱[逐步解說：建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-132">For an example that creates a basic dataflow pipeline, see [Walkthrough: Creating a Dataflow Pipeline](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md).</span></span> <span data-ttu-id="aa2f5-133">如需建立更複雜的資料流程網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="aa2f5-133">For an example that creates a more complex dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2f5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa2f5-134">See Also</span></span>  
 [<span data-ttu-id="aa2f5-135">資料流程</span><span class="sxs-lookup"><span data-stu-id="aa2f5-135">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
