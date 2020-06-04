---
title: From 子句
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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396177"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="adb13-102">From 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb13-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="adb13-103">指定一個或多個範圍變數，以及要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="adb13-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb13-104">語法</span><span class="sxs-lookup"><span data-stu-id="adb13-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="adb13-105">組件</span><span class="sxs-lookup"><span data-stu-id="adb13-105">Parts</span></span>  
  
|<span data-ttu-id="adb13-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="adb13-106">Term</span></span>|<span data-ttu-id="adb13-107">定義</span><span class="sxs-lookup"><span data-stu-id="adb13-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="adb13-108">必要。</span><span class="sxs-lookup"><span data-stu-id="adb13-108">Required.</span></span> <span data-ttu-id="adb13-109">用來逐一查看集合元素的*範圍變數*。</span><span class="sxs-lookup"><span data-stu-id="adb13-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="adb13-110">當查詢逐一查看時，範圍變數會用來參考的每個成員 `collection` `collection` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="adb13-111">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="adb13-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="adb13-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="adb13-112">Optional.</span></span> <span data-ttu-id="adb13-113">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="adb13-113">The type of `element`.</span></span> <span data-ttu-id="adb13-114">如果未 `type` 指定，則 `element` 會從推斷的類型 `collection` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="adb13-115">必要。</span><span class="sxs-lookup"><span data-stu-id="adb13-115">Required.</span></span> <span data-ttu-id="adb13-116">參考要查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="adb13-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="adb13-117">必須是可列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="adb13-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adb13-118">備註</span><span class="sxs-lookup"><span data-stu-id="adb13-118">Remarks</span></span>  
 <span data-ttu-id="adb13-119">`From`子句是用來識別查詢的來源資料，以及用來從來源集合參考元素的變數。</span><span class="sxs-lookup"><span data-stu-id="adb13-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="adb13-120">這些變數稱為「*範圍變數*」。</span><span class="sxs-lookup"><span data-stu-id="adb13-120">These variables are called *range variables*.</span></span> <span data-ttu-id="adb13-121">`From`查詢需要子句，除非 `Aggregate` 使用子句來識別只傳回匯總結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="adb13-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="adb13-122">如需詳細資訊，請參閱[Aggregate 子句](aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="adb13-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="adb13-123">您可以 `From` 在查詢中指定多個子句，以識別要聯結的多個集合。</span><span class="sxs-lookup"><span data-stu-id="adb13-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="adb13-124">當指定多個集合時，會個別反復查看它們，或者您可以聯結它們（如果它們是相關的）。</span><span class="sxs-lookup"><span data-stu-id="adb13-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="adb13-125">您可以使用 `Select` 子句，或使用或子句明確地聯結集合 `Join` `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="adb13-126">或者，您可以在單一子句中指定多個範圍變數和集合 `From` ，並以逗號分隔每個相關的範圍變數和集合與其他專案。</span><span class="sxs-lookup"><span data-stu-id="adb13-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="adb13-127">下列程式碼範例顯示子句的兩個語法選項 `From` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="adb13-128">`From`子句會定義查詢的範圍，這與迴圈的範圍類似 `For` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="adb13-129">因此， `element` 查詢範圍中的每個範圍變數都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="adb13-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="adb13-130">因為您可以為查詢指定多個 `From` 子句，所以後續 `From` 子句可以參考子句中的範圍變數 `From` ，或參考上一個子句中的範圍變數 `From` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="adb13-131">例如，下列範例顯示的是一個 nested `From` 子句，其中第二個子句中的集合是以第一個子句中範圍變數的屬性為基礎。</span><span class="sxs-lookup"><span data-stu-id="adb13-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="adb13-132">每個 `From` 子句後面可以加上任何其他查詢子句的組合，以精簡查詢。</span><span class="sxs-lookup"><span data-stu-id="adb13-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="adb13-133">您可以利用下列方式來精簡查詢：</span><span class="sxs-lookup"><span data-stu-id="adb13-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="adb13-134">使用 `From` 和 `Select` 子句，或使用或子句明確地結合多個集合 `Join` `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="adb13-135">使用 `Where` 子句來篩選查詢結果。</span><span class="sxs-lookup"><span data-stu-id="adb13-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="adb13-136">使用子句來排序結果 `Order By` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="adb13-137">使用子句，將類似的結果群組在一起 `Group By` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="adb13-138">使用 `Aggregate` 子句來識別要評估整個查詢結果的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="adb13-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="adb13-139">使用 `Let` 子句來引進反覆運算變數，其值是由運算式（而非集合）所決定。</span><span class="sxs-lookup"><span data-stu-id="adb13-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="adb13-140">使用 `Distinct` 子句來忽略重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="adb13-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="adb13-141">使用 `Skip` 、、 `Take` `Skip While` 和子句，識別要傳回之結果的各個部分 `Take While` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb13-142">範例</span><span class="sxs-lookup"><span data-stu-id="adb13-142">Example</span></span>  
 <span data-ttu-id="adb13-143">下列查詢運算式會使用 `From` 子句， `cust` 針對集合中的每個物件宣告範圍變數 `Customer` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="adb13-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="adb13-144">`Where`子句會使用範圍變數，將輸出限制為來自指定區域的客戶。</span><span class="sxs-lookup"><span data-stu-id="adb13-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="adb13-145">`For Each`迴圈會在查詢結果中顯示每個客戶的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="adb13-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="adb13-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb13-146">See also</span></span>

- [<span data-ttu-id="adb13-147">查詢</span><span class="sxs-lookup"><span data-stu-id="adb13-147">Queries</span></span>](index.md)
- [<span data-ttu-id="adb13-148">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="adb13-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="adb13-149">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="adb13-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="adb13-150">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="adb13-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="adb13-151">Select 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="adb13-152">Where 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="adb13-153">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="adb13-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="adb13-154">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="adb13-155">Join 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="adb13-156">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="adb13-157">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="adb13-158">Let 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="adb13-159">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="adb13-160">Take 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="adb13-161">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="adb13-162">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="adb13-162">Take While Clause</span></span>](take-while-clause.md)
