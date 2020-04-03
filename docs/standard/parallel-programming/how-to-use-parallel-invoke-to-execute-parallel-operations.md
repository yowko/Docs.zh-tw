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
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635795"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="3351f-102">如何：使用 Parallel.Invoke 執行平行作業</span><span class="sxs-lookup"><span data-stu-id="3351f-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="3351f-103">這個範例示範如何使用工作平行程式庫中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 平行處理作業。</span><span class="sxs-lookup"><span data-stu-id="3351f-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="3351f-104">我們會對共用資料來源執行三項作業。</span><span class="sxs-lookup"><span data-stu-id="3351f-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="3351f-105">操作可以以簡單的方式並行執行,因為它們都無法修改源。</span><span class="sxs-lookup"><span data-stu-id="3351f-105">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="3351f-106">本文件使用 Lambda 運算式來定義 TPL 中的委派。</span><span class="sxs-lookup"><span data-stu-id="3351f-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="3351f-107">如果您不熟悉 C# 或 Visual Basic 中的 lambda 表示式,請參考[PLINQ 與 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="3351f-107">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="3351f-108">範例</span><span class="sxs-lookup"><span data-stu-id="3351f-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="3351f-109">使用<xref:System.Threading.Tasks.Parallel.Invoke%2A>時,只需表示要同時運行哪些操作,運行時即可處理所有線程計劃詳細資訊,包括自動縮放到主機上的內核數。</span><span class="sxs-lookup"><span data-stu-id="3351f-109">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="3351f-110">這個範例會平行處理作業，而不是資料。</span><span class="sxs-lookup"><span data-stu-id="3351f-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="3351f-111">除了前述方法以外，您也可以使用 PLINQ 來平行處理 LINQ 查詢，並依序執行查詢。</span><span class="sxs-lookup"><span data-stu-id="3351f-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="3351f-112">或者，您可以使用 PLINQ 來平行處理資料。</span><span class="sxs-lookup"><span data-stu-id="3351f-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="3351f-113">另一種方式是同時平行處理查詢和工作。</span><span class="sxs-lookup"><span data-stu-id="3351f-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="3351f-114">儘管產生的開銷可能會降低處理器相對較少的主機上的性能,但它在具有許多處理器的計算機上會更好地擴展。</span><span class="sxs-lookup"><span data-stu-id="3351f-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="3351f-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3351f-115">Compile the Code</span></span>

<span data-ttu-id="3351f-116">將整個範例複製並貼到 Microsoft Visual Studio 專案中，然後按 **F5** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3351f-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3351f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3351f-117">See also</span></span>

- [<span data-ttu-id="3351f-118">平行編程式</span><span class="sxs-lookup"><span data-stu-id="3351f-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="3351f-119">如何：取消工作及其子系</span><span class="sxs-lookup"><span data-stu-id="3351f-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="3351f-120">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3351f-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
