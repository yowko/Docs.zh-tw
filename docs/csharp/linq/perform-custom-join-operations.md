---
title: 執行自訂的聯結作業 (C# 中的 LINQ)
description: 了解如何在 C# 中執行自訂的 LINQ 聯結作業。
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659848"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="1c231-103">執行自訂的聯結作業</span><span class="sxs-lookup"><span data-stu-id="1c231-103">Perform custom join operations</span></span>

<span data-ttu-id="1c231-104">此範例示範如何執行無法使用 `join` 子句的聯結作業。</span><span class="sxs-lookup"><span data-stu-id="1c231-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="1c231-105">在查詢運算式中，`join` 子句限於等聯結並已最佳化，是目前為止最常見的聯結運算類型。</span><span class="sxs-lookup"><span data-stu-id="1c231-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="1c231-106">執行等聯結時，使用 `join` 子句可能一律會獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="1c231-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="1c231-107">不過，`join` 子句不能用在下列情況︰</span><span class="sxs-lookup"><span data-stu-id="1c231-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="1c231-108">不等式運算式中預測有聯結時 (非等聯結)。</span><span class="sxs-lookup"><span data-stu-id="1c231-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="1c231-109">多個等式或不等式運算式中預測有聯結時。</span><span class="sxs-lookup"><span data-stu-id="1c231-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="1c231-110">當您必須在聯結作業之前，引入右側 (內部) 序列的暫時範圍變數時。</span><span class="sxs-lookup"><span data-stu-id="1c231-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="1c231-111">若要執行非等聯結的聯結，您可以使用多個 `from` 子句個別引入每個資料來源。</span><span class="sxs-lookup"><span data-stu-id="1c231-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="1c231-112">然後，在 `where` 子句中套用述詞運算式，設定每個來源的變數範圍。</span><span class="sxs-lookup"><span data-stu-id="1c231-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="1c231-113">運算式也可以採用方法呼叫的形式。</span><span class="sxs-lookup"><span data-stu-id="1c231-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="1c231-114">請勿將這類的自訂聯結運算與使用多個 `from` 子句來存取內部集合相混淆。</span><span class="sxs-lookup"><span data-stu-id="1c231-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="1c231-115">有關詳細資訊，請參閱[聯接子句](../language-reference/keywords/join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="1c231-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c231-116">範例</span><span class="sxs-lookup"><span data-stu-id="1c231-116">Example</span></span>

<span data-ttu-id="1c231-117">下例的第一種方法示範簡單的交叉聯結。</span><span class="sxs-lookup"><span data-stu-id="1c231-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="1c231-118">交叉聯結必須謹慎使用，因為它們會產生非常龐大的結果集。</span><span class="sxs-lookup"><span data-stu-id="1c231-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="1c231-119">不過，它們在某些針對執行額外查詢建立來源序列的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="1c231-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="1c231-120">第二個方法會產生一系列類別識別碼列在左側 [類別] 清單中的所有產品。</span><span class="sxs-lookup"><span data-stu-id="1c231-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="1c231-121">請注意使用 `let` 子句和 `Contains` 方法來建立暫存陣列。</span><span class="sxs-lookup"><span data-stu-id="1c231-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="1c231-122">您也可以在查詢前建立陣列，並排除第一個 `from` 子句。</span><span class="sxs-lookup"><span data-stu-id="1c231-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="1c231-123">範例</span><span class="sxs-lookup"><span data-stu-id="1c231-123">Example</span></span>

<span data-ttu-id="1c231-124">在下例中，如果內部 (右側) 序列不能出現在 join 子句之前，查詢必須根據相符的索引鍵聯結兩個序列。</span><span class="sxs-lookup"><span data-stu-id="1c231-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="1c231-125">如果此聯結是使用 `join` 子句執行，則每個項目都必須呼叫 `Split` 方法。</span><span class="sxs-lookup"><span data-stu-id="1c231-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="1c231-126">使用多個 `from` 子句可讓查詢避免重複方法呼叫的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="1c231-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="1c231-127">不過，由於 `join` 已最佳化，在此特例中可能仍比使用多個 `from` 子句快。</span><span class="sxs-lookup"><span data-stu-id="1c231-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="1c231-128">結果主要隨方法呼叫的昂貴程度而不同。</span><span class="sxs-lookup"><span data-stu-id="1c231-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="1c231-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c231-129">See also</span></span>

- [<span data-ttu-id="1c231-130">語言綜合查詢（LINQ）</span><span class="sxs-lookup"><span data-stu-id="1c231-130">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="1c231-131">聯接子句</span><span class="sxs-lookup"><span data-stu-id="1c231-131">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="1c231-132">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="1c231-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
