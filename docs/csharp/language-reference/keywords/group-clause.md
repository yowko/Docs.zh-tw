---
title: group 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 2674986013afccf0a61267e49ca186d2ccb380e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217480"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="bc090-102">group 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bc090-102">group clause (C# Reference)</span></span>
<span data-ttu-id="bc090-103">`group` 子句會傳回一系列的 <xref:System.Linq.IGrouping%602> 物件，而這些物件包含符合群組之索引鍵值的零或多個項目。</span><span class="sxs-lookup"><span data-stu-id="bc090-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="bc090-104">例如，您可以根據每個字串中的第一個字母來分組一序列的字串。</span><span class="sxs-lookup"><span data-stu-id="bc090-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="bc090-105">在此情況下，第一個字母是索引鍵、具有類型 [char](../../../csharp/language-reference/keywords/char.md)，並儲存在每個 <xref:System.Linq.IGrouping%602> 物件的 `Key` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="bc090-105">In this case, the first letter is the key and has a type [char](../../../csharp/language-reference/keywords/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="bc090-106">編譯器會推斷索引鍵類型。</span><span class="sxs-lookup"><span data-stu-id="bc090-106">The compiler infers the type of the key.</span></span>  
  
 <span data-ttu-id="bc090-107">您可以使用 `group` 子句結束查詢運算式，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="bc090-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 <span data-ttu-id="bc090-108">如果您想要對每個群組執行其他查詢作業，則可以使用 [into](../../../csharp/language-reference/keywords/into.md) 內容關鍵字來指定暫時識別碼。</span><span class="sxs-lookup"><span data-stu-id="bc090-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](../../../csharp/language-reference/keywords/into.md) contextual keyword.</span></span> <span data-ttu-id="bc090-109">當您使用 `into` 時，必須繼續進行查詢，最後以 `select` 陳述式或另一個 `group` 子句結束，如下列摘錄所示︰</span><span class="sxs-lookup"><span data-stu-id="bc090-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 <span data-ttu-id="bc090-110">本主題的＜範例＞一節中提供使用或未使用 `into` 之 `group` 的更完整範例。</span><span class="sxs-lookup"><span data-stu-id="bc090-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this topic.</span></span>  
  
## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="bc090-111">列舉群組查詢結果</span><span class="sxs-lookup"><span data-stu-id="bc090-111">Enumerating the Results of a Group Query</span></span>  
 <span data-ttu-id="bc090-112">因為 `group` 查詢所產生的 <xref:System.Linq.IGrouping%602> 物件基本上是清單的清單，所以您必須使用巢狀 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 迴圈來存取每個群組中的項目。</span><span class="sxs-lookup"><span data-stu-id="bc090-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="bc090-113">外部迴圈會逐一查看群組索引鍵，內部迴圈則會逐一查看群組本身中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="bc090-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="bc090-114">群組可能具有索引鍵，但沒有項目。</span><span class="sxs-lookup"><span data-stu-id="bc090-114">A group may have a key but no elements.</span></span> <span data-ttu-id="bc090-115">下列 `foreach` 迴圈會執行先前程式碼範例中的查詢︰</span><span class="sxs-lookup"><span data-stu-id="bc090-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a><span data-ttu-id="bc090-116">索引鍵類型</span><span class="sxs-lookup"><span data-stu-id="bc090-116">Key Types</span></span>  
 <span data-ttu-id="bc090-117">群組索引鍵可以是任何類型，例如字串、內建數值類型，或使用者定義的具名類型或匿名型別。</span><span class="sxs-lookup"><span data-stu-id="bc090-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>  
  
### <a name="grouping-by-string"></a><span data-ttu-id="bc090-118">依字串群組</span><span class="sxs-lookup"><span data-stu-id="bc090-118">Grouping by string</span></span>  
 <span data-ttu-id="bc090-119">先前的程式碼範例已使用 `char`。</span><span class="sxs-lookup"><span data-stu-id="bc090-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="bc090-120">可以改為輕鬆地指定字串索引鍵，例如完整姓氏︰</span><span class="sxs-lookup"><span data-stu-id="bc090-120">A string key could easily have been specified instead, for example the complete last name:</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a><span data-ttu-id="bc090-121">依 bool 群組</span><span class="sxs-lookup"><span data-stu-id="bc090-121">Grouping by bool</span></span>  
 <span data-ttu-id="bc090-122">下列範例示範如何使用索引鍵的 bool 值，以將結果分成兩個群組。</span><span class="sxs-lookup"><span data-stu-id="bc090-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="bc090-123">請注意，值是由 `group` 子句中的子運算式所產生。</span><span class="sxs-lookup"><span data-stu-id="bc090-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a><span data-ttu-id="bc090-124">依數字範圍群組</span><span class="sxs-lookup"><span data-stu-id="bc090-124">Grouping by numeric range</span></span>  
 <span data-ttu-id="bc090-125">下一個範例使用運算式來建立代表百分位數範圍的數字群組索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bc090-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="bc090-126">請注意會使用 [let](../../../csharp/language-reference/keywords/let-clause.md) 作為儲存方法呼叫結果的方便位置，因此不需要在 `group` 子句中呼叫方法兩次。</span><span class="sxs-lookup"><span data-stu-id="bc090-126">Note the use of [let](../../../csharp/language-reference/keywords/let-clause.md) as a convenient location to store a method call result, so that you do not have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="bc090-127">也請注意在 `group` 子句中，為了避免「除以零」例外狀況，程式碼會檢查以確定學生沒有平均值零。</span><span class="sxs-lookup"><span data-stu-id="bc090-127">Note also in the `group` clause that to avoid a "divide by zero" exception the code checks to make sure that the student does not have an average of zero.</span></span> <span data-ttu-id="bc090-128">如需如何在查詢運算式中安全地使用方法的詳細資訊，請參閱[如何：處理查詢運算式中的例外狀況](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bc090-128">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a><span data-ttu-id="bc090-129">依複合索引鍵群組</span><span class="sxs-lookup"><span data-stu-id="bc090-129">Grouping by Composite Keys</span></span>  
 <span data-ttu-id="bc090-130">當您想要根據多個索引鍵來群組項目時，請使用複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bc090-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="bc090-131">您可以使用匿名型別或具名類型來保存索引鍵項目，以建立複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bc090-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="bc090-132">在下列範例中，假設已宣告 `Person` 類別具有名為 `surname` 和 `city` 的成員。</span><span class="sxs-lookup"><span data-stu-id="bc090-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="bc090-133">`group` 子句會為每一組具有相同姓氏和相同城市的人員，建立個別群組。</span><span class="sxs-lookup"><span data-stu-id="bc090-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 <span data-ttu-id="bc090-134">如果您必須將查詢變數傳遞給另一種方法，請使用具名類型。</span><span class="sxs-lookup"><span data-stu-id="bc090-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="bc090-135">請使用索引鍵的自動實作屬性建立特殊類別，然後覆寫 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bc090-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="bc090-136">您也可以使用結構，在此情況下，您絕對不需要覆寫這些方法。</span><span class="sxs-lookup"><span data-stu-id="bc090-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="bc090-137">如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)和[如何：查詢目錄樹狀結構中的重複檔案](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="bc090-137">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="bc090-138">第二個主題的程式碼範例示範如何使用含有具名類型的複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bc090-138">The latter topic has a code example that demonstrates how to use a composite key with a named type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc090-139">範例</span><span class="sxs-lookup"><span data-stu-id="bc090-139">Example</span></span>  
 <span data-ttu-id="bc090-140">下列範例示範未將任何其他查詢邏輯套用到群組時，將來源資料排序成群組的標準模式。</span><span class="sxs-lookup"><span data-stu-id="bc090-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="bc090-141">這稱為無接續群組。</span><span class="sxs-lookup"><span data-stu-id="bc090-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="bc090-142">字串陣列中的項目是根據其第一個字母進行分組。</span><span class="sxs-lookup"><span data-stu-id="bc090-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="bc090-143">查詢的結果是包含 `char` 類型之公用 `Key` 屬性的 <xref:System.Linq.IGrouping%602> 類型，以及包含群組中各個項目的 <xref:System.Collections.Generic.IEnumerable%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="bc090-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>  
  
 <span data-ttu-id="bc090-144">`group` 子句的結果是一連串的序列。</span><span class="sxs-lookup"><span data-stu-id="bc090-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="bc090-145">因此，若要存取每個所傳回群組內的個別項目，請在重複執行群組索引鍵的迴圈內使用巢狀 `foreach` 迴圈，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc090-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="bc090-146">範例</span><span class="sxs-lookup"><span data-stu-id="bc090-146">Example</span></span>  
 <span data-ttu-id="bc090-147">這個範例示範如何搭配使用「接續」與 `into`，以在建立其他邏輯之後，對群組執行這些邏輯。</span><span class="sxs-lookup"><span data-stu-id="bc090-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="bc090-148">如需詳細資訊，請參閱 [into](../../../csharp/language-reference/keywords/into.md)。</span><span class="sxs-lookup"><span data-stu-id="bc090-148">For more information, see [into](../../../csharp/language-reference/keywords/into.md).</span></span> <span data-ttu-id="bc090-149">下列範例會查詢每個群組，只選取其索引鍵值是母音的群組。</span><span class="sxs-lookup"><span data-stu-id="bc090-149">The following example queries each group to select only those whose key value is a vowel.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="bc090-150">備註</span><span class="sxs-lookup"><span data-stu-id="bc090-150">Remarks</span></span>  
 <span data-ttu-id="bc090-151">在編譯時期，`group` 子句會轉譯成 <xref:System.Linq.Enumerable.GroupBy%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bc090-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc090-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc090-152">See Also</span></span>  
 <xref:System.Linq.IGrouping%602>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.Enumerable.ThenBy%2A>  
 <xref:System.Linq.Enumerable.ThenByDescending%2A>  
 [<span data-ttu-id="bc090-153">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bc090-153">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="bc090-154">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="bc090-154">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="bc090-155">如何：建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="bc090-155">How to: Create a Nested Group</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [<span data-ttu-id="bc090-156">如何：將查詢結果分組</span><span class="sxs-lookup"><span data-stu-id="bc090-156">How to: Group Query Results</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [<span data-ttu-id="bc090-157">如何：在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="bc090-157">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
