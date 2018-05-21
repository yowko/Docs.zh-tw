---
title: 如何：撰寫簡單的 Parallel.ForEach 迴圈
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e3fb5fd807971aed014ba98cbb207c4483b93f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="f4ff9-102">如何：撰寫簡單的 Parallel.ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="f4ff9-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="f4ff9-103">此範例示範如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈來透過 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 資料來源啟用資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ff9-104">本文件使用 Lambda 運算式來定義 PLINQ 中的委派。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="f4ff9-105">如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4ff9-106">範例</span><span class="sxs-lookup"><span data-stu-id="f4ff9-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="f4ff9-107"><xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈的運作方式類似 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="f4ff9-108">來源集合會進行分割，並依據系統環境在多個執行緒上排定工作。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="f4ff9-109">系統上的處理器愈多，平行方法的執行速度愈快。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="f4ff9-110">對於某些來源集合，循序迴圈的執行速度可能更快，這取決於來源的大小和執行的工作種類。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="f4ff9-111">如需效能的詳細資訊，請參閱[資料和工作平行處理原則中可能出現的錯誤](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="f4ff9-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="f4ff9-112">如需平行迴圈的詳細資訊，請參閱[如何： 撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="f4ff9-113">若要將 <xref:System.Threading.Tasks.Parallel.ForEach%2A>使用於非泛型集合 ，可使用 <xref:System.Linq.Enumerable.Cast%2A> 擴充方法將集合轉換成泛型集合，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f4ff9-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="f4ff9-114">您也可以使用平行 LINQ (PLINQ) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="f4ff9-115">PLINQ 可讓您使用宣告式查詢語法來表示迴圈行為。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="f4ff9-116">如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4ff9-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f4ff9-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f4ff9-118">複製此程式碼，並將其貼入 Visual Studio 2010 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f4ff9-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="f4ff9-119">加入對 System.Net.Http 的參考</span><span class="sxs-lookup"><span data-stu-id="f4ff9-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="f4ff9-120">按 F5 鍵</span><span class="sxs-lookup"><span data-stu-id="f4ff9-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ff9-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4ff9-121">See Also</span></span>  
 [<span data-ttu-id="f4ff9-122">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="f4ff9-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="f4ff9-123">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="f4ff9-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="f4ff9-124">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f4ff9-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
