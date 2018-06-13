---
title: 將查詢結果分組
description: 如何分組結果。
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: cb7808bfdd86dd23882d0722b87b1e013a84141e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289031"
---
# <a name="group-query-results"></a><span data-ttu-id="c00a6-103">將查詢結果分組</span><span class="sxs-lookup"><span data-stu-id="c00a6-103">Group query results</span></span>

<span data-ttu-id="c00a6-104">分組是 LINQ 最強大的功能之一。</span><span class="sxs-lookup"><span data-stu-id="c00a6-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="c00a6-105">下例示範如何以各種方式分組資料︰</span><span class="sxs-lookup"><span data-stu-id="c00a6-105">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="c00a6-106">根據單一屬性。</span><span class="sxs-lookup"><span data-stu-id="c00a6-106">By a single property.</span></span>  
  
-   <span data-ttu-id="c00a6-107">根據字串屬性的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c00a6-107">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="c00a6-108">根據計算的數字範圍。</span><span class="sxs-lookup"><span data-stu-id="c00a6-108">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="c00a6-109">根據布林值述詞或其他運算式。</span><span class="sxs-lookup"><span data-stu-id="c00a6-109">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="c00a6-110">根據複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c00a6-110">By a compound key.</span></span>  
  
 <span data-ttu-id="c00a6-111">此外，最後兩個查詢會將其結果投射至只包含學生姓名的新匿名型別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="c00a6-112">如需詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c00a6-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c00a6-113">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-113">Example</span></span>  
 <span data-ttu-id="c00a6-114">本主題中的所有範例都使用下列的協助程式類別和資料來源。</span><span class="sxs-lookup"><span data-stu-id="c00a6-114">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c00a6-115">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-115">Example</span></span>  
 <span data-ttu-id="c00a6-116">下例示範如何將項目的單一屬性用為群組索引鍵，來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c00a6-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="c00a6-117">本例的索引鍵是 `string`，為學生的姓氏。</span><span class="sxs-lookup"><span data-stu-id="c00a6-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="c00a6-118">索引鍵也可以使用子字串。</span><span class="sxs-lookup"><span data-stu-id="c00a6-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="c00a6-119">群組作業在類型上會使用預設的相等比較子。</span><span class="sxs-lookup"><span data-stu-id="c00a6-119">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="c00a6-120">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c00a6-121">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySingleProperty()`。</span><span class="sxs-lookup"><span data-stu-id="c00a6-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="c00a6-122">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-122">Example</span></span>  
 <span data-ttu-id="c00a6-123">下例示範如何在群組索引鍵使用物件屬性以外的項目分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c00a6-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="c00a6-124">本例的索引鍵是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c00a6-124">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="c00a6-125">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c00a6-126">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySubstring()`。</span><span class="sxs-lookup"><span data-stu-id="c00a6-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="c00a6-127">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-127">Example</span></span>  
 <span data-ttu-id="c00a6-128">下例示範如何將數字範圍用為群組索引鍵來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c00a6-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="c00a6-129">查詢接著會將結果投射到只包含姓名及學生所屬百分位數範圍的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="c00a6-130">使用匿名型別是因為沒必要使用完整的 `Student` 物件來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c00a6-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="c00a6-131">`GetPercentile` 是根據學生平均分數計算百分位數的 Helper 函式。</span><span class="sxs-lookup"><span data-stu-id="c00a6-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="c00a6-132">方法會傳回 0 到 10 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="c00a6-132">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="c00a6-133">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c00a6-134">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByRange()`。</span><span class="sxs-lookup"><span data-stu-id="c00a6-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="c00a6-135">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-135">Example</span></span>  
 <span data-ttu-id="c00a6-136">下例示範如何使用布林比較運算式來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c00a6-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="c00a6-137">在本例中，布林運算式會測試學生的平均測驗分數是否大於 75。</span><span class="sxs-lookup"><span data-stu-id="c00a6-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="c00a6-138">同上例，結果會投射至匿名型別，因為不需要完整的來源項目。</span><span class="sxs-lookup"><span data-stu-id="c00a6-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="c00a6-139">請注意，匿名型別中的屬性會成為 `Key` 成員上的屬性，並可在執行查詢時依名稱存取。</span><span class="sxs-lookup"><span data-stu-id="c00a6-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="c00a6-140">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c00a6-141">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByBoolean()`。</span><span class="sxs-lookup"><span data-stu-id="c00a6-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="c00a6-142">範例</span><span class="sxs-lookup"><span data-stu-id="c00a6-142">Example</span></span>  
 <span data-ttu-id="c00a6-143">下例示範如何使用匿名型別來封裝包含多個值的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c00a6-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="c00a6-144">本例的第一個索引鍵值是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c00a6-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="c00a6-145">第二個索引鍵值是布林值，指定學生第一次的考試分數是否超過 85。</span><span class="sxs-lookup"><span data-stu-id="c00a6-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="c00a6-146">您可以索引鍵中的任何屬性來排序群組。</span><span class="sxs-lookup"><span data-stu-id="c00a6-146">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="c00a6-147">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c00a6-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c00a6-148">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByCompositeKey()`。</span><span class="sxs-lookup"><span data-stu-id="c00a6-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c00a6-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c00a6-149">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="c00a6-150">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="c00a6-150">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="c00a6-151">group 子句</span><span class="sxs-lookup"><span data-stu-id="c00a6-151">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="c00a6-152">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c00a6-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="c00a6-153">在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="c00a6-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="c00a6-154">建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="c00a6-154">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="c00a6-155">分組資料</span><span class="sxs-lookup"><span data-stu-id="c00a6-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
