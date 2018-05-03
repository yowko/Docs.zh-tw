---
title: 如何：撰寫簡單的 Parallel.ForEach 迴圈
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90b900bf98ab664e0fce5c70573f01e044d70803
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="5dc1d-102">如何：撰寫簡單的 Parallel.ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="5dc1d-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="5dc1d-103">此範例示範如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈來透過 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 資料來源啟用資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dc1d-104">本文件使用 Lambda 運算式來定義 PLINQ 中的委派。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="5dc1d-105">如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dc1d-106">範例</span><span class="sxs-lookup"><span data-stu-id="5dc1d-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="5dc1d-107"><xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈的運作方式類似 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="5dc1d-108">來源集合會進行分割，並依據系統環境在多個執行緒上排定工作。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="5dc1d-109">系統上的處理器愈多，平行方法的執行速度愈快。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="5dc1d-110">對於某些來源集合，循序迴圈的執行速度可能更快，這取決於來源的大小和執行的工作種類。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="5dc1d-111">如需效能的詳細資訊，請參閱[資料和工作平行處理原則中可能出現的錯誤](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="5dc1d-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="5dc1d-112">如需平行迴圈的詳細資訊，請參閱[如何： 撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="5dc1d-113">若要將 <xref:System.Threading.Tasks.Parallel.ForEach%2A>使用於非泛型集合 ，可使用 <xref:System.Linq.Enumerable.Cast%2A> 擴充方法將集合轉換成泛型集合，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5dc1d-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="5dc1d-114">您也可以使用平行 LINQ (PLINQ) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="5dc1d-115">PLINQ 可讓您使用宣告式查詢語法來表示迴圈行為。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="5dc1d-116">如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5dc1d-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5dc1d-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="5dc1d-118">複製此程式碼，並將其貼入 Visual Studio 2010 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="5dc1d-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="5dc1d-119">加入對 System.Net.Http 的參考</span><span class="sxs-lookup"><span data-stu-id="5dc1d-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="5dc1d-120">按 F5 鍵</span><span class="sxs-lookup"><span data-stu-id="5dc1d-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc1d-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dc1d-121">See Also</span></span>  
 [<span data-ttu-id="5dc1d-122">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="5dc1d-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="5dc1d-123">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="5dc1d-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="5dc1d-124">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="5dc1d-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
