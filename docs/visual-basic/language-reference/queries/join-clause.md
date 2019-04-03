---
title: Join 子句 (Visual Basic)
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
ms.openlocfilehash: 21432b95b30ae38ac2cbc9e55b5a3066f0bef665
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825842"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="c9e1b-102">Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9e1b-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="c9e1b-103">將兩個集合合併成單一集合。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="c9e1b-104">根據相符的索引鍵的聯結作業，並使用`Equals`運算子。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e1b-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9e1b-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c9e1b-106">組件</span><span class="sxs-lookup"><span data-stu-id="c9e1b-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="c9e1b-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-107">Required.</span></span> <span data-ttu-id="c9e1b-108">要聯結之集合的控制變數。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="c9e1b-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-109">Required.</span></span> <span data-ttu-id="c9e1b-110">要結合的左邊識別集合的集合`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="c9e1b-111">A`Join`子句可以巢狀方式置於另一個`Join`子句，或在`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="c9e1b-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-112">Optional.</span></span> <span data-ttu-id="c9e1b-113">一個以上的額外`Join`子句，以進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="c9e1b-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-114">Optional.</span></span> <span data-ttu-id="c9e1b-115">一個以上的額外`Group Join`子句，以進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="c9e1b-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="c9e1b-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="c9e1b-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-117">Required.</span></span> <span data-ttu-id="c9e1b-118">識別要聯結之集合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="c9e1b-119">您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="c9e1b-120">您可以使用合併聯結條件`And`運算子來識別多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="c9e1b-121">`key1` 必須從左側集合`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="c9e1b-122">`key2` 從集合中的右側必須是`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="c9e1b-123">聯結條件中使用索引鍵可以包含一個以上的項目從集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="c9e1b-124">不過，每個索引鍵的運算式可以包含從其個別集合的項目。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9e1b-125">備註</span><span class="sxs-lookup"><span data-stu-id="c9e1b-125">Remarks</span></span>  
 <span data-ttu-id="c9e1b-126">`Join`子句結合兩個集合根據比對所聯結之集合中的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="c9e1b-127">產生的集合可以包含任何的組合值集合所識別的左邊`Join`運算子，並識別集合中`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="c9e1b-128">查詢會傳回所指定的條件的結果`Equals`運算子成立。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="c9e1b-129">這相當於`INNER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="c9e1b-130">您可以使用多個`Join`查詢中，以聯結成單一集合的兩個或多個集合的子句。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="c9e1b-131">您可以執行隱含聯結來結合沒有集合`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="c9e1b-132">若要這樣做，包括多個`In`子句，在您`From`子句，並指定`Where`子句，用來識別您想要用於聯結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="c9e1b-133">您可以使用`Group Join`子句結合成單一階層式集合的集合。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="c9e1b-134">這就像是`LEFT OUTER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9e1b-135">範例</span><span class="sxs-lookup"><span data-stu-id="c9e1b-135">Example</span></span>  
 <span data-ttu-id="c9e1b-136">下列程式碼範例會執行隱含聯結結合其訂單的客戶清單。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="c9e1b-137">範例</span><span class="sxs-lookup"><span data-stu-id="c9e1b-137">Example</span></span>  
 <span data-ttu-id="c9e1b-138">下列程式碼範例以使用聯結兩個集合`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 <span data-ttu-id="c9e1b-139">此範例會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="c9e1b-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="c9e1b-140">範例</span><span class="sxs-lookup"><span data-stu-id="c9e1b-140">Example</span></span>  
 <span data-ttu-id="c9e1b-141">下列程式碼範例以使用聯結兩個集合`Join`子句搭配兩個索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="c9e1b-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 <span data-ttu-id="c9e1b-142">此範例會產生如下所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="c9e1b-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="c9e1b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e1b-143">See also</span></span>

- [<span data-ttu-id="c9e1b-144">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="c9e1b-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c9e1b-145">查詢</span><span class="sxs-lookup"><span data-stu-id="c9e1b-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c9e1b-146">Select 子句</span><span class="sxs-lookup"><span data-stu-id="c9e1b-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c9e1b-147">From 子句</span><span class="sxs-lookup"><span data-stu-id="c9e1b-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c9e1b-148">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="c9e1b-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="c9e1b-149">Where 子句</span><span class="sxs-lookup"><span data-stu-id="c9e1b-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
