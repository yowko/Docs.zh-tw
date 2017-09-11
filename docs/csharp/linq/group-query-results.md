---
title: "將查詢結果分組"
description: "如何分組結果。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1c1639651699afbe5fb768db26b98a9b2d734315
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="group-query-results"></a><span data-ttu-id="c359e-104">將查詢結果分組</span><span class="sxs-lookup"><span data-stu-id="c359e-104">Group query results</span></span>

<span data-ttu-id="c359e-105">分組是 LINQ 最強大的功能之一。</span><span class="sxs-lookup"><span data-stu-id="c359e-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="c359e-106">下例示範如何以各種方式分組資料︰</span><span class="sxs-lookup"><span data-stu-id="c359e-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="c359e-107">根據單一屬性。</span><span class="sxs-lookup"><span data-stu-id="c359e-107">By a single property.</span></span>  
  
-   <span data-ttu-id="c359e-108">根據字串屬性的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c359e-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="c359e-109">根據計算的數字範圍。</span><span class="sxs-lookup"><span data-stu-id="c359e-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="c359e-110">根據布林值述詞或其他運算式。</span><span class="sxs-lookup"><span data-stu-id="c359e-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="c359e-111">根據複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c359e-111">By a compound key.</span></span>  
  
 <span data-ttu-id="c359e-112">此外，最後兩個查詢會將其結果投射至只包含學生姓名的新匿名型別。</span><span class="sxs-lookup"><span data-stu-id="c359e-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="c359e-113">如需詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c359e-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-114">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-114">Example</span></span>  
 <span data-ttu-id="c359e-115">本主題中的所有範例都使用下列的協助程式類別和資料來源。</span><span class="sxs-lookup"><span data-stu-id="c359e-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 <span data-ttu-id="c359e-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-117">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-117">Example</span></span>  
 <span data-ttu-id="c359e-118">下例示範如何將項目的單一屬性用為群組索引鍵，來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c359e-118">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="c359e-119">本例的索引鍵是 `string`，為學生的姓氏。</span><span class="sxs-lookup"><span data-stu-id="c359e-119">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="c359e-120">索引鍵也可以使用子字串。</span><span class="sxs-lookup"><span data-stu-id="c359e-120">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="c359e-121">群組作業在類型上會使用預設的相等比較子。</span><span class="sxs-lookup"><span data-stu-id="c359e-121">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="c359e-122">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c359e-122">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c359e-123">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySingleProperty()`。</span><span class="sxs-lookup"><span data-stu-id="c359e-123">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 <span data-ttu-id="c359e-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-125">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-125">Example</span></span>  
 <span data-ttu-id="c359e-126">下例示範如何在群組索引鍵使用物件屬性以外的項目分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c359e-126">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="c359e-127">本例的索引鍵是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c359e-127">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="c359e-128">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c359e-128">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c359e-129">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySubstring()`。</span><span class="sxs-lookup"><span data-stu-id="c359e-129">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 <span data-ttu-id="c359e-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-131">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-131">Example</span></span>  
 <span data-ttu-id="c359e-132">下例示範如何將數字範圍用為群組索引鍵來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c359e-132">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="c359e-133">查詢接著會將結果投射到只包含姓名及學生所屬百分位數範圍的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="c359e-133">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="c359e-134">使用匿名型別是因為沒必要使用完整的 `Student` 物件來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c359e-134">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="c359e-135">`GetPercentile` 是根據學生平均分數計算百分位數的 Helper 函式。</span><span class="sxs-lookup"><span data-stu-id="c359e-135">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="c359e-136">方法會傳回 0 到 10 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="c359e-136">The method returns an integer between 0 and 10.</span></span>  
  
 <span data-ttu-id="c359e-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span></span>  
  
 <span data-ttu-id="c359e-138">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c359e-138">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c359e-139">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByRange()`。</span><span class="sxs-lookup"><span data-stu-id="c359e-139">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 <span data-ttu-id="c359e-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-141">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-141">Example</span></span>  
 <span data-ttu-id="c359e-142">下例示範如何使用布林比較運算式來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="c359e-142">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="c359e-143">在本例中，布林運算式會測試學生的平均測驗分數是否大於 75。</span><span class="sxs-lookup"><span data-stu-id="c359e-143">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="c359e-144">同上例，結果會投射至匿名型別，因為不需要完整的來源項目。</span><span class="sxs-lookup"><span data-stu-id="c359e-144">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="c359e-145">請注意，匿名型別中的屬性會成為 `Key` 成員上的屬性，並可在執行查詢時依名稱存取。</span><span class="sxs-lookup"><span data-stu-id="c359e-145">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="c359e-146">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c359e-146">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c359e-147">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByBoolean()`。</span><span class="sxs-lookup"><span data-stu-id="c359e-147">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 <span data-ttu-id="c359e-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c359e-149">範例</span><span class="sxs-lookup"><span data-stu-id="c359e-149">Example</span></span>  
 <span data-ttu-id="c359e-150">下例示範如何使用匿名型別來封裝包含多個值的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c359e-150">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="c359e-151">本例的第一個索引鍵值是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="c359e-151">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="c359e-152">第二個索引鍵值是布林值，指定學生第一次的考試分數是否超過 85。</span><span class="sxs-lookup"><span data-stu-id="c359e-152">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="c359e-153">您可以索引鍵中的任何屬性來排序群組。</span><span class="sxs-lookup"><span data-stu-id="c359e-153">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="c359e-154">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="c359e-154">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c359e-155">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByCompositeKey()`。</span><span class="sxs-lookup"><span data-stu-id="c359e-155">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 <span data-ttu-id="c359e-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="c359e-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c359e-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="c359e-157">See also</span></span>  
 <span data-ttu-id="c359e-158"><xref:System.Linq.Enumerable.GroupBy%2A></span><span class="sxs-lookup"><span data-stu-id="c359e-158"><xref:System.Linq.Enumerable.GroupBy%2A></span></span>   
 <span data-ttu-id="c359e-159"><xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="c359e-159"><xref:System.Linq.IGrouping%602></span></span>   
 <span data-ttu-id="c359e-160">[LINQ 查詢運算式](index.md) </span><span class="sxs-lookup"><span data-stu-id="c359e-160">[LINQ Query Expressions](index.md) </span></span>  
 <span data-ttu-id="c359e-161">[group 子句](../language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c359e-161">[group clause](../language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="c359e-162">[匿名型別](../programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="c359e-162">[Anonymous Types](../programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="c359e-163">[在分組作業上執行子查詢](perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="c359e-163">[Perform a Subquery on a Grouping Operation](perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 <span data-ttu-id="c359e-164">[建立巢狀群組](create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="c359e-164">[Create a Nested Group](create-a-nested-group.md) </span></span>  
 [<span data-ttu-id="c359e-165">分組資料</span><span class="sxs-lookup"><span data-stu-id="c359e-165">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)

