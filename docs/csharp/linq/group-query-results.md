---
title: 將查詢結果分組 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 將結果分組。
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857849"
---
# <a name="group-query-results"></a><span data-ttu-id="278d7-103">將查詢結果分組</span><span class="sxs-lookup"><span data-stu-id="278d7-103">Group query results</span></span>

<span data-ttu-id="278d7-104">分組是 LINQ 最強大的功能之一。</span><span class="sxs-lookup"><span data-stu-id="278d7-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="278d7-105">下例示範如何以各種方式分組資料︰</span><span class="sxs-lookup"><span data-stu-id="278d7-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="278d7-106">根據單一屬性。</span><span class="sxs-lookup"><span data-stu-id="278d7-106">By a single property.</span></span>

- <span data-ttu-id="278d7-107">根據字串屬性的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="278d7-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="278d7-108">根據計算的數字範圍。</span><span class="sxs-lookup"><span data-stu-id="278d7-108">By a computed numeric range.</span></span>

- <span data-ttu-id="278d7-109">根據布林值述詞或其他運算式。</span><span class="sxs-lookup"><span data-stu-id="278d7-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="278d7-110">根據複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="278d7-110">By a compound key.</span></span>

<span data-ttu-id="278d7-111">此外，最後兩個查詢會將其結果投射至只包含學生姓名的新匿名型別。</span><span class="sxs-lookup"><span data-stu-id="278d7-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="278d7-112">如需詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="278d7-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="278d7-113">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-113">Example</span></span>

<span data-ttu-id="278d7-114">本主題中的所有範例都使用下列的協助程式類別和資料來源。</span><span class="sxs-lookup"><span data-stu-id="278d7-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="278d7-115">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-115">Example</span></span>

<span data-ttu-id="278d7-116">下例示範如何將項目的單一屬性用為群組索引鍵，來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="278d7-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="278d7-117">本例的索引鍵是 `string`，為學生的姓氏。</span><span class="sxs-lookup"><span data-stu-id="278d7-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="278d7-118">索引鍵也可以使用子字串。</span><span class="sxs-lookup"><span data-stu-id="278d7-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="278d7-119">群組作業在類型上會使用預設的相等比較子。</span><span class="sxs-lookup"><span data-stu-id="278d7-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="278d7-120">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="278d7-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="278d7-121">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySingleProperty()`。</span><span class="sxs-lookup"><span data-stu-id="278d7-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="278d7-122">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-122">Example</span></span>

<span data-ttu-id="278d7-123">下例示範如何在群組索引鍵使用物件屬性以外的項目分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="278d7-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="278d7-124">本例的索引鍵是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="278d7-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="278d7-125">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="278d7-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="278d7-126">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySubstring()`。</span><span class="sxs-lookup"><span data-stu-id="278d7-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="278d7-127">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-127">Example</span></span>

<span data-ttu-id="278d7-128">下例示範如何將數字範圍用為群組索引鍵來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="278d7-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="278d7-129">查詢接著會將結果投射到只包含姓名及學生所屬百分位數範圍的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="278d7-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="278d7-130">使用匿名型別是因為沒必要使用完整的 `Student` 物件來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="278d7-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="278d7-131">`GetPercentile` 是根據學生平均分數計算百分位數的 Helper 函式。</span><span class="sxs-lookup"><span data-stu-id="278d7-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="278d7-132">方法會傳回 0 到 10 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="278d7-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="278d7-133">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="278d7-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="278d7-134">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByRange()`。</span><span class="sxs-lookup"><span data-stu-id="278d7-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="278d7-135">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-135">Example</span></span>

<span data-ttu-id="278d7-136">下例示範如何使用布林比較運算式來分組來源項目。</span><span class="sxs-lookup"><span data-stu-id="278d7-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="278d7-137">在本例中，布林運算式會測試學生的平均測驗分數是否大於 75。</span><span class="sxs-lookup"><span data-stu-id="278d7-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="278d7-138">同上例，結果會投射至匿名型別，因為不需要完整的來源項目。</span><span class="sxs-lookup"><span data-stu-id="278d7-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="278d7-139">請注意，匿名型別中的屬性會成為 `Key` 成員上的屬性，並可在執行查詢時依名稱存取。</span><span class="sxs-lookup"><span data-stu-id="278d7-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="278d7-140">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="278d7-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="278d7-141">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByBoolean()`。</span><span class="sxs-lookup"><span data-stu-id="278d7-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="278d7-142">範例</span><span class="sxs-lookup"><span data-stu-id="278d7-142">Example</span></span>

<span data-ttu-id="278d7-143">下例示範如何使用匿名型別來封裝包含多個值的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="278d7-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="278d7-144">本例的第一個索引鍵值是學生姓氏的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="278d7-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="278d7-145">第二個索引鍵值是布林值，指定學生第一次的考試分數是否超過 85。</span><span class="sxs-lookup"><span data-stu-id="278d7-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="278d7-146">您可以索引鍵中的任何屬性來排序群組。</span><span class="sxs-lookup"><span data-stu-id="278d7-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="278d7-147">將下列方法貼入 `StudentClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="278d7-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="278d7-148">將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByCompositeKey()`。</span><span class="sxs-lookup"><span data-stu-id="278d7-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="278d7-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="278d7-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="278d7-150">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="278d7-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="278d7-151">group 子句</span><span class="sxs-lookup"><span data-stu-id="278d7-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="278d7-152">匿名類型</span><span class="sxs-lookup"><span data-stu-id="278d7-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="278d7-153">在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="278d7-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="278d7-154">建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="278d7-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="278d7-155">分組資料</span><span class="sxs-lookup"><span data-stu-id="278d7-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
