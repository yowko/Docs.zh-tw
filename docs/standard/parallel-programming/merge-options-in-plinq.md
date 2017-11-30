---
title: "PLINQ 中的合併選項"
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a><span data-ttu-id="1a8bd-102">PLINQ 中的合併選項</span><span class="sxs-lookup"><span data-stu-id="1a8bd-102">Merge Options in PLINQ</span></span>
<span data-ttu-id="1a8bd-103">當查詢正在執行平行 PLINQ 資料分割作為來源序列，讓多個執行緒可以在不同的組件上同時處理，通常在個別執行緒上。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-103">When a query is executing as parallel, PLINQ partitions the source sequence so that multiple threads can work on different parts concurrently, typically on separate threads.</span></span> <span data-ttu-id="1a8bd-104">如果結果使用上一個執行緒，例如，在`foreach`(`For Each`中[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 迴圈，則必須以每個執行緒的結果合併回單一序列。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-104">If the results are to be consumed on one thread, for example, in a `foreach` (`For Each` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) loop, then the results from every thread must be merged back into one sequence.</span></span> <span data-ttu-id="1a8bd-105">PLINQ 執行的合併類型而定的運算子會出現在查詢中。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-105">The kind of merge that PLINQ performs depends on the operators that are present in the query.</span></span> <span data-ttu-id="1a8bd-106">比方說，強制執行結果，在新的訂單的運算子必須緩衝處理所有執行緒的所有項目。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-106">For example, operators that impose a new order on the results must buffer all elements from all threads.</span></span> <span data-ttu-id="1a8bd-107">觀點耗用端執行緒 （這也是應用程式使用者） 的完整緩衝的查詢可能會執行值得注意的一段時間，它會產生其第一個結果。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-107">From the perspective of the consuming thread (which is also that of the application user) a fully buffered query might run for a noticeable period of time before it produces its first result.</span></span> <span data-ttu-id="1a8bd-108">其他運算子，根據預設，會部分進行緩衝處理;會產生其結果批次中。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-108">Other operators, by default, are partially buffered; they yield their results in batches.</span></span> <span data-ttu-id="1a8bd-109">運算子，<xref:System.Linq.ParallelEnumerable.ForAll%2A>預設不會經過緩衝。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-109">One operator, <xref:System.Linq.ParallelEnumerable.ForAll%2A> is not buffered by default.</span></span> <span data-ttu-id="1a8bd-110">它會產生所有項目從所有執行緒立即。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-110">It yields all elements from all threads immediately.</span></span>  
  
 <span data-ttu-id="1a8bd-111">使用<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>方法，如所示，在下列範例中，您可以提供提示給 PLINQ，表示何種合併，以執行。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-111">By using the <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> method, as shown in the following example, you can provide a hint to PLINQ that indicates what kind of merging to perform.</span></span>  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 <span data-ttu-id="1a8bd-112">完整的範例，請參閱[How to： 在 PLINQ 中指定 「 合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-112">For the complete example, see [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).</span></span>  
  
 <span data-ttu-id="1a8bd-113">如果特定的查詢無法支援要求的選項，此選項將只忽略。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-113">If the particular query cannot support the requested option, then the option will just be ignored.</span></span> <span data-ttu-id="1a8bd-114">在大部分情況下，您就不需要指定 PLINQ 查詢的合併選項。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-114">In most cases, you do not have to specify a merge option for a PLINQ query.</span></span> <span data-ttu-id="1a8bd-115">不過，在某些情況下，您可能會發現藉由測試及查詢的執行最佳的非預設模式的度量。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-115">However, in some cases you may find by testing and measurement that a query executes best in a non-default mode.</span></span> <span data-ttu-id="1a8bd-116">這個選項的常見用法是強制使用區塊合併的運算子，將串流處理其結果，以提供更能有效回應的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-116">A common use of this option is to force a chunk-merging operator to stream its results in order to provide a more responsive user interface.</span></span>  
  
## <a name="parallelmergeoptions"></a><span data-ttu-id="1a8bd-117">ParallelMergeOptions</span><span class="sxs-lookup"><span data-stu-id="1a8bd-117">ParallelMergeOptions</span></span>  
 <span data-ttu-id="1a8bd-118"><xref:System.Linq.ParallelMergeOptions>列舉會包含下列選項，指定當一個執行緒上耗用結果查詢的最終輸出產生的時，支援的查詢圖形：</span><span class="sxs-lookup"><span data-stu-id="1a8bd-118">The <xref:System.Linq.ParallelMergeOptions> enumeration includes the following options that specify, for supported query shapes, how the final output of the query is yielded when the results are consumed on one thread:</span></span>  
  
-   `Not Buffered`  
  
     <span data-ttu-id="1a8bd-119"><xref:System.Linq.ParallelMergeOptions.NotBuffered>選項會讓每個處理過的項目，傳回每個執行緒，因為它會產生。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-119">The <xref:System.Linq.ParallelMergeOptions.NotBuffered> option causes each processed element to be returned from each thread as soon as it is produced.</span></span> <span data-ttu-id="1a8bd-120">此行為是類似於 「 streaming 」 的輸出。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-120">This behavior is analogous to "streaming" the output.</span></span> <span data-ttu-id="1a8bd-121">如果<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>運算子是在查詢中，存在`NotBuffered`保留來源項目順序。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-121">If the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator is present in the query, `NotBuffered` preserves the order of the source elements.</span></span> <span data-ttu-id="1a8bd-122">雖然`NotBuffered`而產生的結果，因為已經有開始、 所有結果可能仍會產生的總時間會超過使用其他合併選項之一。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-122">Although `NotBuffered` starts yielding results as soon as they're available,, the total time to produce all the results might still be longer than using one of the other merge options.</span></span>  
  
-   `Auto Buffered`  
  
     <span data-ttu-id="1a8bd-123"><xref:System.Linq.ParallelMergeOptions.AutoBuffered> 選項會讓查詢將項目收集至緩衝區中，然後定期將緩衝區內容一次產生至耗用端執行緒中。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-123">The <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option causes the query to collect elements into a buffer and then periodically yield the buffer contents all at once to the consuming thread.</span></span> <span data-ttu-id="1a8bd-124">這是產生 「 區塊 」 中的來源資料，而不使用 「 資料流 」 的行為類似`NotBuffered`。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-124">This is analogous to yielding the source data in "chunks" instead of using the "streaming" behavior of `NotBuffered`.</span></span> <span data-ttu-id="1a8bd-125">`AutoBuffered`可能需要花費長於`NotBuffered`至耗用端執行緒上使用第一個項目。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-125">`AutoBuffered` may take longer than `NotBuffered` to make the first element available on the consuming thread.</span></span> <span data-ttu-id="1a8bd-126">緩衝區的大小以及產生的確切行為不是可設定，而可能有所不同，取決於各種因素與查詢相關聯。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-126">The size of the buffer and the exact yielding behavior are not configurable and may vary, depending on various factors that relate to the query.</span></span>  
  
-   `FullyBuffered`  
  
     <span data-ttu-id="1a8bd-127"><xref:System.Linq.ParallelMergeOptions.FullyBuffered>選項會使任何項目產生之前進行緩衝處理整個查詢的輸出。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-127">The <xref:System.Linq.ParallelMergeOptions.FullyBuffered> option causes the output of the whole query to be buffered before any of the elements are yielded.</span></span> <span data-ttu-id="1a8bd-128">當您使用此選項時，就可以花長時間之前第一個項目位於耗用端執行緒，但仍會產生完整的結果，可能會較快，使用其他選項。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-128">When you use this option, it can take longer before the first element is available on the consuming thread, but the complete results might still be produced faster than by using the other options.</span></span>  
  
## <a name="query-operators-that-support-merge-options"></a><span data-ttu-id="1a8bd-129">支援的合併選項的查詢運算子</span><span class="sxs-lookup"><span data-stu-id="1a8bd-129">Query Operators that Support Merge Options</span></span>  
 <span data-ttu-id="1a8bd-130">下表列出支援所有的合併選項模式，受限於指定的限制的運算子。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-130">The following table lists the operators that support all merge option modes, subject to the specified restrictions.</span></span>  
  
|<span data-ttu-id="1a8bd-131">運算子</span><span class="sxs-lookup"><span data-stu-id="1a8bd-131">Operator</span></span>|<span data-ttu-id="1a8bd-132">限制</span><span class="sxs-lookup"><span data-stu-id="1a8bd-132">Restrictions</span></span>|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|<span data-ttu-id="1a8bd-133">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-133">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|<span data-ttu-id="1a8bd-134">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-134">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|<span data-ttu-id="1a8bd-135">需要陣列或清單僅限於來源的非排序查詢。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-135">Non-ordered queries that have an Array or List source only.</span></span>|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|<span data-ttu-id="1a8bd-136">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-136">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|<span data-ttu-id="1a8bd-137">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-137">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|<span data-ttu-id="1a8bd-138">需要陣列或清單僅限於來源的非排序查詢。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-138">Non-ordered queries that have an Array or List source only.</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|<span data-ttu-id="1a8bd-139">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-139">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|<span data-ttu-id="1a8bd-140">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-140">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|<span data-ttu-id="1a8bd-141">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-141">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|<span data-ttu-id="1a8bd-142">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-142">None</span></span>|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|<span data-ttu-id="1a8bd-143">無</span><span class="sxs-lookup"><span data-stu-id="1a8bd-143">None</span></span>|  
  
 <span data-ttu-id="1a8bd-144">所有其他 PLINQ 查詢運算子可能會忽略使用者提供的合併選項。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-144">All other PLINQ query operators might ignore user-provided merge options.</span></span> <span data-ttu-id="1a8bd-145">例如，某些查詢運算子，<xref:System.Linq.ParallelEnumerable.Reverse%2A>和<xref:System.Linq.ParallelEnumerable.OrderBy%2A>，無法產生任何項目，直到所有已產生及重新排列。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-145">Some query operators, for example, <xref:System.Linq.ParallelEnumerable.Reverse%2A> and <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, cannot yield any elements until all have been produced and reordered.</span></span> <span data-ttu-id="1a8bd-146">因此，當<xref:System.Linq.ParallelMergeOptions>也包含這類運算子的查詢中使用了<xref:System.Linq.ParallelEnumerable.Reverse%2A>，合併行為將不會套用在查詢中，直到之後該運算子所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-146">Therefore, when <xref:System.Linq.ParallelMergeOptions> is used in a query that also contains an operator such as <xref:System.Linq.ParallelEnumerable.Reverse%2A>, the merge behavior will not be applied in the query until after that operator has produced its results.</span></span>  
  
 <span data-ttu-id="1a8bd-147">有些運算子能夠處理的合併選項取決於來源序列中，類型及是否<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>稍早在查詢中使用運算子。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-147">The ability of some operators to handle merge options depends on the type of the source sequence, and whether the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator was used earlier in the query.</span></span> <span data-ttu-id="1a8bd-148"><xref:System.Linq.ParallelEnumerable.ForAll%2A>一定是<xref:System.Linq.ParallelMergeOptions.NotBuffered>; 它會立即產生其項目。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-148"><xref:System.Linq.ParallelEnumerable.ForAll%2A> is always <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; it yields its elements immediately.</span></span> <span data-ttu-id="1a8bd-149"><xref:System.Linq.ParallelEnumerable.OrderBy%2A>一定是<xref:System.Linq.ParallelMergeOptions.FullyBuffered>; 它會產生前，它必須排序整份清單。</span><span class="sxs-lookup"><span data-stu-id="1a8bd-149"><xref:System.Linq.ParallelEnumerable.OrderBy%2A> is always <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; it must sort the whole list before it yields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a8bd-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a8bd-150">See Also</span></span>  
 [<span data-ttu-id="1a8bd-151">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1a8bd-151">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="1a8bd-152">操作說明：在 PLINQ 中指定合併選項</span><span class="sxs-lookup"><span data-stu-id="1a8bd-152">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
