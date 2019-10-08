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
ms.openlocfilehash: 50a53cd45cc428541c90fbf82089518be2212fae
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004801"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="cbade-102">Aggregate 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbade-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="cbade-103">將一個或多個彙總函式套用至集合。</span><span class="sxs-lookup"><span data-stu-id="cbade-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbade-104">語法</span><span class="sxs-lookup"><span data-stu-id="cbade-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="cbade-105">組件</span><span class="sxs-lookup"><span data-stu-id="cbade-105">Parts</span></span>  
  
|<span data-ttu-id="cbade-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="cbade-106">Term</span></span>|<span data-ttu-id="cbade-107">定義</span><span class="sxs-lookup"><span data-stu-id="cbade-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="cbade-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbade-108">Required.</span></span> <span data-ttu-id="cbade-109">變數，用來逐一查看集合的元素。</span><span class="sxs-lookup"><span data-stu-id="cbade-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="cbade-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cbade-110">Optional.</span></span> <span data-ttu-id="cbade-111">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cbade-111">The type of `element`.</span></span> <span data-ttu-id="cbade-112">如果未指定類型，則會從 `collection` 推斷 `element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cbade-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="cbade-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbade-113">Required.</span></span> <span data-ttu-id="cbade-114">參考要在其上操作的集合。</span><span class="sxs-lookup"><span data-stu-id="cbade-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="cbade-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cbade-115">Optional.</span></span> <span data-ttu-id="cbade-116">一或多個查詢子句（例如 `Where` 子句），以精簡查詢結果，以套用匯總子句或子句。</span><span class="sxs-lookup"><span data-stu-id="cbade-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="cbade-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbade-117">Required.</span></span> <span data-ttu-id="cbade-118">一或多個以逗號分隔的運算式，可識別要套用至集合的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="cbade-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="cbade-119">您可以將別名套用至彙總函式，以指定查詢結果的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="cbade-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="cbade-120">如果未提供別名，則會使用彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbade-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="cbade-121">如需範例，請參閱本主題稍後的關於彙總函式的一節。</span><span class="sxs-lookup"><span data-stu-id="cbade-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbade-122">備註</span><span class="sxs-lookup"><span data-stu-id="cbade-122">Remarks</span></span>  
 <span data-ttu-id="cbade-123">@No__t-0 子句可以用來在查詢中包含彙總函式。</span><span class="sxs-lookup"><span data-stu-id="cbade-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="cbade-124">彙總函式會對一組值執行檢查和計算，並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="cbade-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="cbade-125">您可以使用查詢結果類型的成員來存取計算的值。</span><span class="sxs-lookup"><span data-stu-id="cbade-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="cbade-126">您可以使用的標準彙總函式為 `All`、`Any`、`Average`、`Count`、`LongCount`、`Max`、`Min` 和 `Sum` 函數。</span><span class="sxs-lookup"><span data-stu-id="cbade-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="cbade-127">這些函式對於熟悉 SQL 中匯總的開發人員而言是很熟悉的。</span><span class="sxs-lookup"><span data-stu-id="cbade-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="cbade-128">本主題的下一節將說明這些功能。</span><span class="sxs-lookup"><span data-stu-id="cbade-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="cbade-129">彙總函式的結果會當做查詢結果類型的欄位，包含在查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="cbade-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="cbade-130">您可以提供彙總函式結果的別名，以指定將保留匯總值之查詢結果類型的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="cbade-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="cbade-131">如果未提供別名，則會使用彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbade-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="cbade-132">@No__t 0 子句可以開始查詢，也可以在查詢中包含為額外的子句。</span><span class="sxs-lookup"><span data-stu-id="cbade-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="cbade-133">如果 `Aggregate` 子句開始查詢，則結果會是單一值，這是在 `Into` 子句中指定之彙總函式的結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="cbade-134">如果在 `Into` 子句中指定了一個以上的彙總函式，則查詢會傳回具有個別屬性的單一類型，以參考 `Into` 子句中每個彙總函式的結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="cbade-135">如果 `Aggregate` 子句包含為查詢中的其他子句，則查詢集合中傳回的類型會有不同的屬性，可參考 `Into` 子句中每個彙總函式的結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="cbade-136">彙總函式</span><span class="sxs-lookup"><span data-stu-id="cbade-136">Aggregate Functions</span></span>

<span data-ttu-id="cbade-137">以下是可搭配 `Aggregate` 子句使用的標準彙總函式。</span><span class="sxs-lookup"><span data-stu-id="cbade-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="cbade-138">全部</span><span class="sxs-lookup"><span data-stu-id="cbade-138">All</span></span>

<span data-ttu-id="cbade-139">如果集合中的所有元素都符合指定的條件，則傳回 `true`：否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="cbade-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="cbade-140">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="cbade-141">Any</span><span class="sxs-lookup"><span data-stu-id="cbade-141">Any</span></span>

<span data-ttu-id="cbade-142">如果集合中有任何元素符合指定的條件，則傳回 `true`;否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="cbade-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="cbade-143">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="cbade-144">Average</span><span class="sxs-lookup"><span data-stu-id="cbade-144">Average</span></span>

<span data-ttu-id="cbade-145">計算集合中所有專案的平均值，或計算集合中所有元素的提供運算式。</span><span class="sxs-lookup"><span data-stu-id="cbade-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cbade-146">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="cbade-147">Count</span><span class="sxs-lookup"><span data-stu-id="cbade-147">Count</span></span>

<span data-ttu-id="cbade-148">計算集合中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="cbade-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="cbade-149">您可以提供選擇性的 `Boolean` 運算式，只計算集合中滿足條件的元素數目。</span><span class="sxs-lookup"><span data-stu-id="cbade-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="cbade-150">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="cbade-151">群組</span><span class="sxs-lookup"><span data-stu-id="cbade-151">Group</span></span>

<span data-ttu-id="cbade-152">指的是將查詢結果分組為 `Group By` 或 @no__t 1 子句的結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="cbade-153">@No__t-0 函數只在 `Group By` 或 `Group Join` 子句的 `Into` 子句中有效。</span><span class="sxs-lookup"><span data-stu-id="cbade-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="cbade-154">如需詳細資訊和範例，請參閱[Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)和[group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="cbade-154">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="cbade-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="cbade-155">LongCount</span></span>

<span data-ttu-id="cbade-156">計算集合中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="cbade-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="cbade-157">您可以提供選擇性的 `Boolean` 運算式，只計算集合中滿足條件的元素數目。</span><span class="sxs-lookup"><span data-stu-id="cbade-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="cbade-158">以 `Long` 的形式傳回結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="cbade-159">如需範例，請參閱 `Count` 彙總函式。</span><span class="sxs-lookup"><span data-stu-id="cbade-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="cbade-160">max</span><span class="sxs-lookup"><span data-stu-id="cbade-160">Max</span></span>

<span data-ttu-id="cbade-161">計算集合中的最大值，或針對集合中的所有元素計算提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="cbade-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cbade-162">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="cbade-163">Min</span><span class="sxs-lookup"><span data-stu-id="cbade-163">Min</span></span>

<span data-ttu-id="cbade-164">計算集合中的最小值，或針對集合中的所有元素計算提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="cbade-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cbade-165">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="cbade-166">Sum</span><span class="sxs-lookup"><span data-stu-id="cbade-166">Sum</span></span>

<span data-ttu-id="cbade-167">計算集合中所有專案的總和，或針對集合中的所有元素計算提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="cbade-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="cbade-168">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="cbade-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="cbade-169">範例</span><span class="sxs-lookup"><span data-stu-id="cbade-169">Example</span></span>  

<span data-ttu-id="cbade-170">下列範例顯示如何使用 `Aggregate` 子句，將彙總函式套用至查詢結果。</span><span class="sxs-lookup"><span data-stu-id="cbade-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="cbade-171">建立使用者定義彙總函式</span><span class="sxs-lookup"><span data-stu-id="cbade-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="cbade-172">您可以藉由將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 類型，在查詢運算式中包含您自己的自訂彙總函式。</span><span class="sxs-lookup"><span data-stu-id="cbade-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="cbade-173">然後，您的自訂方法就可以在已參考彙總函式的可列舉集合上執行計算或作業。</span><span class="sxs-lookup"><span data-stu-id="cbade-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="cbade-174">如需擴充方法的詳細資訊，請參閱[擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="cbade-174">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="cbade-175">例如，下列範例顯示的自訂彙總函式會計算數位集合的中間值。</span><span class="sxs-lookup"><span data-stu-id="cbade-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="cbade-176">@No__t 0 擴充方法有兩個多載。</span><span class="sxs-lookup"><span data-stu-id="cbade-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="cbade-177">第一個多載會接受 `IEnumerable(Of Double)` 類型的集合做為輸入。</span><span class="sxs-lookup"><span data-stu-id="cbade-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="cbade-178">如果對 `Double` 類型的查詢欄位呼叫 `Median` 彙總函式，則會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="cbade-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="cbade-179">@No__t-0 方法的第二個多載可以傳遞任何泛型型別。</span><span class="sxs-lookup"><span data-stu-id="cbade-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="cbade-180">@No__t-0 方法的泛型多載會採用第二個參數，參考 @no__t 1 lambda 運算式來投影類型的值（從集合）做為類型 `Double` 的對應值。</span><span class="sxs-lookup"><span data-stu-id="cbade-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="cbade-181">然後，它會將中間值的計算委派給 `Median` 方法的其他多載。</span><span class="sxs-lookup"><span data-stu-id="cbade-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="cbade-182">如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="cbade-182">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="cbade-183">下列範例會顯示在 `Integer` 類型的集合上呼叫 `Median` 彙總函式的範例查詢，以及 `Double` 類型的集合。</span><span class="sxs-lookup"><span data-stu-id="cbade-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="cbade-184">在類型的集合上呼叫 `Median` 彙總函式的查詢 `Double` 會呼叫可接受做為輸入之類型集合 `Double` 的 @no__t 2 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="cbade-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="cbade-185">在類型的集合上呼叫 `Median` 彙總函式的查詢 `Integer` 會呼叫 @no__t 2 方法的泛型多載。</span><span class="sxs-lookup"><span data-stu-id="cbade-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="cbade-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbade-186">See also</span></span>

- [<span data-ttu-id="cbade-187">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="cbade-187">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="cbade-188">查詢</span><span class="sxs-lookup"><span data-stu-id="cbade-188">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="cbade-189">Select 子句</span><span class="sxs-lookup"><span data-stu-id="cbade-189">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="cbade-190">From 子句</span><span class="sxs-lookup"><span data-stu-id="cbade-190">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="cbade-191">Where 子句</span><span class="sxs-lookup"><span data-stu-id="cbade-191">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="cbade-192">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="cbade-192">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
