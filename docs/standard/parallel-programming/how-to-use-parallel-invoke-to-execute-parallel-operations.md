---
title: 如何：使用 Parallel.Invoke 執行平行作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 7189c478e132a41971a364b833f0fabda6ff84d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588403"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="e6e71-102">如何：使用 Parallel.Invoke 執行平行作業</span><span class="sxs-lookup"><span data-stu-id="e6e71-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="e6e71-103">這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。</span><span class="sxs-lookup"><span data-stu-id="e6e71-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="e6e71-104">我們會對共用資料來源執行三項作業。</span><span class="sxs-lookup"><span data-stu-id="e6e71-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="e6e71-105">這些作業都不會修改來源，因此可以直接平行執行。</span><span class="sxs-lookup"><span data-stu-id="e6e71-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="e6e71-106">本文件使用 Lambda 運算式來定義 TPL 中的委派。</span><span class="sxs-lookup"><span data-stu-id="e6e71-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="e6e71-107">如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="e6e71-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6e71-108">範例</span><span class="sxs-lookup"><span data-stu-id="e6e71-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="e6e71-109">請注意，使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 時，您只需指出要並行執行的動作即可，執行階段會處理所有執行緒排程詳細資料，包括自動根據主機電腦的核心數進行調整。</span><span class="sxs-lookup"><span data-stu-id="e6e71-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="e6e71-110">這個範例會平行處理作業，而不是資料。</span><span class="sxs-lookup"><span data-stu-id="e6e71-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="e6e71-111">除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e6e71-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="e6e71-112">或者，您可以使用 PLINQ 來平行處理資料。</span><span class="sxs-lookup"><span data-stu-id="e6e71-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="e6e71-113">另一種方式是同時平行處理查詢和工作。</span><span class="sxs-lookup"><span data-stu-id="e6e71-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="e6e71-114">雖然產生的額外負荷可能會使處理器數目相對較少的主機電腦效能減低，但將更適用在具有較多處理器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e6e71-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e6e71-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e6e71-115">Compile the Code</span></span>

<span data-ttu-id="e6e71-116">將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。</span><span class="sxs-lookup"><span data-stu-id="e6e71-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6e71-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6e71-117">See also</span></span>

- [<span data-ttu-id="e6e71-118">平行編程式</span><span class="sxs-lookup"><span data-stu-id="e6e71-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="e6e71-119">如何：取消工作及其子系</span><span class="sxs-lookup"><span data-stu-id="e6e71-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="e6e71-120">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e6e71-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
