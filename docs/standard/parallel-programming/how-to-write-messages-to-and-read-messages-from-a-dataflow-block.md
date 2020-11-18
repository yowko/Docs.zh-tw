---
title: 如何：寫入和讀取資料流程區塊中的訊息
ms.date: 09/10/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: be0e78989105cc59bd041ceb8c6f31073a702f83
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820783"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a><span data-ttu-id="b3fa0-102">如何：寫入和讀取資料流程區塊中的訊息</span><span class="sxs-lookup"><span data-stu-id="b3fa0-102">How to: Write and read messages from a Dataflow block</span></span>

<span data-ttu-id="b3fa0-103">本文說明如何使用工作平行程式庫 (TPL) 資料流程程式庫，將訊息寫入至資料流程區塊並從中讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-103">This article describes how to use the Task Parallel Library (TPL) Dataflow Library to write messages to and read messages from a dataflow block.</span></span> <span data-ttu-id="b3fa0-104">TPL 資料流程程式庫提供了在資料流程區塊中寫入和讀取訊息的同步和非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-104">The TPL Dataflow Library provides both synchronous and asynchronous methods for writing messages to and reading messages from a dataflow block.</span></span> <span data-ttu-id="b3fa0-105">本文說明如何使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-105">This article shows how to uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="b3fa0-106"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601>類別會緩衝訊息，並以訊息來源和訊息目標的形式來運作。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-106">The <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class buffers messages and behaves as both a message source and a message target.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a><span data-ttu-id="b3fa0-107">以同步方式寫入和讀取</span><span class="sxs-lookup"><span data-stu-id="b3fa0-107">Writing and reading synchronously</span></span>

<span data-ttu-id="b3fa0-108">下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 資料流程區塊，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法從同一個物件讀取。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-108">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method to write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dataflow block and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method to read from the same object.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

<span data-ttu-id="b3fa0-109">您也可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從資料流程區塊中讀取，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-109">You can also use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read from a dataflow block, as shown in the following example.</span></span> <span data-ttu-id="b3fa0-110"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不會封鎖目前執行緒，當您偶爾輪詢資料時很有用。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-110">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method does not block the current thread and is useful when you occasionally poll for data.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

<span data-ttu-id="b3fa0-111">由於 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法會同步執行，因此先前範例中的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件會在第二個迴圈讀取資料前接收所有資料。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-111">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method acts synchronously, the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in the previous examples receives all data before the second loop reads data.</span></span> <span data-ttu-id="b3fa0-112">下列範例會使用 <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> 擴充第一個範例，以並行方式讀取和寫入訊息區塊。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-112">The following example extends the first example by using <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> to read from and write to the message block concurrently.</span></span> <span data-ttu-id="b3fa0-113">由於 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會以並行方式執行動作，因此值不會依照特定順序寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件中。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-113">Because <xref:System.Threading.Tasks.Task.WhenAll%2A> performs actions concurrently, the values are not written to the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in any specific order.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a><span data-ttu-id="b3fa0-114">以非同步方式撰寫和讀取</span><span class="sxs-lookup"><span data-stu-id="b3fa0-114">Writing and reading asynchronously</span></span>

<span data-ttu-id="b3fa0-115">下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法以非同步方式寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法以非同步方式從同一個物件讀取。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-115">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method to asynchronously write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method to asynchronously read from the same object.</span></span> <span data-ttu-id="b3fa0-116">這個範例會使用 [async](../../csharp/language-reference/keywords/async.md) 和 [await](../../csharp/language-reference/operators/await.md) 運算子 (在 Visual Basic 中為 [Async](../../visual-basic/language-reference/modifiers/async.md) 和 [Await](../../visual-basic/language-reference/operators/await-operator.md)) 以非同步方式對目標區塊傳送和讀取資料。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-116">This example uses the [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) operators ([Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously send data to and read data from the target block.</span></span> <span data-ttu-id="b3fa0-117">當您必須讓資料流程區塊延後訊息時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-117">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method is useful when you must enable a dataflow block to postpone messages.</span></span> <span data-ttu-id="b3fa0-118">當您想要在有資料可用時處理資料時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-118">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method is useful when you want to act on data when that data becomes available.</span></span> <span data-ttu-id="b3fa0-119">如需訊息如何在訊息區塊之間傳播的詳細資訊，請參閱[資料流程](dataflow-task-parallel-library.md)中的＜訊息傳遞＞一節。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-119">For more information about how messages propagate among message blocks, see the section Message Passing in [Dataflow](dataflow-task-parallel-library.md).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a><span data-ttu-id="b3fa0-120">完整範例</span><span class="sxs-lookup"><span data-stu-id="b3fa0-120">A complete example</span></span>

<span data-ttu-id="b3fa0-121">下列範例顯示本文的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-121">The following example shows all of the code for this article.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a><span data-ttu-id="b3fa0-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b3fa0-122">Next steps</span></span>

<span data-ttu-id="b3fa0-123">這個範例將示範如何直接讀取和寫入訊息區塊。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-123">This example shows how to read from and write to a message block directly.</span></span> <span data-ttu-id="b3fa0-124">您也可以連接資料流程區塊組成「管線」，這是資料流程區塊的線性序列，或是組成「網路」，這是資料流程區塊的圖形。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-124">You can also connect dataflow blocks to form *pipelines*, which are linear sequences of dataflow blocks, or *networks*, which are graphs of dataflow blocks.</span></span> <span data-ttu-id="b3fa0-125">在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-125">In a pipeline or network, sources asynchronously propagate data to targets as that data becomes available.</span></span> <span data-ttu-id="b3fa0-126">如需建立基本資料流程管線的範例，請參閱[逐步解說：建立資料流程管線](walkthrough-creating-a-dataflow-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-126">For an example that creates a basic dataflow pipeline, see [Walkthrough: Creating a Dataflow Pipeline](walkthrough-creating-a-dataflow-pipeline.md).</span></span> <span data-ttu-id="b3fa0-127">如需建立更複雜的資料流程網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b3fa0-127">For an example that creates a more complex dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3fa0-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3fa0-128">See also</span></span>

- [<span data-ttu-id="b3fa0-129">資料流程 (工作平行程式庫)</span><span class="sxs-lookup"><span data-stu-id="b3fa0-129">Dataflow (Task Parallel Library)</span></span>](dataflow-task-parallel-library.md)
