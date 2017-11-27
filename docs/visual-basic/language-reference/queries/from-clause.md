---
title: "From 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="8b2e2-102">From 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b2e2-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="8b2e2-103">指定一或多個範圍變數以及要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b2e2-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="8b2e2-105">組件</span><span class="sxs-lookup"><span data-stu-id="8b2e2-105">Parts</span></span>  
  
|<span data-ttu-id="8b2e2-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="8b2e2-106">Term</span></span>|<span data-ttu-id="8b2e2-107">定義</span><span class="sxs-lookup"><span data-stu-id="8b2e2-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="8b2e2-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-108">Required.</span></span> <span data-ttu-id="8b2e2-109">A*範圍變數*用來逐一查看集合的元素。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="8b2e2-110">範圍變數用來參考的每個成員`collection`如逐一查看查詢`collection`。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="8b2e2-111">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="8b2e2-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-112">Optional.</span></span> <span data-ttu-id="8b2e2-113">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-113">The type of `element`.</span></span> <span data-ttu-id="8b2e2-114">如果沒有`type`指定的型別`element`推斷從`collection`。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="8b2e2-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-115">Required.</span></span> <span data-ttu-id="8b2e2-116">是指要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="8b2e2-117">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b2e2-118">備註</span><span class="sxs-lookup"><span data-stu-id="8b2e2-118">Remarks</span></span>  
 <span data-ttu-id="8b2e2-119">`From`子句用來識別來源資料查詢，包括用來參考項目的來源集合的變數。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="8b2e2-120">這些變數稱為*範圍變數*。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-120">These variables are called *range variables*.</span></span> <span data-ttu-id="8b2e2-121">`From`子句是必要的查詢，除非`Aggregate`子句用來識別傳回只會彙總結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="8b2e2-122">如需詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="8b2e2-123">您可以指定多個`From`查詢中，以識別要加入多個集合的子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="8b2e2-124">當指定多個集合時，它們各自獨立地重複處理，或您可以將其聯結如果它們相關。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="8b2e2-125">使用隱含聯結集合`Select`子句，或明確地使用`Join`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="8b2e2-126">或者，您可以指定多個範圍變數和集合中單一`From`子句，具有每個相關的範圍變數以及與其他以逗號分隔的集合。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="8b2e2-127">下列程式碼範例顯示兩個語法選項`From`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="8b2e2-128">`From`子句定義的範圍內的類似查詢的範圍`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="8b2e2-129">因此，每個`element`查詢範圍中的範圍變數必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="8b2e2-130">因為您可以指定多個`From`子句的查詢時，後續`From`子句可以參考中的範圍變數`From`子句，或者也可以參考的範圍變數中前一個`From`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="8b2e2-131">例如，下列範例顯示巢狀`From`子句，其中第二個子句中的集合根據第一個子句中的範圍變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="8b2e2-132">每個`From`子句後面可以接著以精簡查詢的其他查詢子句的任何組合。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="8b2e2-133">您可以下列方式來縮小查詢：</span><span class="sxs-lookup"><span data-stu-id="8b2e2-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="8b2e2-134">使用隱含結合多個集合`From`和`Select`子句，或明確地使用`Join`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="8b2e2-135">使用`Where`子句來篩選查詢結果。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="8b2e2-136">使用排序結果`Order By`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="8b2e2-137">利用群組類似的結果`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="8b2e2-138">使用`Aggregate`子句，以識別要評估的整個查詢結果的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="8b2e2-139">使用`Let`引入反覆運算變數的值取決於運算式而不是集合的子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="8b2e2-140">使用`Distinct`子句來略過重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="8b2e2-141">使用傳回的結果的部分識別為`Skip`， `Take`， `Skip While`，和`Take While`子句。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b2e2-142">範例</span><span class="sxs-lookup"><span data-stu-id="8b2e2-142">Example</span></span>  
 <span data-ttu-id="8b2e2-143">下列查詢運算式使用`From`子句來宣告範圍變數`cust`每個`Customer`物件存放至`customers`集合。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="8b2e2-144">`Where`子句來限制輸出給客戶，從指定的地區中使用的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="8b2e2-145">`For Each`迴圈會顯示查詢結果中的每個客戶的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="8b2e2-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8b2e2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b2e2-146">See Also</span></span>  
 [<span data-ttu-id="8b2e2-147">查詢</span><span class="sxs-lookup"><span data-stu-id="8b2e2-147">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="8b2e2-148">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="8b2e2-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="8b2e2-149">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="8b2e2-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="8b2e2-150">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="8b2e2-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="8b2e2-151">Select 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="8b2e2-152">Where 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="8b2e2-153">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="8b2e2-154">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="8b2e2-155">Join 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="8b2e2-156">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="8b2e2-157">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="8b2e2-158">Let 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="8b2e2-159">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="8b2e2-160">Take 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="8b2e2-161">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="8b2e2-162">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="8b2e2-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
