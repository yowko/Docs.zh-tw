---
title: 作法：使用 Parallel.Invoke 執行平行作業
description: 請參閱如何使用工作平行程式庫中的 Parallel. Invoke 方法 (TPL) ，其會對 .NET 中的共用資料來源執行平行作業。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 6ec8f03216cc6225e909f5dc3128469047826166
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825477"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="ea165-103">作法：使用 Parallel.Invoke 執行平行作業</span><span class="sxs-lookup"><span data-stu-id="ea165-103">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="ea165-104">這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。</span><span class="sxs-lookup"><span data-stu-id="ea165-104">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="ea165-105">我們會對共用資料來源執行三項作業。</span><span class="sxs-lookup"><span data-stu-id="ea165-105">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="ea165-106">您可以直接以平行方式執行作業，因為它們都不會修改來源。</span><span class="sxs-lookup"><span data-stu-id="ea165-106">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="ea165-107">本文件使用 Lambda 運算式來定義 TPL 中的委派。</span><span class="sxs-lookup"><span data-stu-id="ea165-107">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="ea165-108">如果您不熟悉 c # 或 Visual Basic 中的 lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="ea165-108">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="ea165-109">範例</span><span class="sxs-lookup"><span data-stu-id="ea165-109">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="ea165-110">使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 時，您只需表達要並存執行的動作，而執行時間會處理所有線程排程詳細資料，包括自動調整為主電腦上的核心數目。</span><span class="sxs-lookup"><span data-stu-id="ea165-110">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="ea165-111">這個範例會平行處理作業，而不是資料。</span><span class="sxs-lookup"><span data-stu-id="ea165-111">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="ea165-112">除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ea165-112">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="ea165-113">或者，您可以使用 PLINQ 來平行處理資料。</span><span class="sxs-lookup"><span data-stu-id="ea165-113">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="ea165-114">另一種方式是同時平行處理查詢和工作。</span><span class="sxs-lookup"><span data-stu-id="ea165-114">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="ea165-115">雖然產生的額外負荷可能會降低具有相對較少處理器之主機電腦上的效能，但在具有許多處理器的電腦上更能調整其效能。</span><span class="sxs-lookup"><span data-stu-id="ea165-115">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="ea165-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ea165-116">Compile the Code</span></span>

<span data-ttu-id="ea165-117">將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。</span><span class="sxs-lookup"><span data-stu-id="ea165-117">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea165-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea165-118">See also</span></span>

- [<span data-ttu-id="ea165-119">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="ea165-119">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="ea165-120">作法：取消工作及其子系</span><span class="sxs-lookup"><span data-stu-id="ea165-120">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="ea165-121">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ea165-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
