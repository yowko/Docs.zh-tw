---
title: Join 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359770"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="9e2d9-102">Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e2d9-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="9e2d9-103">將兩個集合合併成單一集合。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="9e2d9-104">聯結作業是以相符的索引鍵為基礎，並使用 `Equals` 運算子。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e2d9-105">語法</span><span class="sxs-lookup"><span data-stu-id="9e2d9-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="9e2d9-106">組件</span><span class="sxs-lookup"><span data-stu-id="9e2d9-106">Parts</span></span>

<span data-ttu-id="9e2d9-107">需要 `element`。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-107">`element` Required.</span></span> <span data-ttu-id="9e2d9-108">要聯結之集合的控制項變數。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="9e2d9-109">必要。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-109">Required.</span></span> <span data-ttu-id="9e2d9-110">要與運算子左邊所識別之集合結合的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="9e2d9-111">`Join`子句可以嵌套在另一個 `Join` 子句或 `Group Join` 子句中。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="9e2d9-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-112">Optional.</span></span> <span data-ttu-id="9e2d9-113">一或多個額外 `Join` 的子句，可進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="9e2d9-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-114">Optional.</span></span> <span data-ttu-id="9e2d9-115">一或多個額外 `Group Join` 的子句，可進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="9e2d9-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="9e2d9-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="9e2d9-117">必要。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-117">Required.</span></span> <span data-ttu-id="9e2d9-118">識別要聯結之集合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="9e2d9-119">您必須使用 `Equals` 運算子來比較所聯結之集合中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="9e2d9-120">您可以使用 `And` 運算子來識別多個索引鍵，以結合聯結條件。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="9e2d9-121">`key1`必須來自運算子左邊的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="9e2d9-122">`key2`必須來自運算子右邊的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="9e2d9-123">聯結條件中使用的索引鍵可以是包含集合中一個以上專案的運算式。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="9e2d9-124">不過，每個索引鍵運算式只能包含其各自集合中的專案。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e2d9-125">備註</span><span class="sxs-lookup"><span data-stu-id="9e2d9-125">Remarks</span></span>

<span data-ttu-id="9e2d9-126">`Join`子句會根據聯結的集合中相符的索引鍵值，結合兩個集合。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="9e2d9-127">產生的集合可以包含運算子左邊所識別之集合中的任何值組合 `Join` ，以及在子句中識別的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="9e2d9-128">查詢只會傳回符合運算子所指定條件的結果 `Equals` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="9e2d9-129">這相當於 `INNER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="9e2d9-130">您可以 `Join` 在查詢中使用多個子句，將兩個或更多個集合聯結至單一集合。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="9e2d9-131">您可以執行隱含聯結來結合沒有子句的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="9e2d9-132">若要這麼做，請 `In` 在子句中包含多個子句， `From` 並指定一個 `Where` 子句來識別您想要用於聯結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="9e2d9-133">您可以使用 `Group Join` 子句，將集合合併成單一階層式集合。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="9e2d9-134">這就像 `LEFT OUTER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="9e2d9-135">範例</span><span class="sxs-lookup"><span data-stu-id="9e2d9-135">Example</span></span>

<span data-ttu-id="9e2d9-136">下列程式碼範例會執行隱含聯結，以結合客戶清單與訂單。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="9e2d9-137">範例</span><span class="sxs-lookup"><span data-stu-id="9e2d9-137">Example</span></span>

<span data-ttu-id="9e2d9-138">下列程式碼範例會使用子句聯結兩個集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="9e2d9-139">這個範例會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="9e2d9-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="9e2d9-140">範例</span><span class="sxs-lookup"><span data-stu-id="9e2d9-140">Example</span></span>

<span data-ttu-id="9e2d9-141">下列程式碼範例會使用子句搭配兩個索引鍵資料行來聯結兩個集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="9e2d9-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="9e2d9-142">此範例會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="9e2d9-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="9e2d9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e2d9-143">See also</span></span>

- [<span data-ttu-id="9e2d9-144">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="9e2d9-144">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9e2d9-145">查詢</span><span class="sxs-lookup"><span data-stu-id="9e2d9-145">Queries</span></span>](index.md)
- [<span data-ttu-id="9e2d9-146">Select 子句</span><span class="sxs-lookup"><span data-stu-id="9e2d9-146">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="9e2d9-147">From 子句</span><span class="sxs-lookup"><span data-stu-id="9e2d9-147">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="9e2d9-148">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="9e2d9-148">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="9e2d9-149">Where 子句</span><span class="sxs-lookup"><span data-stu-id="9e2d9-149">Where Clause</span></span>](where-clause.md)
