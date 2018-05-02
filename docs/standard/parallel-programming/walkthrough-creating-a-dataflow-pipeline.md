---
title: 逐步解說：建立資料流程管線
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e6471de1a6231f114f6967bb6f777a8dc4d39b82
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a><span data-ttu-id="d6e1a-102">逐步解說：建立資料流程管線</span><span class="sxs-lookup"><span data-stu-id="d6e1a-102">Walkthrough: Creating a Dataflow Pipeline</span></span>
<span data-ttu-id="d6e1a-103">雖然您可以使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> 方法從來源區塊接收訊息，但是也可以將訊息區連接起來，形成「資料流程管線」。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-103">Although you can use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> methods to receive messages from source blocks, you can also connect message blocks to form a *dataflow pipeline*.</span></span> <span data-ttu-id="d6e1a-104">資料流程管線是一系列的元件，或稱為「資料流程區塊」，各個元件分別執行一項特定工作，以便共同完成整體目標。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-104">A dataflow pipeline is a series of components, or *dataflow blocks*, each of which performs a specific task that contributes to a larger goal.</span></span> <span data-ttu-id="d6e1a-105">資料流程管線中的每個資料流程區塊會在收到來自其他資料流程區塊的訊息時，開始執行工作。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-105">Every dataflow block in a dataflow pipeline performs work when it receives a message from another dataflow block.</span></span> <span data-ttu-id="d6e1a-106">以汽車製造的裝配線做比喻。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-106">An analogy to this is an assembly line for automobile manufacturing.</span></span> <span data-ttu-id="d6e1a-107">當每輛汽車通過裝配線時，某一站會組裝車架，下一站會安裝引擎，以此類推。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-107">As each vehicle passes through the assembly line, one station assembles the frame, the next one installs the engine, and so on.</span></span> <span data-ttu-id="d6e1a-108">由於裝配線能夠同時組裝多輛車，因此裝配線的生產量會優於一次將一輛車從頭到尾組裝完成的生產量。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-108">Because an assembly line enables multiple vehicles to be assembled at the same time, it provides better throughput than assembling complete vehicles one at a time.</span></span>

 <span data-ttu-id="d6e1a-109">本文示範資料流程管線，該管線會從網站下載《The Iliad of Homer》一書，並搜尋拼字順序相反的單字，例如 doom 與 mood。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-109">This document demonstrates a dataflow pipeline that downloads the book *The Iliad of Homer* from a website and searches the text to match individual words with words that reverse the first word's characters.</span></span> <span data-ttu-id="d6e1a-110">本文件中資料流程管線是由下列步驟形成：</span><span class="sxs-lookup"><span data-stu-id="d6e1a-110">The formation of the dataflow pipeline in this document consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="d6e1a-111">建立參與管線的資料流程區塊。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-111">Create the dataflow blocks that participate in the pipeline.</span></span>  
  
2.  <span data-ttu-id="d6e1a-112">將每個資料流程區塊連接到管線中的下一個區塊。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-112">Connect each dataflow block to the next block in the pipeline.</span></span> <span data-ttu-id="d6e1a-113">每個區塊都會收到管線中前一個區塊的輸出做為輸入。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-113">Each block receives as input the output of the previous block in the pipeline.</span></span>  
  
3.  <span data-ttu-id="d6e1a-114">對每個資料流程區塊建立接續工作，在前一個區塊完成之後將下一個區塊設定為已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-114">For each dataflow block, create a continuation task that sets the next block to the completed state after the previous block finishes.</span></span>  
  
4.  <span data-ttu-id="d6e1a-115">將資料公佈至管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-115">Post data to the head of the pipeline.</span></span>  
  
5.  <span data-ttu-id="d6e1a-116">將管線的開頭標示為已完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-116">Mark the head of the pipeline as completed.</span></span>  
  
6.  <span data-ttu-id="d6e1a-117">等候管線完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-117">Wait for the pipeline to complete all work.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d6e1a-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="d6e1a-118">Prerequisites</span></span>  
 <span data-ttu-id="d6e1a-119">在開始進行這個逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-119">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  
  
## <a name="creating-a-console-application"></a><span data-ttu-id="d6e1a-120">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d6e1a-120">Creating a Console Application</span></span>  
 <span data-ttu-id="d6e1a-121">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，建立 Visual C# 或 Visual Basic 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-121">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic Console Application project.</span></span> <span data-ttu-id="d6e1a-122">安裝 System.Threading.Tasks.Dataflow NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-122">Install the System.Threading.Tasks.Dataflow NuGet package.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 <span data-ttu-id="d6e1a-123">將下列程式碼加入至您的專案，建立基本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-123">Add the following code to your project to create the basic application.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a><span data-ttu-id="d6e1a-124">建立資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="d6e1a-124">Creating the Dataflow Blocks</span></span>  
 <span data-ttu-id="d6e1a-125">將下列程式碼加入至 `Main` 方法，建立參與管線的資料流程區塊。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-125">Add the following code to the `Main` method to create the dataflow blocks that participate in the pipeline.</span></span> <span data-ttu-id="d6e1a-126">下表摘要說明管線中每個成員的角色。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-126">The table that follows summarizes the role of each member of the pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|<span data-ttu-id="d6e1a-127">成員</span><span class="sxs-lookup"><span data-stu-id="d6e1a-127">Member</span></span>|<span data-ttu-id="d6e1a-128">類型</span><span class="sxs-lookup"><span data-stu-id="d6e1a-128">Type</span></span>|<span data-ttu-id="d6e1a-129">描述</span><span class="sxs-lookup"><span data-stu-id="d6e1a-129">Description</span></span>|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="d6e1a-130">從網站下載書籍的文字。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-130">Downloads the book text from the Web.</span></span>|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="d6e1a-131">將書籍的文字分成文字陣列。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-131">Separates the book text into an array of words.</span></span>|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="d6e1a-132">移除文字陣列中的短字和重複字。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-132">Removes short words and duplicates from the word array.</span></span>|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<span data-ttu-id="d6e1a-133">在篩選過的文字陣列集合中，尋找反向排列項目同樣出現在文字陣列中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-133">Finds all words in the filtered word array collection whose reverse also occurs in the word array.</span></span>|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="d6e1a-134">將文字和對應的反向文字顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-134">Displays words and the corresponding reverse words to the console.</span></span>|  
  
 <span data-ttu-id="d6e1a-135">雖然您可以將這個範例中資料流程管線的多個步驟合併成單一步驟，但是範例的目的在於說明撰寫多個獨立的資料流程工作來執行整體工作的概念。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-135">Although you could combine multiple steps in the dataflow pipeline in this example into one step, the example illustrates the concept of composing multiple independent dataflow tasks to perform a larger task.</span></span> <span data-ttu-id="d6e1a-136">這個範例會使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 讓管線的每個成員對其輸入資料執行作業，並且將結果傳送到管線中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-136">The example uses <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> to enable each member of the pipeline to perform an operation on its input data and send the results to the next step in the pipeline.</span></span> <span data-ttu-id="d6e1a-137">管線的 `findReversedWords` 成員是 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件，因為它會針對每個輸入產生多個獨立的輸出。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-137">The `findReversedWords` member of the pipeline is a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> object because it produces multiple independent outputs for each input.</span></span> <span data-ttu-id="d6e1a-138">管線的尾端 `printReversedWords` 是 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，因為它會對其輸入執行動作，但不會產生結果。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-138">The tail of the pipeline, `printReversedWords`, is an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object because it performs an action on its input, and does not produce a result.</span></span>  
  
## <a name="forming-the-pipeline"></a><span data-ttu-id="d6e1a-139">構成管線</span><span class="sxs-lookup"><span data-stu-id="d6e1a-139">Forming the Pipeline</span></span>  
 <span data-ttu-id="d6e1a-140">加入下列程式碼，將管線中的每個區塊連接到下一個區塊。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-140">Add the following code to connect each block to the next block in the pipeline.</span></span>  
  
 <span data-ttu-id="d6e1a-141">當您呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法將來源資料流程區塊連接到目標資料流程區塊時，來源資料流程區塊會在有可用資料時，將資料傳播至目標區塊。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-141">When you call the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method to connect a source dataflow block to a target dataflow block, the source dataflow block propagates data to the target block as data becomes available.</span></span> <span data-ttu-id="d6e1a-142">如果您也提供了 <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> 並將 <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> 設為 true，不論管線中某個區塊是否順利完成，都將使得管線中的下一個區域完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-142">If you also provide <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> with <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> set to true, successful or unsuccessful completion of one block in the pipeline will cause completion of the next block in the pipeline.</span></span>
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a><span data-ttu-id="d6e1a-143">將資料公佈至管線</span><span class="sxs-lookup"><span data-stu-id="d6e1a-143">Posting Data to the Pipeline</span></span>  
 <span data-ttu-id="d6e1a-144">加入下列程式碼，將《The Iliad of Homer》這本書的 URL 張貼至資料流程管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-144">Add the following code to post the URL of the book *The Iliad of Homer* to the head of the dataflow pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 <span data-ttu-id="d6e1a-145">這個範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> 以同步方式將資料傳送至管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-145">This example uses <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> to synchronously send data to the head of the pipeline.</span></span> <span data-ttu-id="d6e1a-146">如果您必須以非同步方式將資料傳送至資料流程節點，則使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-146">Use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> method when you must asynchronously send data to a dataflow node.</span></span>  
  
## <a name="completing-pipeline-activity"></a><span data-ttu-id="d6e1a-147">完成管線活動</span><span class="sxs-lookup"><span data-stu-id="d6e1a-147">Completing Pipeline Activity</span></span>  
 <span data-ttu-id="d6e1a-148">加入下列程式碼，將管線的開頭標示為已完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-148">Add the following code to mark the head of the pipeline as completed.</span></span> <span data-ttu-id="d6e1a-149">管線的開頭會在處理所有緩衝的訊息後，繼續完成其工作。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-149">The head of the pipeline propagates its completion after it processes all buffered messages.</span></span>
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 <span data-ttu-id="d6e1a-150">這個範例會藉由資料流程管線傳送要處理的 URL。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-150">This example sends one URL through the dataflow pipeline to be processed.</span></span> <span data-ttu-id="d6e1a-151">如果您透過管線傳送多個輸入，請在送出所有輸入之後呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-151">If you send more than one input through a pipeline, call the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> method after you submit all the input.</span></span> <span data-ttu-id="d6e1a-152">如果您的應用程式並未明確定義資料何時失效，或是應用程式不需要等候管線完成，則可以省略這個步驟。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-152">You can omit this step if your application has no well-defined point at which data is no longer available or the application does not have to wait for the pipeline to finish.</span></span>  
  
## <a name="waiting-for-the-pipeline-to-finish"></a><span data-ttu-id="d6e1a-153">等候管線完成</span><span class="sxs-lookup"><span data-stu-id="d6e1a-153">Waiting for the Pipeline to Finish</span></span>  
 <span data-ttu-id="d6e1a-154">加入下列程式碼等候管線完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-154">Add the following code to wait for the pipeline to finish.</span></span> <span data-ttu-id="d6e1a-155">管線尾端完成時，整體作業即告完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-155">The overall operation is finished when the tail of the pipeline finishes.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 <span data-ttu-id="d6e1a-156">您可以從任何一個執行緒或同時從多個執行緒等候資料流程完成。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-156">You can wait for dataflow completion from any thread or from multiple threads at the same time.</span></span>  
  
## <a name="the-complete-example"></a><span data-ttu-id="d6e1a-157">完整範例</span><span class="sxs-lookup"><span data-stu-id="d6e1a-157">The Complete Example</span></span>  
 <span data-ttu-id="d6e1a-158">下列範例將示範本逐步解說的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-158">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="d6e1a-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d6e1a-159">Next Steps</span></span>  
 <span data-ttu-id="d6e1a-160">這個範例會藉由資料流程管線傳送要處理的 URL。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-160">This example sends one URL to process through the dataflow pipeline.</span></span> <span data-ttu-id="d6e1a-161">如果您透過管線傳送多個輸入值，則可以在應用程式中引入某種形式的平行處理原則，這種形式類似組件汽車工廠內零件移動的流程。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-161">If you send more than one input value through a pipeline, you can introduce a form of parallelism into your application that resembles how parts might move through an automobile factory.</span></span> <span data-ttu-id="d6e1a-162">當管線中的第一個成員將其結果傳送給第二個成員時，可以在第二個成員處理第一個結果時平行處理另一個項目。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-162">When the first member of the pipeline sends its result to the second member, it can process another item in parallel as the second member processes the first result.</span></span>  
  
 <span data-ttu-id="d6e1a-163">使用資料流程管線達成的平行處理原則稱為「粗略平行處理原則」(Coarse-grained Parallelism)，因為它通常包含數量較少的大型工作。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-163">The parallelism that is achieved by using dataflow pipelines is known as *coarse-grained parallelism* because it typically consists of fewer, larger tasks.</span></span> <span data-ttu-id="d6e1a-164">您也可以在資料流程管線中使用「精細平行處理原則」(Fine-grained Parallelism) 來處理一些較小且執行時間較短的工作。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-164">You can also use a more *fine-grained parallelism* of smaller, short-running tasks in a dataflow pipeline.</span></span> <span data-ttu-id="d6e1a-165">在這個範例中，管線的 `findReversedWords` 成員會使用 [PLINQ](parallel-linq-plinq.md) 來平行處理工作清單中的多個項目。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-165">In this example, the `findReversedWords` member of the pipeline uses [PLINQ](parallel-linq-plinq.md) to process multiple items in the work list in parallel.</span></span> <span data-ttu-id="d6e1a-166">在粗略管線中使用精細平行處理原則可以改善整體生產量。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-166">The use of fine-grained parallelism in a coarse-grained pipeline can improve overall throughput.</span></span>  
  
 <span data-ttu-id="d6e1a-167">您也可以將來源資料流程區塊連接到多個目標區塊，藉此建立「資料流程網路」。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-167">You can also connect a source dataflow block to multiple target blocks to create a *dataflow network*.</span></span> <span data-ttu-id="d6e1a-168"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法的多載版本採用 <xref:System.Predicate%601> 物件定義目標區塊是否依據其值接受每個訊息。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-168">The overloaded version of the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method takes a <xref:System.Predicate%601> object that defines whether the target block accepts each message based on its value.</span></span> <span data-ttu-id="d6e1a-169">大部分做為來源的資料流程區塊類型都會依照連接的順序，對所有連接的目標區塊提供訊息，直到其中一個區塊接受該訊息為止。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-169">Most dataflow block types that act as sources offer messages to all connected target blocks, in the order in which they were connected, until one of the blocks accepts that message.</span></span> <span data-ttu-id="d6e1a-170">使用這個篩選機制就可以建立連接資料流程區塊的系統，透過不同的路徑導引不同的資料。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-170">By using this filtering mechanism, you can create systems of connected dataflow blocks that direct certain data through one path and other data through another path.</span></span> <span data-ttu-id="d6e1a-171">如需使用篩選來建立資料流程網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e1a-171">For an example that uses filtering to create a dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e1a-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e1a-172">See Also</span></span>  
 [<span data-ttu-id="d6e1a-173">資料流程</span><span class="sxs-lookup"><span data-stu-id="d6e1a-173">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
