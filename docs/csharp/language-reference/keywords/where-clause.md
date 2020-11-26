---
description: where 子句 - C# 參考
title: where 子句 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141682"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="dd9be-103">where 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dd9be-103">where clause (C# Reference)</span></span>

<span data-ttu-id="dd9be-104">`where` 子句用於查詢運算式中，以指定將在查詢運算式中傳回資料來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="dd9be-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="dd9be-105">它會將布林值條件 (*predicate*) 套用到每個來源項目 (透過範圍變數所參考)，並傳回所指定條件為 true 的項目。</span><span class="sxs-lookup"><span data-stu-id="dd9be-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="dd9be-106">單一查詢運算式可能會包含多個 `where` 子句，而單一子句可能會包含多個述詞子運算式。</span><span class="sxs-lookup"><span data-stu-id="dd9be-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="dd9be-107">範例</span><span class="sxs-lookup"><span data-stu-id="dd9be-107">Example</span></span>

<span data-ttu-id="dd9be-108">在下列範例中，`where` 子句會篩選掉不小於五的所有數字。</span><span class="sxs-lookup"><span data-stu-id="dd9be-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="dd9be-109">如果您移除 `where` 子句，則會傳回資料來源中的所有數字。</span><span class="sxs-lookup"><span data-stu-id="dd9be-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="dd9be-110">`num < 5` 運算式是套用至每個項目的述詞。</span><span class="sxs-lookup"><span data-stu-id="dd9be-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="dd9be-111">範例</span><span class="sxs-lookup"><span data-stu-id="dd9be-111">Example</span></span>

<span data-ttu-id="dd9be-112">在單一 `where` 子句內，您可以使用 [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) 和 [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) 運算子，視需要指定多個述詞。</span><span class="sxs-lookup"><span data-stu-id="dd9be-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="dd9be-113">在下列範例中，查詢會指定兩個述詞，只選取小於五的偶數。</span><span class="sxs-lookup"><span data-stu-id="dd9be-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="dd9be-114">範例</span><span class="sxs-lookup"><span data-stu-id="dd9be-114">Example</span></span>

<span data-ttu-id="dd9be-115">`where` 子句可能包含一個或多個傳回布林值的方法。</span><span class="sxs-lookup"><span data-stu-id="dd9be-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="dd9be-116">在下列範例中，`where` 子句使用方法來判斷範圍變數的目前值是偶數還是奇數。</span><span class="sxs-lookup"><span data-stu-id="dd9be-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="dd9be-117">備註</span><span class="sxs-lookup"><span data-stu-id="dd9be-117">Remarks</span></span>

<span data-ttu-id="dd9be-118">`where` 子句是篩選機制。</span><span class="sxs-lookup"><span data-stu-id="dd9be-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="dd9be-119">它幾乎可以放在查詢運算式中的任何位置，但不能是第一個或最後一個子句。</span><span class="sxs-lookup"><span data-stu-id="dd9be-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="dd9be-120">`where` 子句可能出現在 [group](group-clause.md) 子句之前或之後，取決於必須在分組來源項目之前還是之後進行篩選。</span><span class="sxs-lookup"><span data-stu-id="dd9be-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="dd9be-121">如果指定的述詞不適用於資料來源中的項目，則會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd9be-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="dd9be-122">這是 LINQ 提供的強型別檢查的其中一個優點。</span><span class="sxs-lookup"><span data-stu-id="dd9be-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="dd9be-123">在編譯時間，`where` 關鍵字會轉換為 <xref:System.Linq.Enumerable.Where%2A> 標準查詢運算子方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd9be-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd9be-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9be-124">See also</span></span>

- [<span data-ttu-id="dd9be-125">LINQ)  (查詢關鍵字 </span><span class="sxs-lookup"><span data-stu-id="dd9be-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="dd9be-126">from 子句</span><span class="sxs-lookup"><span data-stu-id="dd9be-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="dd9be-127">select 子句</span><span class="sxs-lookup"><span data-stu-id="dd9be-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="dd9be-128">篩選資料</span><span class="sxs-lookup"><span data-stu-id="dd9be-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="dd9be-129">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="dd9be-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="dd9be-130">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="dd9be-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
