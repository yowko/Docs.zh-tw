---
title: 平行 LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c438170ec48f40e59f8710d4e3820d6e915bed5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903824"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="9ac61-102">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9ac61-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="9ac61-103">Parallel LINQ (PLINQ) 是平行實作的 LINQ to Objects。</span><span class="sxs-lookup"><span data-stu-id="9ac61-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="9ac61-104">PLINQ 實作了一組完整的 LINQ 標準查詢運算子來作為 <xref:System.Linq> 命名空間的擴充方法，並具有其他運算子可供平行作業使用。</span><span class="sxs-lookup"><span data-stu-id="9ac61-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="9ac61-105">PLINQ 結合了 LINQ 語法簡單易懂的特性以及平行程式設計的威力。</span><span class="sxs-lookup"><span data-stu-id="9ac61-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="9ac61-106">和以工作平行程式庫為目標的程式碼一樣，PLINQ 查詢會根據主機電腦的能力來以並行程度縮放。</span><span class="sxs-lookup"><span data-stu-id="9ac61-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="9ac61-107">在許多情況下，PLINQ 可以更有效率地使用主機電腦上的所有可用核心，來大幅增加 LINQ to Objects 查詢的速度。</span><span class="sxs-lookup"><span data-stu-id="9ac61-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="9ac61-108">提升效能可為桌面帶來高效能的運算能力。</span><span class="sxs-lookup"><span data-stu-id="9ac61-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ac61-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="9ac61-109">In This Section</span></span>  
 [<span data-ttu-id="9ac61-110">PLINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="9ac61-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="9ac61-111">認識 PLINQ 中的加速</span><span class="sxs-lookup"><span data-stu-id="9ac61-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="9ac61-112">PLINQ 中的順序保留</span><span class="sxs-lookup"><span data-stu-id="9ac61-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="9ac61-113">PLINQ 中的合併選項</span><span class="sxs-lookup"><span data-stu-id="9ac61-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9ac61-114">如何：建立並執行簡單的 PLINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="9ac61-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="9ac61-115">如何：控制 PLINQ 查詢中的順序</span><span class="sxs-lookup"><span data-stu-id="9ac61-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9ac61-116">如何：結合平行和循序 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="9ac61-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="9ac61-117">如何：處理 PLINQ 查詢中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="9ac61-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9ac61-118">如何：取消 PLINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="9ac61-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="9ac61-119">如何：撰寫自訂 PLINQ 彙總函式</span><span class="sxs-lookup"><span data-stu-id="9ac61-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="9ac61-120">如何：在 PLINQ 中指定執行模式</span><span class="sxs-lookup"><span data-stu-id="9ac61-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="9ac61-121">如何：在 PLINQ 中指定合併選項</span><span class="sxs-lookup"><span data-stu-id="9ac61-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9ac61-122">如何：使用 PLINQ 逐一查看檔案目錄</span><span class="sxs-lookup"><span data-stu-id="9ac61-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="9ac61-123">如何：測量 PLINQ 查詢效能</span><span class="sxs-lookup"><span data-stu-id="9ac61-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="9ac61-124">PLINQ 資料範例</span><span class="sxs-lookup"><span data-stu-id="9ac61-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ac61-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac61-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="9ac61-126">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="9ac61-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="9ac61-127">Language-Integrated Query (LINQ) - C#</span><span class="sxs-lookup"><span data-stu-id="9ac61-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="9ac61-128">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ac61-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
