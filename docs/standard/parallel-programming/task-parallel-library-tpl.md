---
title: "工作平行程式庫 (TPL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: "37"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e1dcb10189405c368b3739020a7bfa875792184
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="task-parallel-library-tpl"></a><span data-ttu-id="2bf75-102">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="2bf75-102">Task Parallel Library (TPL)</span></span>
<span data-ttu-id="2bf75-103">工作平行程式庫 (TPL) 是 <xref:System.Threading?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks?displayProperty=nameWithType> 命名空間中的一組公用類型和 API。</span><span class="sxs-lookup"><span data-stu-id="2bf75-103">The Task Parallel Library (TPL) is a set of public types and APIs in the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Threading.Tasks?displayProperty=nameWithType> namespaces.</span></span> <span data-ttu-id="2bf75-104">TPL 的目的是透過簡化將平行處理原則和並行加入至應用程式的流程，讓開發人員更有生產力。</span><span class="sxs-lookup"><span data-stu-id="2bf75-104">The purpose of the TPL is to make developers more productive by simplifying the process of adding parallelism and concurrency to applications.</span></span> <span data-ttu-id="2bf75-105">TPL 可動態調整並行程度，最有效率地使用所有可用的處理器。</span><span class="sxs-lookup"><span data-stu-id="2bf75-105">The TPL scales the degree of concurrency dynamically to most efficiently use all the processors that are available.</span></span> <span data-ttu-id="2bf75-106">此外，TPL 還會處理工作分割、<xref:System.Threading.ThreadPool> 上執行緒的排程、取消支援、狀態管理和其他低階細節。</span><span class="sxs-lookup"><span data-stu-id="2bf75-106">In addition, the TPL handles the partitioning of the work, the scheduling of threads on the <xref:System.Threading.ThreadPool>, cancellation support, state management, and other low-level details.</span></span> <span data-ttu-id="2bf75-107">使用 TPL，可讓您發揮程式碼的最大效能，同時專注於程式所應完成的工作。</span><span class="sxs-lookup"><span data-stu-id="2bf75-107">By using TPL, you can maximize the performance of your code while focusing on the work that your program is designed to accomplish.</span></span>  
  
 <span data-ttu-id="2bf75-108">從開始[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，TPL 是撰寫多執行緒和平行程式碼的慣用的方式。</span><span class="sxs-lookup"><span data-stu-id="2bf75-108">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the TPL is the preferred way to write multithreaded and parallel code.</span></span> <span data-ttu-id="2bf75-109">但是，並非所有程式碼都適用於平行化作業；例如，如果迴圈只會在每個反覆項目執行少量工作，或是迴圈執行的反覆項目並不多，則平行化作業帶來的額外負荷可能會讓程式碼的執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="2bf75-109">However, not all code is suitable for parallelization; for example, if a loop performs only a small amount of work on each iteration, or it doesn't run for many iterations, then the overhead of parallelization can cause the code to run more slowly.</span></span> <span data-ttu-id="2bf75-110">再者，就像任何多執行緒執行碼，平行化作業會使程式執行變得複雜。</span><span class="sxs-lookup"><span data-stu-id="2bf75-110">Furthermore, parallelization like any multithreaded code adds complexity to your program execution.</span></span> <span data-ttu-id="2bf75-111">雖然 TPL 可簡化多執行緒案例，但建議您應先了解執行緒處理的基本概念 (例如鎖定、死結、競爭情況等)，以有效使用 TPL。</span><span class="sxs-lookup"><span data-stu-id="2bf75-111">Although the TPL simplifies multithreaded scenarios, we recommend that you have a basic understanding of threading concepts, for example, locks, deadlocks, and race conditions, so that you can use the TPL effectively.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="2bf75-112">相關主題</span><span class="sxs-lookup"><span data-stu-id="2bf75-112">Related Topics</span></span>  
  
|<span data-ttu-id="2bf75-113">標題</span><span class="sxs-lookup"><span data-stu-id="2bf75-113">Title</span></span>|<span data-ttu-id="2bf75-114">說明</span><span class="sxs-lookup"><span data-stu-id="2bf75-114">Description</span></span>|  
|-|-|  
|[<span data-ttu-id="2bf75-115">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="2bf75-115">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|<span data-ttu-id="2bf75-116">說明如何建立平行 `for` 和 `foreach` 迴圈 (在 Visual Basic 中為 `For` 和 `For Each`)。</span><span class="sxs-lookup"><span data-stu-id="2bf75-116">Describes how to create parallel `for` and `foreach` loops (`For` and `For Each` in Visual Basic).</span></span>|  
|[<span data-ttu-id="2bf75-117">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="2bf75-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|<span data-ttu-id="2bf75-118">說明如何使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> (以隱含方式) 或直接使用 <xref:System.Threading.Tasks.Task> 物件 (以明確方式) 建立和執行工作。</span><span class="sxs-lookup"><span data-stu-id="2bf75-118">Describes how to create and run tasks implicitly by using <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> or explicitly by using <xref:System.Threading.Tasks.Task> objects directly.</span></span>|  
|[<span data-ttu-id="2bf75-119">資料流程</span><span class="sxs-lookup"><span data-stu-id="2bf75-119">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|<span data-ttu-id="2bf75-120">說明如何使用 TPL 資料流程程式庫中的資料流程元件，以處理必須彼此通訊的多項作業，或是在資料可用時處理資料。</span><span class="sxs-lookup"><span data-stu-id="2bf75-120">Describes how to use the dataflow components in the TPL Dataflow Library to handle multiple operations that must communicate with one another or to process data as it becomes available.</span></span>|  
|[<span data-ttu-id="2bf75-121">使用具有其他非同步模式的 TPL</span><span class="sxs-lookup"><span data-stu-id="2bf75-121">Using TPL with Other Asynchronous Patterns</span></span>](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|<span data-ttu-id="2bf75-122">說明如何將 TPL 搭配 .NET 中的其他非同步模式使用</span><span class="sxs-lookup"><span data-stu-id="2bf75-122">Describes how to use TPL with other asynchronous patterns in .NET</span></span>|  
|[<span data-ttu-id="2bf75-123">資料和工作平行處理原則中可能出現的錯誤</span><span class="sxs-lookup"><span data-stu-id="2bf75-123">Potential Pitfalls in Data and Task Parallelism</span></span>](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|<span data-ttu-id="2bf75-124">說明一些常見陷阱以及如何避免這些陷阱。</span><span class="sxs-lookup"><span data-stu-id="2bf75-124">Describes some common pitfalls and how to avoid them.</span></span>|  
|[<span data-ttu-id="2bf75-125">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2bf75-125">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|<span data-ttu-id="2bf75-126">說明如何使用 LINQ 查詢達到資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="2bf75-126">Describes how to achieve data parallelism with LINQ queries.</span></span>|  
|[<span data-ttu-id="2bf75-127">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="2bf75-127">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)|<span data-ttu-id="2bf75-128">.NET 平行程式設計的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="2bf75-128">Top level node for .NET parallel programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bf75-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bf75-129">See Also</span></span>  
 [<span data-ttu-id="2bf75-130">使用 .NET Framework 進行平行程式設計的範例</span><span class="sxs-lookup"><span data-stu-id="2bf75-130">Samples for Parallel Programming with the .NET Framework</span></span>](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
