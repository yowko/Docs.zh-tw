---
title: "逐步解說：建立資料流程管線"
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
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d63fb872382bfc0a3ba3b8637c7357ab65c58fbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a><span data-ttu-id="a1cde-102">逐步解說：建立資料流程管線</span><span class="sxs-lookup"><span data-stu-id="a1cde-102">Walkthrough: Creating a Dataflow Pipeline</span></span>
<span data-ttu-id="a1cde-103">雖然您可以使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>， <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>，和<xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType>方法，以接收來自來源區塊，您也可以連接訊息區塊組成*資料流程管線*。</span><span class="sxs-lookup"><span data-stu-id="a1cde-103">Although you can use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> methods to receive messages from source blocks, you can also connect message blocks to form a *dataflow pipeline*.</span></span> <span data-ttu-id="a1cde-104">資料流程管線是一系列的元件，或*資料流程區塊*，其中每個執行特定工作，提供更大的目標。</span><span class="sxs-lookup"><span data-stu-id="a1cde-104">A dataflow pipeline is a series of components, or *dataflow blocks*, each of which performs a specific task that contributes to a larger goal.</span></span> <span data-ttu-id="a1cde-105">資料流程管線中的每個資料流程區塊會在收到來自其他資料流程區塊的訊息時，開始執行工作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-105">Every dataflow block in a dataflow pipeline performs work when it receives a message from another dataflow block.</span></span> <span data-ttu-id="a1cde-106">以汽車製造的裝配線做比喻。</span><span class="sxs-lookup"><span data-stu-id="a1cde-106">An analogy to this is an assembly line for automobile manufacturing.</span></span> <span data-ttu-id="a1cde-107">當每輛汽車通過裝配線時，某一站會組裝車架，下一站會安裝引擎，以此類推。</span><span class="sxs-lookup"><span data-stu-id="a1cde-107">As each vehicle passes through the assembly line, one station assembles the frame, the next one installs the engine, and so on.</span></span> <span data-ttu-id="a1cde-108">由於裝配線能夠同時組裝多輛車，因此裝配線的生產量會優於一次將一輛車從頭到尾組裝完成的生產量。</span><span class="sxs-lookup"><span data-stu-id="a1cde-108">Because an assembly line enables multiple vehicles to be assembled at the same time, it provides better throughput than assembling complete vehicles one at a time.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="a1cde-109">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a1cde-109">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="a1cde-110">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="a1cde-110">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
 <span data-ttu-id="a1cde-111">本文示範資料流程管線下載活頁簿*The Iliad of Homer*來自網站及搜尋要比對個別字與文字字反向第一個字的字元。</span><span class="sxs-lookup"><span data-stu-id="a1cde-111">This document demonstrates a dataflow pipeline that downloads the book *The Iliad of Homer* from a website and searches the text to match individual words with words that reverse the first word's characters.</span></span> <span data-ttu-id="a1cde-112">本文件中資料流程管線是由下列步驟形成：</span><span class="sxs-lookup"><span data-stu-id="a1cde-112">The formation of the dataflow pipeline in this document consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="a1cde-113">建立參與管線的資料流程區塊。</span><span class="sxs-lookup"><span data-stu-id="a1cde-113">Create the dataflow blocks that participate in the pipeline.</span></span>  
  
2.  <span data-ttu-id="a1cde-114">將每個資料流程區塊連接到管線中的下一個區塊。</span><span class="sxs-lookup"><span data-stu-id="a1cde-114">Connect each dataflow block to the next block in the pipeline.</span></span> <span data-ttu-id="a1cde-115">每個區塊都會收到管線中前一個區塊的輸出做為輸入。</span><span class="sxs-lookup"><span data-stu-id="a1cde-115">Each block receives as input the output of the previous block in the pipeline.</span></span>  
  
3.  <span data-ttu-id="a1cde-116">對每個資料流程區塊建立接續工作，在前一個區塊完成之後將下一個區塊設定為已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="a1cde-116">For each dataflow block, create a continuation task that sets the next block to the completed state after the previous block finishes.</span></span>  
  
4.  <span data-ttu-id="a1cde-117">將資料公佈至管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="a1cde-117">Post data to the head of the pipeline.</span></span>  
  
5.  <span data-ttu-id="a1cde-118">將管線的開頭標示為已完成。</span><span class="sxs-lookup"><span data-stu-id="a1cde-118">Mark the head of the pipeline as completed.</span></span>  
  
6.  <span data-ttu-id="a1cde-119">等候管線完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-119">Wait for the pipeline to complete all work.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a1cde-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="a1cde-120">Prerequisites</span></span>  
 <span data-ttu-id="a1cde-121">在開始進行這個逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="a1cde-121">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  
  
## <a name="creating-a-console-application"></a><span data-ttu-id="a1cde-122">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a1cde-122">Creating a Console Application</span></span>  
 <span data-ttu-id="a1cde-123">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，建立 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a1cde-123">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] Console Application project.</span></span> <span data-ttu-id="a1cde-124">加入 System.Threading.Tasks.Dataflow.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="a1cde-124">Add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
 <span data-ttu-id="a1cde-125">或者，建立檔案並將其命名`ReverseWords.cs`(`ReverseWords.vb`如[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])，然後執行下列命令在 Visual Studio 命令提示字元視窗中，將專案編譯。</span><span class="sxs-lookup"><span data-stu-id="a1cde-125">Alternatively, create a file and name it `ReverseWords.cs` (`ReverseWords.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window to compile the project.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="a1cde-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**</span><span class="sxs-lookup"><span data-stu-id="a1cde-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="a1cde-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**</span><span class="sxs-lookup"><span data-stu-id="a1cde-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**</span></span>  
  
 <span data-ttu-id="a1cde-128">將下列程式碼加入至您的專案，建立基本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1cde-128">Add the following code to your project to create the basic application.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a><span data-ttu-id="a1cde-129">建立資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="a1cde-129">Creating the Dataflow Blocks</span></span>  
 <span data-ttu-id="a1cde-130">將下列程式碼加入至 `Main` 方法，建立參與管線的資料流程區塊。</span><span class="sxs-lookup"><span data-stu-id="a1cde-130">Add the following code to the `Main` method to create the dataflow blocks that participate in the pipeline.</span></span> <span data-ttu-id="a1cde-131">下表摘要說明管線中每個成員的角色。</span><span class="sxs-lookup"><span data-stu-id="a1cde-131">The table that follows summarizes the role of each member of the pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|<span data-ttu-id="a1cde-132">成員</span><span class="sxs-lookup"><span data-stu-id="a1cde-132">Member</span></span>|<span data-ttu-id="a1cde-133">類型</span><span class="sxs-lookup"><span data-stu-id="a1cde-133">Type</span></span>|<span data-ttu-id="a1cde-134">說明</span><span class="sxs-lookup"><span data-stu-id="a1cde-134">Description</span></span>|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="a1cde-135">從網站下載書籍的文字。</span><span class="sxs-lookup"><span data-stu-id="a1cde-135">Downloads the book text from the Web.</span></span>|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="a1cde-136">將書籍的文字分成文字陣列。</span><span class="sxs-lookup"><span data-stu-id="a1cde-136">Separates the book text into an array of words.</span></span>|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="a1cde-137">移除文字陣列中簡短的字，依字母順序排序產生的字，並且移除重複項目。</span><span class="sxs-lookup"><span data-stu-id="a1cde-137">Removes short words from the word array, orders the resulting words alphabetically, and remove duplicates.</span></span>|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<span data-ttu-id="a1cde-138">在篩選過的文字陣列集合中，尋找反向排列項目同樣出現在文字陣列中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="a1cde-138">Finds all words in the filtered word array collection whose reverse also occurs in the word array.</span></span>|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="a1cde-139">將文字和對應的反向文字顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="a1cde-139">Displays words and the corresponding reverse words to the console.</span></span>|  
  
 <span data-ttu-id="a1cde-140">雖然您可以將這個範例中資料流程管線的多個步驟合併成單一步驟，但是範例的目的在於說明撰寫多個獨立的資料流程工作來執行整體工作的概念。</span><span class="sxs-lookup"><span data-stu-id="a1cde-140">Although you could combine multiple steps in the dataflow pipeline in this example into one step, the example illustrates the concept of composing multiple independent dataflow tasks to perform a larger task.</span></span> <span data-ttu-id="a1cde-141">這個範例會使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 讓管線的每個成員對其輸入資料執行作業，並且將結果傳送到管線中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a1cde-141">The example uses <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> to enable each member of the pipeline to perform an operation on its input data and send the results to the next step in the pipeline.</span></span> <span data-ttu-id="a1cde-142">管線的 `findReversedWords` 成員是 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件，因為它會針對每個輸入產生多個獨立的輸出。</span><span class="sxs-lookup"><span data-stu-id="a1cde-142">The `findReversedWords` member of the pipeline is a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> object because it produces multiple independent outputs for each input.</span></span> <span data-ttu-id="a1cde-143">管線的尾端 `printReversedWords` 是 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，因為它會對其輸入執行動作，但不會產生結果。</span><span class="sxs-lookup"><span data-stu-id="a1cde-143">The tail of the pipeline, `printReversedWords`, is a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object because it performs an action on its input, and does not produce a result.</span></span>  
  
## <a name="forming-the-pipeline"></a><span data-ttu-id="a1cde-144">構成管線</span><span class="sxs-lookup"><span data-stu-id="a1cde-144">Forming the Pipeline</span></span>  
 <span data-ttu-id="a1cde-145">加入下列程式碼，將管線中的每個區塊連接到下一個區塊。</span><span class="sxs-lookup"><span data-stu-id="a1cde-145">Add the following code to connect each block to the next block in the pipeline.</span></span>  
  
 <span data-ttu-id="a1cde-146">當您呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法將來源資料流程區塊連接到目標資料流程區塊時，來源資料流程區塊會在有可用資料時，將資料傳播至目標區塊。</span><span class="sxs-lookup"><span data-stu-id="a1cde-146">When you call the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method to connect a source dataflow block to a target dataflow block, the source dataflow block propagates data to the target block as data becomes available.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="creating-the-completion-tasks"></a><span data-ttu-id="a1cde-147">建立完成工作</span><span class="sxs-lookup"><span data-stu-id="a1cde-147">Creating the Completion Tasks</span></span>  
 <span data-ttu-id="a1cde-148">加入下列程式碼，讓每個資料流程區塊在處理所有資料之後執行最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-148">Add the following code to enable each dataflow block to perform a final action after it processes all data.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 <span data-ttu-id="a1cde-149">若要在管線中傳播完成，每一項完成工作都要將下一個資料流程區塊設定為已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="a1cde-149">To propagate completion through the pipeline, each completion task sets the next dataflow block to the completed state.</span></span> <span data-ttu-id="a1cde-150">例如，當管線的開頭設定為已完成狀態時，它會處理所有剩餘的緩衝訊息，然後執行其完成工作，將管線中的第二個成員設定為已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="a1cde-150">For example, when the head of the pipeline is set to the completed state, it processes any remaining buffered messages and then runs its completion task, which sets the second member of the pipeline to the completed state.</span></span> <span data-ttu-id="a1cde-151">管線中的第二個成員接著就會處理所有剩餘的緩衝訊息，並執行其完成工作，將管線中的第三個成員設定為已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="a1cde-151">The second member of the pipeline in turn processes any remaining buffered messages and then runs its completion task, which sets the third member of the pipeline to the completed state.</span></span> <span data-ttu-id="a1cde-152">這個流程會繼續進行，直到管線中的所有成員完成為止。</span><span class="sxs-lookup"><span data-stu-id="a1cde-152">This process continues until all members of the pipeline finish.</span></span> <span data-ttu-id="a1cde-153">這個範例會使用 `delegate` 關鍵字 (在 `Function` 中為 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 定義接續工作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-153">This example uses the `delegate` keyword (`Function` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) to define the continuation tasks.</span></span>  
  
## <a name="posting-data-to-the-pipeline"></a><span data-ttu-id="a1cde-154">將資料公佈至管線</span><span class="sxs-lookup"><span data-stu-id="a1cde-154">Posting Data to the Pipeline</span></span>  
 <span data-ttu-id="a1cde-155">將下列的程式碼加入活頁簿的 URL 公佈*The Iliad of Homer*至資料流程管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="a1cde-155">Add the following code to post the URL of the book *The Iliad of Homer* to the head of the dataflow pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 <span data-ttu-id="a1cde-156">這個範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> 以同步方式將資料傳送至管線的開頭。</span><span class="sxs-lookup"><span data-stu-id="a1cde-156">This example uses <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> to synchronously send data to the head of the pipeline.</span></span> <span data-ttu-id="a1cde-157">如果您必須以非同步方式將資料傳送至資料流程節點，則使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a1cde-157">Use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> method when you must asynchronously send data to a dataflow node.</span></span>  
  
## <a name="completing-pipeline-activity"></a><span data-ttu-id="a1cde-158">完成管線活動</span><span class="sxs-lookup"><span data-stu-id="a1cde-158">Completing Pipeline Activity</span></span>  
 <span data-ttu-id="a1cde-159">加入下列程式碼，將管線的開頭標示為已完成。</span><span class="sxs-lookup"><span data-stu-id="a1cde-159">Add the following code to mark the head of the pipeline as completed.</span></span> <span data-ttu-id="a1cde-160">管線的開頭會在處理所有緩衝的訊息後，執行其接續工作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-160">The head of the pipeline runs its continuation task after it processes all buffered messages.</span></span> <span data-ttu-id="a1cde-161">這個接續工作會透過管線傳播已完成狀態。</span><span class="sxs-lookup"><span data-stu-id="a1cde-161">This continuation task propagates the completed state through the pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 <span data-ttu-id="a1cde-162">這個範例會藉由資料流程管線傳送要處理的 URL。</span><span class="sxs-lookup"><span data-stu-id="a1cde-162">This example sends one URL through the dataflow pipeline to be processed.</span></span> <span data-ttu-id="a1cde-163">如果您透過管線傳送多個輸入，請在送出所有輸入之後呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a1cde-163">If you send more than one input through a pipeline, call the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> method after you submit all the input.</span></span> <span data-ttu-id="a1cde-164">如果您的應用程式並未明確定義資料何時失效，或是應用程式不需要等候管線完成，則可以省略這個步驟。</span><span class="sxs-lookup"><span data-stu-id="a1cde-164">You can omit this step if your application has no well-defined point at which data is no longer available or the application does not have to wait for the pipeline to finish.</span></span>  
  
## <a name="waiting-for-the-pipeline-to-finish"></a><span data-ttu-id="a1cde-165">等候管線完成</span><span class="sxs-lookup"><span data-stu-id="a1cde-165">Waiting for the Pipeline to Finish</span></span>  
 <span data-ttu-id="a1cde-166">加入下列程式碼等候管線完成。</span><span class="sxs-lookup"><span data-stu-id="a1cde-166">Add the following code to wait for the pipeline to finish.</span></span> <span data-ttu-id="a1cde-167">由於這個範例使用接續工作透過管線傳播完成，因此整個作業會在管線的尾端完成時完成。</span><span class="sxs-lookup"><span data-stu-id="a1cde-167">Because this example uses continuation tasks to propagate completion through the pipeline, the overall operation is finished when the tail of the pipeline finishes.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 <span data-ttu-id="a1cde-168">您可以從任何一個執行緒或同時從多個執行緒等候資料流程完成。</span><span class="sxs-lookup"><span data-stu-id="a1cde-168">You can wait for dataflow completion from any thread or from multiple threads at the same time.</span></span>  
  
## <a name="the-complete-example"></a><span data-ttu-id="a1cde-169">完整範例</span><span class="sxs-lookup"><span data-stu-id="a1cde-169">The Complete Example</span></span>  
 <span data-ttu-id="a1cde-170">下列範例將示範本逐步解說的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="a1cde-170">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="a1cde-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a1cde-171">Next Steps</span></span>  
 <span data-ttu-id="a1cde-172">這個範例會藉由資料流程管線傳送要處理的 URL。</span><span class="sxs-lookup"><span data-stu-id="a1cde-172">This example sends one URL to process through the dataflow pipeline.</span></span> <span data-ttu-id="a1cde-173">如果您透過管線傳送多個輸入值，則可以在應用程式中引入某種形式的平行處理原則，這種形式類似組件汽車工廠內零件移動的流程。</span><span class="sxs-lookup"><span data-stu-id="a1cde-173">If you send more than one input value through a pipeline, you can introduce a form of parallelism into your application that resembles how parts might move through an automobile factory.</span></span> <span data-ttu-id="a1cde-174">當管線中的第一個成員將其結果傳送給第二個成員時，可以在第二個成員處理第一個結果時平行處理另一個項目。</span><span class="sxs-lookup"><span data-stu-id="a1cde-174">When the first member of the pipeline sends its result to the second member, it can process another item in parallel as the second member processes the first result.</span></span>  
  
 <span data-ttu-id="a1cde-175">使用資料流程管線達成的平行處理原則稱為*粗略平行處理原則*因為它通常包含數量較少，較大的工作。</span><span class="sxs-lookup"><span data-stu-id="a1cde-175">The parallelism that is achieved by using dataflow pipelines is known as *coarse-grained parallelism* because it typically consists of fewer, larger tasks.</span></span> <span data-ttu-id="a1cde-176">您也可以使用更*細部平行處理原則*的較短執行的工作中資料流程管線。</span><span class="sxs-lookup"><span data-stu-id="a1cde-176">You can also use a more *fine-grained parallelism* of smaller, short-running tasks in a dataflow pipeline.</span></span> <span data-ttu-id="a1cde-177">在這個範例中，管線的 `findReversedWords` 成員會使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法平行處理工作清單中的多個項目。</span><span class="sxs-lookup"><span data-stu-id="a1cde-177">In this example, the `findReversedWords` member of the pipeline uses the <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> method to process multiple items in the work list in parallel.</span></span> <span data-ttu-id="a1cde-178">在粗略管線中使用精細平行處理原則可以改善整體生產量。</span><span class="sxs-lookup"><span data-stu-id="a1cde-178">The use of fine-grained parallelism in a coarse-grained pipeline can improve overall throughput.</span></span>  
  
 <span data-ttu-id="a1cde-179">您也可以連接來源資料流程區塊以建立多個目標區塊*資料流程網路*。</span><span class="sxs-lookup"><span data-stu-id="a1cde-179">You can also connect a source dataflow block to multiple target blocks to create a *dataflow network*.</span></span> <span data-ttu-id="a1cde-180"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法的多載版本採用 <xref:System.Predicate%601> 物件定義目標區塊是否依據其值接受每個訊息。</span><span class="sxs-lookup"><span data-stu-id="a1cde-180">The overloaded version of the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method takes a <xref:System.Predicate%601> object that defines whether the target block accepts each message based on its value.</span></span> <span data-ttu-id="a1cde-181">大部分做為來源的資料流程區塊類型都會依照連接的順序，對所有連接的目標區塊提供訊息，直到其中一個區塊接受該訊息為止。</span><span class="sxs-lookup"><span data-stu-id="a1cde-181">Most dataflow block types that act as sources offer messages to all connected target blocks, in the order in which they were connected, until one of the blocks accepts that message.</span></span> <span data-ttu-id="a1cde-182">使用這個篩選機制就可以建立連接資料流程區塊的系統，透過不同的路徑導引不同的資料。</span><span class="sxs-lookup"><span data-stu-id="a1cde-182">By using this filtering mechanism, you can create systems of connected dataflow blocks that direct certain data through one path and other data through another path.</span></span> <span data-ttu-id="a1cde-183">如需使用篩選建立資料流程網路的範例，請參閱[逐步解說： 在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a1cde-183">For an example that uses filtering to create a dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1cde-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1cde-184">See Also</span></span>  
 [<span data-ttu-id="a1cde-185">資料流程</span><span class="sxs-lookup"><span data-stu-id="a1cde-185">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
