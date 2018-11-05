---
title: 在分組作業上執行子查詢 (C# 中的 LINQ)
description: 如何使用 C# 中的 LINQ 在分組作業上執行子查詢。
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 19be93fe695982e93abea9a59153a4245dce4a60
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846314"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="43219-103">在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="43219-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="43219-104">本文說明兩種不同的建立查詢方式，將來源資料排序成群組，然後個別對每個群組執行子查詢。</span><span class="sxs-lookup"><span data-stu-id="43219-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="43219-105">每個範例中的基本技巧是使用名為 `newGroup` 的「接續」來分組來源元素，然後針對 `newGroup` 產生新的子查詢。</span><span class="sxs-lookup"><span data-stu-id="43219-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="43219-106">這個子查詢會針對外部查詢所建立的每個新群組執行。</span><span class="sxs-lookup"><span data-stu-id="43219-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="43219-107">請注意，在這個特別的範例中，最終輸出不是群組，而是匿名型別的一般序列。</span><span class="sxs-lookup"><span data-stu-id="43219-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="43219-108">如需如何分組的詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="43219-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="43219-109">如需接續的詳細資訊，請參閱 [into](../language-reference/keywords/into.md)。</span><span class="sxs-lookup"><span data-stu-id="43219-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="43219-110">下列範例將記憶體內部資料結構用為資料來源，但是相同的原則也適用於任何一種 LINQ 資料來源。</span><span class="sxs-lookup"><span data-stu-id="43219-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43219-111">範例</span><span class="sxs-lookup"><span data-stu-id="43219-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="43219-112">這個範例包含[查詢物件的集合](query-a-collection-of-objects.md)中範例程式碼中定義的物件參考。</span><span class="sxs-lookup"><span data-stu-id="43219-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)] 

<span data-ttu-id="43219-113">上述程式碼片段中的查詢也可以使用方法語法來撰寫。</span><span class="sxs-lookup"><span data-stu-id="43219-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="43219-114">下列程式碼片段有使用方法語法撰寫的語意對等查詢。</span><span class="sxs-lookup"><span data-stu-id="43219-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="43219-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43219-115">See also</span></span>

- [<span data-ttu-id="43219-116">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="43219-116">Language Integrated Query (LINQ)</span></span>](index.md)
