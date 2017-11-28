---
title: "執行自訂的聯結作業"
description: "如何執行自訂的聯結作業。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="c7469-104">執行自訂的聯結作業</span><span class="sxs-lookup"><span data-stu-id="c7469-104">Perform custom join operations</span></span>

<span data-ttu-id="c7469-105">本例示範如何執行無法使用 `join` 子句的聯結作業。</span><span class="sxs-lookup"><span data-stu-id="c7469-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="c7469-106">在查詢運算式中，`join` 子句限於等聯結並已最佳化，是目前為止最常見的聯結運算類型。</span><span class="sxs-lookup"><span data-stu-id="c7469-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="c7469-107">執行等聯結時，使用 `join` 子句可能一律會獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="c7469-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="c7469-108">不過，`join` 子句不能用在下列情況︰</span><span class="sxs-lookup"><span data-stu-id="c7469-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="c7469-109">不等式運算式中預測有聯結時 (非等聯結)。</span><span class="sxs-lookup"><span data-stu-id="c7469-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="c7469-110">多個等式或不等式運算式中預測有聯結時。</span><span class="sxs-lookup"><span data-stu-id="c7469-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="c7469-111">當您必須在聯結作業之前，引入右側 (內部) 序列的暫時範圍變數時。</span><span class="sxs-lookup"><span data-stu-id="c7469-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="c7469-112">若要執行非等聯結的聯結，您可以使用多個 `from` 子句個別引入每個資料來源。</span><span class="sxs-lookup"><span data-stu-id="c7469-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="c7469-113">然後，在 `where` 子句中套用述詞運算式，設定每個來源的變數範圍。</span><span class="sxs-lookup"><span data-stu-id="c7469-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="c7469-114">運算式也可以採用方法呼叫的形式。</span><span class="sxs-lookup"><span data-stu-id="c7469-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7469-115">請勿將這類的自訂聯結運算與使用多個 `from` 子句來存取內部集合相混淆。</span><span class="sxs-lookup"><span data-stu-id="c7469-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="c7469-116">如需詳細資訊，請參閱 [join 子句](../language-reference/keywords/join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c7469-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7469-117">範例</span><span class="sxs-lookup"><span data-stu-id="c7469-117">Example</span></span>  
 <span data-ttu-id="c7469-118">下例的第一種方法示範簡單的交叉聯結。</span><span class="sxs-lookup"><span data-stu-id="c7469-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="c7469-119">交叉聯結必須謹慎使用，因為它們會產生非常龐大的結果集。</span><span class="sxs-lookup"><span data-stu-id="c7469-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="c7469-120">不過，它們在某些針對執行額外查詢建立來源序列的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="c7469-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="c7469-121">第二個方法會產生一系列類別識別碼列在左側 [類別] 清單中的所有產品。</span><span class="sxs-lookup"><span data-stu-id="c7469-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="c7469-122">請注意使用 `let` 子句和 `Contains` 方法來建立暫存陣列。</span><span class="sxs-lookup"><span data-stu-id="c7469-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="c7469-123">您也可以在查詢前建立陣列，並排除第一個 `from` 子句。</span><span class="sxs-lookup"><span data-stu-id="c7469-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c7469-124">範例</span><span class="sxs-lookup"><span data-stu-id="c7469-124">Example</span></span>  
 <span data-ttu-id="c7469-125">在下例中，如果內部 (右側) 序列不能出現在 join 子句之前，查詢必須根據相符的索引鍵聯結兩個序列。</span><span class="sxs-lookup"><span data-stu-id="c7469-125">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="c7469-126">如果此聯結是使用 `join` 子句執行，則每個項目都必須呼叫 `Split` 方法。</span><span class="sxs-lookup"><span data-stu-id="c7469-126">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="c7469-127">使用多個 `from` 子句可讓查詢避免重複方法呼叫的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c7469-127">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="c7469-128">不過，由於 `join` 已最佳化，在此特例中可能仍比使用多個 `from` 子句快。</span><span class="sxs-lookup"><span data-stu-id="c7469-128">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="c7469-129">結果主要隨方法呼叫的昂貴程度而不同。</span><span class="sxs-lookup"><span data-stu-id="c7469-129">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c7469-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7469-130">See also</span></span>  
 [<span data-ttu-id="c7469-131">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="c7469-131">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="c7469-132">join 子句</span><span class="sxs-lookup"><span data-stu-id="c7469-132">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="c7469-133">排序 Join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="c7469-133">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
