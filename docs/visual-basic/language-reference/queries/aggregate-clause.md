---
title: Aggregate 子句 (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 21781db637c71abbbe9366bc95b6ee4c89ac2246
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981955"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="54698-102">Aggregate 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54698-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="54698-103">適用於一或多個彙總函式集合。</span><span class="sxs-lookup"><span data-stu-id="54698-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54698-104">語法</span><span class="sxs-lookup"><span data-stu-id="54698-104">Syntax</span></span>  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="54698-105">組件</span><span class="sxs-lookup"><span data-stu-id="54698-105">Parts</span></span>  
  
|<span data-ttu-id="54698-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="54698-106">Term</span></span>|<span data-ttu-id="54698-107">定義</span><span class="sxs-lookup"><span data-stu-id="54698-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="54698-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="54698-108">Required.</span></span> <span data-ttu-id="54698-109">變數，可用來逐一查看集合的元素。</span><span class="sxs-lookup"><span data-stu-id="54698-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="54698-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="54698-110">Optional.</span></span> <span data-ttu-id="54698-111">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="54698-111">The type of `element`.</span></span> <span data-ttu-id="54698-112">如果未不指定任何類型，類型`element`推斷從`collection`。</span><span class="sxs-lookup"><span data-stu-id="54698-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="54698-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="54698-113">Required.</span></span> <span data-ttu-id="54698-114">指的是要處理的集合。</span><span class="sxs-lookup"><span data-stu-id="54698-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="54698-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="54698-115">Optional.</span></span> <span data-ttu-id="54698-116">一或多個查詢子句，例如`Where`子句，來限定要套用的彙總子句或子句的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="54698-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="54698-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="54698-117">Required.</span></span> <span data-ttu-id="54698-118">一或多個以逗點分隔運算式可識別要套用至集合的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="54698-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="54698-119">您可以將別名套用至指定成員名稱的查詢結果的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="54698-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="54698-120">如果未不提供任何別名，則會使用彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="54698-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="54698-121">如需範例，請參閱本主題稍後的彙總函式的相關章節。</span><span class="sxs-lookup"><span data-stu-id="54698-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54698-122">備註</span><span class="sxs-lookup"><span data-stu-id="54698-122">Remarks</span></span>  
 <span data-ttu-id="54698-123">`Aggregate`子句可以用來在您的查詢中包含彙總函式。</span><span class="sxs-lookup"><span data-stu-id="54698-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="54698-124">彙總函式會執行檢查及計算值的集合，並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="54698-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="54698-125">您可以使用查詢結果型別的成員，以存取計算的值。</span><span class="sxs-lookup"><span data-stu-id="54698-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="54698-126">您可以使用標準彙總函式`All`， `Any`， `Average`， `Count`， `LongCount`， `Max`， `Min`，以及`Sum`函式。</span><span class="sxs-lookup"><span data-stu-id="54698-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="54698-127">這些函式是熟悉的開發人員已熟悉 SQL 中的彙總。</span><span class="sxs-lookup"><span data-stu-id="54698-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="54698-128">它們都是以本主題的下一節所述。</span><span class="sxs-lookup"><span data-stu-id="54698-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="54698-129">查詢結果中包含的彙總函式的結果為查詢結果型別的欄位。</span><span class="sxs-lookup"><span data-stu-id="54698-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="54698-130">您可以提供彙總函式的結果，以指定的查詢結果型別，用以保存彙總值的成員名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="54698-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="54698-131">如果未不提供任何別名，則會使用彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="54698-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="54698-132">`Aggregate`子句可以開始查詢，或者它可以包含在查詢中的其他子句。</span><span class="sxs-lookup"><span data-stu-id="54698-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="54698-133">如果`Aggregate`子句開始查詢，則結果為單一值中指定的彙總函式的結果`Into`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="54698-134">如果一個以上的彙總函式中指定`Into`子句，查詢會傳回個別屬性來參考每個彙總函式的結果的單一類型`Into`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="54698-135">如果`Aggregate`子句會包含在查詢中的其他子句，查詢集合中傳回的型別就會有不同的屬性來參考每個彙總函式的結果`Into`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="54698-136">彙總函式</span><span class="sxs-lookup"><span data-stu-id="54698-136">Aggregate Functions</span></span>

<span data-ttu-id="54698-137">以下是適用於標準彙總函式`Aggregate`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="54698-138">全部</span><span class="sxs-lookup"><span data-stu-id="54698-138">All</span></span>

<span data-ttu-id="54698-139">會傳回`true`如果在集合中的所有項目符合指定的條件; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="54698-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="54698-140">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="54698-141">任何</span><span class="sxs-lookup"><span data-stu-id="54698-141">Any</span></span>

<span data-ttu-id="54698-142">會傳回`true`如果在集合中的任何項目符合指定的條件; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="54698-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="54698-143">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="54698-144">平均</span><span class="sxs-lookup"><span data-stu-id="54698-144">Average</span></span>

<span data-ttu-id="54698-145">計算集合中的所有項目的平均值，或計算提供的運算式，針對集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="54698-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="54698-146">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="54698-147">計數</span><span class="sxs-lookup"><span data-stu-id="54698-147">Count</span></span>

<span data-ttu-id="54698-148">計算集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="54698-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="54698-149">您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。</span><span class="sxs-lookup"><span data-stu-id="54698-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="54698-150">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="54698-151">群組</span><span class="sxs-lookup"><span data-stu-id="54698-151">Group</span></span>

<span data-ttu-id="54698-152">查詢結果的群組是指`Group By`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="54698-153">`Group`函式是僅適用於`Into`子句`Group By`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="54698-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="54698-154">如需詳細資訊和範例，請參閱 <<c0> [ 群組的子句](../../../visual-basic/language-reference/queries/group-by-clause.md)並[Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="54698-154">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="54698-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="54698-155">LongCount</span></span>

<span data-ttu-id="54698-156">計算集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="54698-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="54698-157">您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。</span><span class="sxs-lookup"><span data-stu-id="54698-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="54698-158">傳回結果做`Long`。</span><span class="sxs-lookup"><span data-stu-id="54698-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="54698-159">如需範例，請參閱`Count`彙總函式。</span><span class="sxs-lookup"><span data-stu-id="54698-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="54698-160">最大</span><span class="sxs-lookup"><span data-stu-id="54698-160">Max</span></span>

<span data-ttu-id="54698-161">從集合中的最大值或是計算集合中的所有項目的而提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="54698-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="54698-162">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="54698-163">最小</span><span class="sxs-lookup"><span data-stu-id="54698-163">Min</span></span>

<span data-ttu-id="54698-164">計算集合的最小值或計算提供的運算式，針對集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="54698-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="54698-165">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="54698-166">Sum</span><span class="sxs-lookup"><span data-stu-id="54698-166">Sum</span></span>

<span data-ttu-id="54698-167">集合中的所有項目的總和或是計算集合中的所有項目的而提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="54698-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="54698-168">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="54698-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="54698-169">範例</span><span class="sxs-lookup"><span data-stu-id="54698-169">Example</span></span>  

<span data-ttu-id="54698-170">下列範例示範如何使用`Aggregate`子句，以套用彙總函式，將查詢結果。</span><span class="sxs-lookup"><span data-stu-id="54698-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="54698-171">建立使用者定義彙總函式</span><span class="sxs-lookup"><span data-stu-id="54698-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="54698-172">您也可以加入擴充方法，以查詢運算式中包含您自己自訂的彙總函式<xref:System.Collections.Generic.IEnumerable%601>型別。</span><span class="sxs-lookup"><span data-stu-id="54698-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="54698-173">計算或參考您彙總函式的可列舉集合上的作業，接著可以執行您的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="54698-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="54698-174">如需擴充方法的詳細資訊，請參閱[擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="54698-174">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="54698-175">例如，下列範例顯示自訂的彙總函式會計算數字集合的中間值。</span><span class="sxs-lookup"><span data-stu-id="54698-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="54698-176">有兩個多載`Median`擴充方法。</span><span class="sxs-lookup"><span data-stu-id="54698-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="54698-177">第一個多載接受，做為輸入，型別集合`IEnumerable(Of Double)`。</span><span class="sxs-lookup"><span data-stu-id="54698-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="54698-178">如果`Median`彙總函式會呼叫類型的查詢欄位`Double`，會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="54698-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="54698-179">第二個多載`Median`方法可以傳遞任何泛型型別。</span><span class="sxs-lookup"><span data-stu-id="54698-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="54698-180">泛型多載`Median`方法會採用第二個參數會參考`Func(Of T, Double)`投影的類型 （集合） 的值類型的對應值的 lambda 運算式`Double`。</span><span class="sxs-lookup"><span data-stu-id="54698-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="54698-181">然後它會委派其他多載的中間值的計算`Median`方法。</span><span class="sxs-lookup"><span data-stu-id="54698-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="54698-182">如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="54698-182">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="54698-183">下列範例顯示範例查詢來呼叫`Median`彙總類型的集合上的函式`Integer`，和型別集合`Double`。</span><span class="sxs-lookup"><span data-stu-id="54698-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="54698-184">查詢會呼叫`Median`彙總類型的集合上的函式`Double`呼叫的多載`Median`做為輸入，接受型別集合的方式來`Double`。</span><span class="sxs-lookup"><span data-stu-id="54698-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="54698-185">查詢會呼叫`Median`彙總類型的集合上的函式`Integer`呼叫的泛型多載`Median`方法。</span><span class="sxs-lookup"><span data-stu-id="54698-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="54698-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54698-186">See also</span></span>

- [<span data-ttu-id="54698-187">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="54698-187">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="54698-188">查詢</span><span class="sxs-lookup"><span data-stu-id="54698-188">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="54698-189">Select 子句</span><span class="sxs-lookup"><span data-stu-id="54698-189">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="54698-190">From 子句</span><span class="sxs-lookup"><span data-stu-id="54698-190">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="54698-191">Where 子句</span><span class="sxs-lookup"><span data-stu-id="54698-191">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="54698-192">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="54698-192">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
