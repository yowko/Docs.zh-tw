---
title: "select 子句 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f40bc26d1812e76ac618c5a0ddf23c4cef2700d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="56d64-102">select 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="56d64-102">select clause (C# Reference)</span></span>
<span data-ttu-id="56d64-103">在查詢運算式中，`select` 子句指定將在執行查詢時產生之值的類型。</span><span class="sxs-lookup"><span data-stu-id="56d64-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="56d64-104">結果是根據評估所有先前子句以及 `select` 子句本身中的任何運算式而來。</span><span class="sxs-lookup"><span data-stu-id="56d64-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="56d64-105">查詢運算式必須以 `select` 子句或 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句來終止。</span><span class="sxs-lookup"><span data-stu-id="56d64-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="56d64-106">下列範例示範查詢運算式中的簡單 `select` 子句。</span><span class="sxs-lookup"><span data-stu-id="56d64-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 <span data-ttu-id="56d64-107">`select` 子句所產生的序列類型可決定查詢變數 `queryHighScores` 的類型。</span><span class="sxs-lookup"><span data-stu-id="56d64-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="56d64-108">在最簡單的情況下，`select` 子句只會指定範圍變數。</span><span class="sxs-lookup"><span data-stu-id="56d64-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="56d64-109">這會導致傳回的序列將相同類型的項目包含為資料來源。</span><span class="sxs-lookup"><span data-stu-id="56d64-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="56d64-110">如需詳細資訊，請參閱 [LINQ 查詢作業中的類型關聯性](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="56d64-110">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="56d64-111">不過，`select` 子句也提供功能強大的機制，將來源資料轉換 (或「投影」) 為新的類型。</span><span class="sxs-lookup"><span data-stu-id="56d64-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="56d64-112">如需詳細資訊，請參閱[使用 LINQ 轉換資料 (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="56d64-112">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56d64-113">範例</span><span class="sxs-lookup"><span data-stu-id="56d64-113">Example</span></span>  
 <span data-ttu-id="56d64-114">下列範例示範 `select` 子句可接受的所有不同形式。</span><span class="sxs-lookup"><span data-stu-id="56d64-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="56d64-115">在每個查詢中，請注意 `select` 子句與「查詢變數」類型之間的關聯性 (`studentQuery1`、`studentQuery2`，依此類推)。</span><span class="sxs-lookup"><span data-stu-id="56d64-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 <span data-ttu-id="56d64-116">如前一個範例中的 `studentQuery8` 所示，您有時可能想要所傳回序列的項目只包含來源項目的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="56d64-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="56d64-117">盡量保持最少的所傳回序列，以降低記憶體需求，並提高查詢的執行速度。</span><span class="sxs-lookup"><span data-stu-id="56d64-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="56d64-118">做法是在 `select` 子句中建立匿名型別，並使用物件初始設定式以利用來源項目中的適當屬性來初始化它。</span><span class="sxs-lookup"><span data-stu-id="56d64-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="56d64-119">如需如何執行此作業的範例，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="56d64-119">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d64-120">備註</span><span class="sxs-lookup"><span data-stu-id="56d64-120">Remarks</span></span>  
 <span data-ttu-id="56d64-121">在編譯時間，`select` 子句會轉譯為 <xref:System.Linq.Enumerable.Select%2A> 標準查詢運算子的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="56d64-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d64-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56d64-122">See Also</span></span>  
 [<span data-ttu-id="56d64-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="56d64-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="56d64-124">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="56d64-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="56d64-125">from 子句</span><span class="sxs-lookup"><span data-stu-id="56d64-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="56d64-126">partial （方法） （C# 參考）</span><span class="sxs-lookup"><span data-stu-id="56d64-126">partial (Method) (C# Reference)</span></span>](../../../csharp/language-reference/keywords/partial-method.md)  
 [<span data-ttu-id="56d64-127">匿名類型</span><span class="sxs-lookup"><span data-stu-id="56d64-127">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="56d64-128">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="56d64-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="56d64-129">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="56d64-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
