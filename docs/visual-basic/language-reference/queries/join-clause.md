---
title: "Join 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="64785-102">Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64785-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="64785-103">將兩個集合合併成單一集合。</span><span class="sxs-lookup"><span data-stu-id="64785-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="64785-104">根據相符索引鍵的聯結作業，並使用`Equals`運算子。</span><span class="sxs-lookup"><span data-stu-id="64785-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64785-105">語法</span><span class="sxs-lookup"><span data-stu-id="64785-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="64785-106">組件</span><span class="sxs-lookup"><span data-stu-id="64785-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="64785-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="64785-107">Required.</span></span> <span data-ttu-id="64785-108">所要加入之控制項的變數。</span><span class="sxs-lookup"><span data-stu-id="64785-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="64785-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="64785-109">Required.</span></span> <span data-ttu-id="64785-110">結合集合所識別的左邊集合`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="64785-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="64785-111">A`Join`子句可以巢狀方式置於另一個`Join`子句，或在`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="64785-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="64785-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="64785-112">Optional.</span></span> <span data-ttu-id="64785-113">一個以上的額外`Join`子句來進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="64785-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="64785-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="64785-114">Optional.</span></span> <span data-ttu-id="64785-115">一個以上的額外`Group Join`子句來進一步精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="64785-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="64785-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="64785-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="64785-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="64785-117">Required.</span></span> <span data-ttu-id="64785-118">識別要聯結之集合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="64785-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="64785-119">您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="64785-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="64785-120">您可以使用合併聯結條件`And`運算子來識別多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="64785-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="64785-121">`key1`從集合上的左側必須是`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="64785-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="64785-122">`key2`從集合中的右側必須是`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="64785-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="64785-123">聯結條件中使用的索引鍵可以是包含一個以上的項目集合中的運算式。</span><span class="sxs-lookup"><span data-stu-id="64785-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="64785-124">不過，每個索引鍵的運算式可以包含從其各自集合的項目。</span><span class="sxs-lookup"><span data-stu-id="64785-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64785-125">備註</span><span class="sxs-lookup"><span data-stu-id="64785-125">Remarks</span></span>  
 <span data-ttu-id="64785-126">`Join`子句結合兩個比對所聯結之集合中的索引鍵值為基礎的集合。</span><span class="sxs-lookup"><span data-stu-id="64785-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="64785-127">產生的集合可以包含任何的組合值集合所識別的左邊`Join`運算子和識別集合中`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="64785-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="64785-128">查詢會傳回的結果的條件指定由`Equals`運算子成立。</span><span class="sxs-lookup"><span data-stu-id="64785-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="64785-129">這相當於`INNER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="64785-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="64785-130">您可以使用多個`Join`来聯結成為單一集合的兩個或多個集合的查詢中的子句。</span><span class="sxs-lookup"><span data-stu-id="64785-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="64785-131">您可以執行隱含聯結來結合集合不含`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="64785-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="64785-132">若要這樣做，包括多個`In`子句中的您`From`子句，並指定`Where`識別您想要用於聯結的索引鍵的子句。</span><span class="sxs-lookup"><span data-stu-id="64785-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="64785-133">您可以使用`Group Join`子句結合成單一階層式集合的集合。</span><span class="sxs-lookup"><span data-stu-id="64785-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="64785-134">這就相當於`LEFT OUTER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="64785-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64785-135">範例</span><span class="sxs-lookup"><span data-stu-id="64785-135">Example</span></span>  
 <span data-ttu-id="64785-136">下列程式碼範例會執行隱含聯結以結合其訂單的客戶清單。</span><span class="sxs-lookup"><span data-stu-id="64785-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="64785-137">範例</span><span class="sxs-lookup"><span data-stu-id="64785-137">Example</span></span>  
 <span data-ttu-id="64785-138">下列程式碼範例會使用聯結兩個集合`Join`子句。</span><span class="sxs-lookup"><span data-stu-id="64785-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="64785-139">這個範例會產生類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="64785-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="64785-140">範例</span><span class="sxs-lookup"><span data-stu-id="64785-140">Example</span></span>  
 <span data-ttu-id="64785-141">下列程式碼範例會使用聯結兩個集合`Join`具有兩個索引鍵資料行子句。</span><span class="sxs-lookup"><span data-stu-id="64785-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="64785-142">此範例會產生類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="64785-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="64785-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64785-143">See Also</span></span>  
 [<span data-ttu-id="64785-144">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="64785-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="64785-145">查詢</span><span class="sxs-lookup"><span data-stu-id="64785-145">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="64785-146">Select 子句</span><span class="sxs-lookup"><span data-stu-id="64785-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="64785-147">From 子句</span><span class="sxs-lookup"><span data-stu-id="64785-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="64785-148">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="64785-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="64785-149">Where 子句</span><span class="sxs-lookup"><span data-stu-id="64785-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
