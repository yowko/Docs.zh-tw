---
title: .NET 的平行程式設計
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b5426f5af9cd6ca919d8da0de0acfed76a2e63
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970385"
---
# <a name="parallel-programming-in-net"></a><span data-ttu-id="d4eec-102">.NET 的平行程式設計</span><span class="sxs-lookup"><span data-stu-id="d4eec-102">Parallel Programming in .NET</span></span>

<span data-ttu-id="d4eec-103">許多個人電腦和工作站都具有多個 CPU 核心，以便能夠同時執行多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="d4eec-103">Many personal computers and workstations have multiple CPU cores that enable multiple threads to be executed simultaneously.</span></span> <span data-ttu-id="d4eec-104">若要利用硬體優勢，您可以將您的程式碼平行化，以便將工作分散到多個處理器。</span><span class="sxs-lookup"><span data-stu-id="d4eec-104">To take advantage of the hardware, you can parallelize your code to distribute work across multiple processors.</span></span>

<span data-ttu-id="d4eec-105">在過去，平行化作業需要在低階操作執行緒和鎖定。</span><span class="sxs-lookup"><span data-stu-id="d4eec-105">In the past, parallelization required low-level manipulation of threads and locks.</span></span> <span data-ttu-id="d4eec-106">Visual Studio 與 .NET Framework 提供了執行階段、類別庫類型和診斷工具，以加強支援平行程式設計。</span><span class="sxs-lookup"><span data-stu-id="d4eec-106">Visual Studio and the .NET Framework enhance support for parallel programming by providing a runtime, class library types, and diagnostic tools.</span></span> <span data-ttu-id="d4eec-107">從 .NET Framework 4 引進的這些功能簡化了平行開發。</span><span class="sxs-lookup"><span data-stu-id="d4eec-107">These features, which were introduced with the .NET Framework 4, simplify parallel development.</span></span> <span data-ttu-id="d4eec-108">您能夠利用簡單常見的語法，撰寫效率高、精細且具彈性的平行程式碼，而不需要直接使用執行緒或執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="d4eec-108">You can write efficient, fine-grained, and scalable parallel code in a natural idiom without having to work directly with threads or the thread pool.</span></span>

<span data-ttu-id="d4eec-109">下圖提供 .NET Framework 中平行程式設計架構的高階概觀：</span><span class="sxs-lookup"><span data-stu-id="d4eec-109">The following illustration provides a high-level overview of the parallel programming architecture in the .NET Framework:</span></span>

![.NET 平行程式設計架構](./media/tpl-architecture.png)

## <a name="related-topics"></a><span data-ttu-id="d4eec-111">相關主題</span><span class="sxs-lookup"><span data-stu-id="d4eec-111">Related Topics</span></span>

|<span data-ttu-id="d4eec-112">技術</span><span class="sxs-lookup"><span data-stu-id="d4eec-112">Technology</span></span>|<span data-ttu-id="d4eec-113">說明</span><span class="sxs-lookup"><span data-stu-id="d4eec-113">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="d4eec-114">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="d4eec-114">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|<span data-ttu-id="d4eec-115">提供 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 類別 (包含平行版本的 `For` 和 `ForEach` 迴圈) 及 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別 (表示表達非同步作業較好的方式) 的文件。</span><span class="sxs-lookup"><span data-stu-id="d4eec-115">Provides documentation for the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> class, which includes parallel versions of `For` and `ForEach` loops, and also for the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class, which represents the preferred way to express asynchronous operations.</span></span>|
|[<span data-ttu-id="d4eec-116">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d4eec-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|<span data-ttu-id="d4eec-117">平行實作的 LINQ to Objects，在許多情節中可大幅改善效能。</span><span class="sxs-lookup"><span data-stu-id="d4eec-117">A parallel implementation of LINQ to Objects that significantly improves performance in many scenarios.</span></span>|
|[<span data-ttu-id="d4eec-118">適用於平行程式設計的資料結構</span><span class="sxs-lookup"><span data-stu-id="d4eec-118">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|<span data-ttu-id="d4eec-119">提供安全執行緒集合類別、輕量型同步處理類型和延遲初始設定類型的文件連結。</span><span class="sxs-lookup"><span data-stu-id="d4eec-119">Provides links to documentation for thread-safe collection classes, lightweight synchronization types, and types for lazy initialization.</span></span>|
|[<span data-ttu-id="d4eec-120">平行診斷工具</span><span class="sxs-lookup"><span data-stu-id="d4eec-120">Parallel Diagnostic Tools</span></span>](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|<span data-ttu-id="d4eec-121">提供工作與平行堆疊的 Visual Studio 偵錯工具視窗文件連結，以及[並行視覺化工具](/visualstudio/profiling/concurrency-visualizer)的連結。</span><span class="sxs-lookup"><span data-stu-id="d4eec-121">Provides links to documentation for Visual Studio debugger windows for tasks and parallel stacks, and for the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>|
|[<span data-ttu-id="d4eec-122">PLINQ 和 TPL 的自訂 Partitioner</span><span class="sxs-lookup"><span data-stu-id="d4eec-122">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|<span data-ttu-id="d4eec-123">說明 Partitioner 的運作方式，以及如何設定預設 Partitioner 或建立新的 Partitioner。</span><span class="sxs-lookup"><span data-stu-id="d4eec-123">Describes how partitioners work and how to configure the default partitioners or create a new partitioner.</span></span>|
|[<span data-ttu-id="d4eec-124">工作排程器</span><span class="sxs-lookup"><span data-stu-id="d4eec-124">Task Schedulers</span></span>](xref:System.Threading.Tasks.TaskScheduler)|<span data-ttu-id="d4eec-125">說明排程器的運作方式以及如何設定預設排程器。</span><span class="sxs-lookup"><span data-stu-id="d4eec-125">Describes how schedulers work and how the default schedulers may be configured.</span></span>|
|[<span data-ttu-id="d4eec-126">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d4eec-126">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|<span data-ttu-id="d4eec-127">提供 C# 和 Visual Basic 中之 Lambda 運算式的簡短概觀，並且顯示如何在 PLINQ 和工作平行程式庫中使用這些運算式。</span><span class="sxs-lookup"><span data-stu-id="d4eec-127">Provides a brief overview of lambda expressions in C# and Visual Basic, and shows how they are used in PLINQ and the Task Parallel Library.</span></span>|
|[<span data-ttu-id="d4eec-128">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="d4eec-128">For Further Reading</span></span>](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|<span data-ttu-id="d4eec-129">提供以 .NET 進行平行程式設計的額外資訊和範例資源連結。</span><span class="sxs-lookup"><span data-stu-id="d4eec-129">Provides links to additional information and sample resources for parallel programming in .NET.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d4eec-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4eec-130">See also</span></span>

- [<span data-ttu-id="d4eec-131">非同步總覽</span><span class="sxs-lookup"><span data-stu-id="d4eec-131">Async Overview</span></span>](../async.md)
- [<span data-ttu-id="d4eec-132">受控執行緒處理</span><span class="sxs-lookup"><span data-stu-id="d4eec-132">Managed Threading</span></span>](../threading/index.md)
