---
title: From 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004775"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="75534-102">From 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75534-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="75534-103">指定一個或多個範圍變數，以及要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="75534-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75534-104">語法</span><span class="sxs-lookup"><span data-stu-id="75534-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="75534-105">組件</span><span class="sxs-lookup"><span data-stu-id="75534-105">Parts</span></span>  
  
|<span data-ttu-id="75534-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="75534-106">Term</span></span>|<span data-ttu-id="75534-107">定義</span><span class="sxs-lookup"><span data-stu-id="75534-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="75534-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="75534-108">Required.</span></span> <span data-ttu-id="75534-109">用來逐一查看集合元素的*範圍變數*。</span><span class="sxs-lookup"><span data-stu-id="75534-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="75534-110">範圍變數是用來在查詢逐一查看 `collection` 時，參考 @no__t 0 的每個成員。</span><span class="sxs-lookup"><span data-stu-id="75534-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="75534-111">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="75534-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="75534-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="75534-112">Optional.</span></span> <span data-ttu-id="75534-113">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="75534-113">The type of `element`.</span></span> <span data-ttu-id="75534-114">如果未指定 `type`，則會從 `collection` 推斷 `element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="75534-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="75534-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="75534-115">Required.</span></span> <span data-ttu-id="75534-116">參考要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="75534-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="75534-117">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="75534-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75534-118">備註</span><span class="sxs-lookup"><span data-stu-id="75534-118">Remarks</span></span>  
 <span data-ttu-id="75534-119">@No__t-0 子句是用來識別查詢的來源資料，以及用來從來源集合參考元素的變數。</span><span class="sxs-lookup"><span data-stu-id="75534-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="75534-120">這些變數稱為「*範圍變數*」。</span><span class="sxs-lookup"><span data-stu-id="75534-120">These variables are called *range variables*.</span></span> <span data-ttu-id="75534-121">除非使用 `Aggregate` 子句來識別只傳回匯總結果的查詢，否則查詢需要 `From` 子句。</span><span class="sxs-lookup"><span data-stu-id="75534-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="75534-122">如需詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="75534-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="75534-123">您可以在查詢中指定多個 @no__t 0 子句，以識別要聯結的多個集合。</span><span class="sxs-lookup"><span data-stu-id="75534-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="75534-124">當指定多個集合時，會個別反復查看它們，或者您可以聯結它們（如果它們是相關的）。</span><span class="sxs-lookup"><span data-stu-id="75534-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="75534-125">您可以使用 `Select` 子句，或使用 `Join` 或 @no__t 2 子句明確地聯結集合。</span><span class="sxs-lookup"><span data-stu-id="75534-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="75534-126">或者，您可以在單一 `From` 子句中指定多個範圍變數和集合，其中每個相關的範圍變數和集合都是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="75534-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="75534-127">下列程式碼範例顯示 `From` 子句的兩個語法選項。</span><span class="sxs-lookup"><span data-stu-id="75534-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="75534-128">@No__t-0 子句會定義查詢的範圍，這類似于 @no__t 1 迴圈的範圍。</span><span class="sxs-lookup"><span data-stu-id="75534-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="75534-129">因此，查詢範圍中的每個 @no__t 0 範圍變數都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="75534-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="75534-130">因為您可以為查詢指定多個 `From` 子句，所以後續的 @no__t 1 子句可以參考 `From` 子句中的範圍變數，或參考前一個 `From` 子句中的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="75534-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="75534-131">例如，下列範例會顯示一個 nested `From` 子句，其中第二個子句中的集合是以第一個子句中範圍變數的屬性為基礎。</span><span class="sxs-lookup"><span data-stu-id="75534-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="75534-132">每個 @no__t 0 子句後面都可以加上任何其他查詢子句的組合，以精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="75534-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="75534-133">您可以利用下列方式來精簡查詢：</span><span class="sxs-lookup"><span data-stu-id="75534-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="75534-134">使用 `From` 和 `Select` 子句，或使用 `Join` 或 `Group Join` 子句明確地結合多個集合。</span><span class="sxs-lookup"><span data-stu-id="75534-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="75534-135">使用 `Where` 子句來篩選查詢結果。</span><span class="sxs-lookup"><span data-stu-id="75534-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="75534-136">使用 `Order By` 子句來排序結果。</span><span class="sxs-lookup"><span data-stu-id="75534-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="75534-137">使用 `Group By` 子句，將類似的結果群組在一起。</span><span class="sxs-lookup"><span data-stu-id="75534-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="75534-138">您可以使用 `Aggregate` 子句來識別要評估整個查詢結果的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="75534-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="75534-139">使用 `Let` 子句來引進反覆運算變數，其值是由運算式（而非集合）所決定。</span><span class="sxs-lookup"><span data-stu-id="75534-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="75534-140">使用 `Distinct` 子句來忽略重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="75534-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="75534-141">使用 `Skip`、`Take`、`Skip While` 和 `Take While` 子句，識別要傳回的結果部分。</span><span class="sxs-lookup"><span data-stu-id="75534-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75534-142">範例</span><span class="sxs-lookup"><span data-stu-id="75534-142">Example</span></span>  
 <span data-ttu-id="75534-143">下列查詢運算式會使用 `From` 子句，針對 `customers` 集合中的每個 @no__t 2 物件，宣告範圍變數 `cust`。</span><span class="sxs-lookup"><span data-stu-id="75534-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="75534-144">@No__t-0 子句會使用範圍變數，將輸出限制為來自指定區域的客戶。</span><span class="sxs-lookup"><span data-stu-id="75534-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="75534-145">[@No__t-0] 迴圈會在查詢結果中顯示每個客戶的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="75534-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="75534-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75534-146">See also</span></span>

- [<span data-ttu-id="75534-147">查詢</span><span class="sxs-lookup"><span data-stu-id="75534-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="75534-148">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="75534-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="75534-149">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="75534-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="75534-150">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="75534-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="75534-151">Select 子句</span><span class="sxs-lookup"><span data-stu-id="75534-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="75534-152">Where 子句</span><span class="sxs-lookup"><span data-stu-id="75534-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="75534-153">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="75534-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="75534-154">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="75534-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="75534-155">Join 子句</span><span class="sxs-lookup"><span data-stu-id="75534-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="75534-156">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="75534-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="75534-157">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="75534-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="75534-158">Let 子句</span><span class="sxs-lookup"><span data-stu-id="75534-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="75534-159">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="75534-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="75534-160">Take 子句</span><span class="sxs-lookup"><span data-stu-id="75534-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="75534-161">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="75534-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="75534-162">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="75534-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
