---
title: join 子句 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 21d4d1f9878fb7df4692fdeacd23b042680c14f1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633614"
---
# <a name="join-clause-c-reference"></a><span data-ttu-id="814a3-102">join 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="814a3-102">join clause (C# Reference)</span></span>

<span data-ttu-id="814a3-103">`join` 子句可用於將不同來源序列中的項目產生關聯，這些項目在物件模型中沒有直接關聯性。</span><span class="sxs-lookup"><span data-stu-id="814a3-103">The `join` clause is useful for associating elements from different source sequences that have no direct relationship in the object model.</span></span> <span data-ttu-id="814a3-104">唯一的需求是每個來源中的項目必須共用可比較是否相等的特定值。</span><span class="sxs-lookup"><span data-stu-id="814a3-104">The only requirement is that the elements in each source share some value that can be compared for equality.</span></span> <span data-ttu-id="814a3-105">例如，食品經銷商可能有一份特定產品的供應商清單，以及一份買家清單。</span><span class="sxs-lookup"><span data-stu-id="814a3-105">For example, a food distributor might have a list of suppliers of a certain product, and a list of buyers.</span></span> <span data-ttu-id="814a3-106">針對位於相同指定地區的所有供應商和買家，可使用 `join` 子句來建立該產品的供應商和買家清單。</span><span class="sxs-lookup"><span data-stu-id="814a3-106">A `join` clause can be used, for example, to create a list of the suppliers and buyers of that product who are all in the same specified region.</span></span>

<span data-ttu-id="814a3-107">`join` 子句接受兩個來源序列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="814a3-107">A `join` clause takes two source sequences as input.</span></span> <span data-ttu-id="814a3-108">每個序列中的項目必須是可與另一個序列中的對應屬性進行比較的屬性，或包含這類屬性。</span><span class="sxs-lookup"><span data-stu-id="814a3-108">The elements in each sequence must either be or contain a property that can be compared to a corresponding property in the other sequence.</span></span> <span data-ttu-id="814a3-109">`join` 子句使用特殊的 `equals` 關鍵字，來比較指定的索引鍵是否相等。</span><span class="sxs-lookup"><span data-stu-id="814a3-109">The `join` clause compares the specified keys for equality by using the special `equals` keyword.</span></span> <span data-ttu-id="814a3-110">`join` 子句執行的所有聯結都是等聯結。</span><span class="sxs-lookup"><span data-stu-id="814a3-110">All joins performed by the `join` clause are equijoins.</span></span> <span data-ttu-id="814a3-111">`join` 子句輸出的組織結構取決於您要執行之聯結的特定類型。</span><span class="sxs-lookup"><span data-stu-id="814a3-111">The shape of the output of a `join` clause depends on the specific type of join you are performing.</span></span> <span data-ttu-id="814a3-112">以下是三種最常見的聯結類型：</span><span class="sxs-lookup"><span data-stu-id="814a3-112">The following are three most common join types:</span></span>

- <span data-ttu-id="814a3-113">內部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-113">Inner join</span></span>

- <span data-ttu-id="814a3-114">群組聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-114">Group join</span></span>

- <span data-ttu-id="814a3-115">左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-115">Left outer join</span></span>

## <a name="inner-join"></a><span data-ttu-id="814a3-116">內部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-116">Inner join</span></span>

<span data-ttu-id="814a3-117">下列範例顯示一個簡單的內部等聯結。</span><span class="sxs-lookup"><span data-stu-id="814a3-117">The following example shows a simple inner equijoin.</span></span> <span data-ttu-id="814a3-118">此查詢會產生「產品名稱/分類」配對的一般序列。</span><span class="sxs-lookup"><span data-stu-id="814a3-118">This query produces a flat sequence of "product name / category" pairs.</span></span> <span data-ttu-id="814a3-119">相同的分類字串會出現在多個項目中。</span><span class="sxs-lookup"><span data-stu-id="814a3-119">The same category string will appear in multiple elements.</span></span> <span data-ttu-id="814a3-120">如果 `categories` 中有某個項目具有不相符的 `products`，則該分類不會出現在結果中。</span><span class="sxs-lookup"><span data-stu-id="814a3-120">If an element from `categories` has no matching `products`, that category will not appear in the results.</span></span>

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

<span data-ttu-id="814a3-121">如需詳細資訊，請參閱[執行內部聯結](../../linq/perform-inner-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-121">For more information, see [Perform inner joins](../../linq/perform-inner-joins.md).</span></span>

## <a name="group-join"></a><span data-ttu-id="814a3-122">群組聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-122">Group join</span></span>

<span data-ttu-id="814a3-123">具有 `into` 運算式的 `join` 子句稱為群組聯結。</span><span class="sxs-lookup"><span data-stu-id="814a3-123">A `join` clause with an `into` expression is called a group join.</span></span>

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

<span data-ttu-id="814a3-124">群組聯結會產生階層式結果序列，將左側來源序列中的項目與右側來源序列中的一或多個相符項目產生關聯。</span><span class="sxs-lookup"><span data-stu-id="814a3-124">A group join produces a hierarchical result sequence, which associates elements in the left source sequence with one or more matching elements in the right side source sequence.</span></span> <span data-ttu-id="814a3-125">群組聯結從關聯式觀點來看沒有對等項目，它基本上是物件陣列的序列。</span><span class="sxs-lookup"><span data-stu-id="814a3-125">A group join has no equivalent in relational terms; it is essentially a sequence of object arrays.</span></span>

<span data-ttu-id="814a3-126">如果右側來源序列中找不到項目會符合左側來源的項目，`join` 子句會針對該項目產生空陣列。</span><span class="sxs-lookup"><span data-stu-id="814a3-126">If no elements from the right source sequence are found to match an element in the left source, the `join` clause will produce an empty array for that item.</span></span> <span data-ttu-id="814a3-127">因此，群組聯結基本上仍然是內部等聯結，不同之處在於結果序列會組織成群組。</span><span class="sxs-lookup"><span data-stu-id="814a3-127">Therefore, the group join is still basically an inner-equijoin except that the result sequence is organized into groups.</span></span>

<span data-ttu-id="814a3-128">如果您只選取群組聯結的結果，便可以存取項目，但無法識別比對的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="814a3-128">If you just select the results of a group join, you can access the items, but you cannot identify the key that they match on.</span></span> <span data-ttu-id="814a3-129">因此，選取群組聯結成同時具有索引鍵名稱之新類型的結果，通常會比較有用 (如上述範例所示)。</span><span class="sxs-lookup"><span data-stu-id="814a3-129">Therefore, it is generally more useful to select the results of the group join into a new type that also has the key name, as shown in the previous example.</span></span>

<span data-ttu-id="814a3-130">您當然也可以使用群組聯結的結果，作為另一個子查詢的產生器：</span><span class="sxs-lookup"><span data-stu-id="814a3-130">You can also, of course, use the result of a group join as the generator of another subquery:</span></span>

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

<span data-ttu-id="814a3-131">如需詳細資訊，請參閱[執行群組聯結](../../linq/perform-grouped-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-131">For more information, see [Perform grouped joins](../../linq/perform-grouped-joins.md).</span></span>

## <a name="left-outer-join"></a><span data-ttu-id="814a3-132">左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-132">Left outer join</span></span>

<span data-ttu-id="814a3-133">在左方外部聯結中，會傳回左側來源序列中的所有項目，即使在右側序列中沒有相符項目亦然。</span><span class="sxs-lookup"><span data-stu-id="814a3-133">In a left outer join, all the elements in the left source sequence are returned, even if no matching elements are in the right sequence.</span></span> <span data-ttu-id="814a3-134">若要在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 中執行左方外部聯結，請搭配群組聯結使用 `DefaultIfEmpty` 方法，以指定在左側項目沒有相符項目時所要產生的預設右側項目。</span><span class="sxs-lookup"><span data-stu-id="814a3-134">To perform a left outer join in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], use the `DefaultIfEmpty` method in combination with a group join to specify a default right-side element to produce if a left-side element has no matches.</span></span> <span data-ttu-id="814a3-135">您可以使用 `null` 作為任何參考型別的預設值，也可以指定使用者定義的預設類型。</span><span class="sxs-lookup"><span data-stu-id="814a3-135">You can use `null` as the default value for any reference type, or you can specify a user-defined default type.</span></span> <span data-ttu-id="814a3-136">在下列範例中，會顯示使用者定義的預設類型：</span><span class="sxs-lookup"><span data-stu-id="814a3-136">In the following example, a user-defined default type is shown:</span></span>

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

<span data-ttu-id="814a3-137">如需詳細資訊，請參閱[執行左方外部聯結](../../linq/perform-left-outer-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-137">For more information, see [Perform left outer joins](../../linq/perform-left-outer-joins.md).</span></span>

## <a name="the-equals-operator"></a><span data-ttu-id="814a3-138">等號運算子</span><span class="sxs-lookup"><span data-stu-id="814a3-138">The equals operator</span></span>

<span data-ttu-id="814a3-139">`join` 子句會執行等聯結。</span><span class="sxs-lookup"><span data-stu-id="814a3-139">A `join` clause performs an equijoin.</span></span> <span data-ttu-id="814a3-140">換句話說，您只能根據兩個索引鍵是否相等進行比對。</span><span class="sxs-lookup"><span data-stu-id="814a3-140">In other words, you can only base matches on the equality of two keys.</span></span> <span data-ttu-id="814a3-141">不支援其他比較類型，例如「大於」或「不等於」。</span><span class="sxs-lookup"><span data-stu-id="814a3-141">Other types of comparisons such as "greater than" or "not equals" are not supported.</span></span> <span data-ttu-id="814a3-142">為了釐清所有聯結都是等聯結，`join` 子句使用 `equals` 關鍵字而非 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="814a3-142">To make clear that all joins are equijoins, the `join` clause uses the `equals` keyword instead of the `==` operator.</span></span> <span data-ttu-id="814a3-143">`equals` 關鍵字只能用於 `join` 子句，而且與 `==` 運算子有一個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="814a3-143">The `equals` keyword can only be used in a `join` clause and it differs from the `==` operator in one important way.</span></span> <span data-ttu-id="814a3-144">使用 `equals` 時，左側索引鍵會取用外部來源序列，而右側索引鍵會取用內部來源。</span><span class="sxs-lookup"><span data-stu-id="814a3-144">With `equals`, the left key consumes the outer source sequence, and the right key consumes the inner source.</span></span> <span data-ttu-id="814a3-145">外部來源只會在 `equals` 的左側範圍內，而內部來源序列只會在右側範圍內。</span><span class="sxs-lookup"><span data-stu-id="814a3-145">The outer source is only in scope on the left side of `equals` and the inner source sequence is only in scope on the right side.</span></span>

## <a name="non-equijoins"></a><span data-ttu-id="814a3-146">非等聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-146">Non-equijoins</span></span>

<span data-ttu-id="814a3-147">您可以使用多個 `from` 子句單獨將新的序列引入查詢，以執行非等聯結、交叉聯結及其他自訂聯結作業。</span><span class="sxs-lookup"><span data-stu-id="814a3-147">You can perform non-equijoins, cross joins, and other custom join operations by using multiple `from` clauses to introduce new sequences independently into a query.</span></span> <span data-ttu-id="814a3-148">如需詳細資訊，請參閱[執行自訂聯結作業](../../linq/perform-custom-join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-148">For more information, see [Perform custom join operations](../../linq/perform-custom-join-operations.md).</span></span>

## <a name="joins-on-object-collections-vs-relational-tables"></a><span data-ttu-id="814a3-149">物件集合上的聯結與關聯式資料表的比較</span><span class="sxs-lookup"><span data-stu-id="814a3-149">Joins on object collections vs. relational tables</span></span>

<span data-ttu-id="814a3-150">在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中，聯結作業是在物件集合上執行。</span><span class="sxs-lookup"><span data-stu-id="814a3-150">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression, join operations are performed on object collections.</span></span> <span data-ttu-id="814a3-151">物件集合無法以與兩個關聯式資料表完全相同的方式進行「聯結」。</span><span class="sxs-lookup"><span data-stu-id="814a3-151">Object collections cannot be "joined" in exactly the same way as two relational tables.</span></span> <span data-ttu-id="814a3-152">在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 中，只有在兩個來源序列未透過任何關聯性繫結時，才需要明確的 `join` 子句。</span><span class="sxs-lookup"><span data-stu-id="814a3-152">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], explicit `join` clauses are only required when two source sequences are not tied by any relationship.</span></span> <span data-ttu-id="814a3-153">使用 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 時，外部索引鍵資料表在物件模型中會表示為主要資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="814a3-153">When working with [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], foreign key tables are represented in the object model as properties of the primary table.</span></span> <span data-ttu-id="814a3-154">例如，在 Northwind 資料庫中，Customer 資料表與 Orders 資料表有外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="814a3-154">For example, in the Northwind database, the Customer table has a foreign key relationship with the Orders table.</span></span> <span data-ttu-id="814a3-155">當您將資料表對應至物件模型時，Customer 類別會有 Orders 屬性，其中包含與 Customer 相關聯之 Orders 的集合。</span><span class="sxs-lookup"><span data-stu-id="814a3-155">When you map the tables to the object model, the Customer class has an Orders property that contains the collection of Orders associated with that Customer.</span></span> <span data-ttu-id="814a3-156">實際上已為您完成此聯結。</span><span class="sxs-lookup"><span data-stu-id="814a3-156">In effect, the join has already been done for you.</span></span>

<span data-ttu-id="814a3-157">如需在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 內容中查詢所有關聯資料表的詳細資訊，請參閱[如何︰對應資料庫關聯性](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-157">For more information about querying across related tables in the context of [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], see [How to: Map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).</span></span>

## <a name="composite-keys"></a><span data-ttu-id="814a3-158">複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="814a3-158">Composite keys</span></span>

<span data-ttu-id="814a3-159">您可以使用複合索引鍵來測試多個值是否相等。</span><span class="sxs-lookup"><span data-stu-id="814a3-159">You can test for equality of multiple values by using a composite key.</span></span> <span data-ttu-id="814a3-160">如需詳細資訊，請參閱[使用複合索引鍵執行聯結](../../linq/join-by-using-composite-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="814a3-160">For more information, see [Join by using composite keys](../../linq/join-by-using-composite-keys.md).</span></span> <span data-ttu-id="814a3-161">複合索引鍵也可用於 `group` 子句。</span><span class="sxs-lookup"><span data-stu-id="814a3-161">Composite keys can be also used in a `group` clause.</span></span>

## <a name="example"></a><span data-ttu-id="814a3-162">範例</span><span class="sxs-lookup"><span data-stu-id="814a3-162">Example</span></span>

<span data-ttu-id="814a3-163">下列範例使用相同的比對索引鍵，來比較相同資料來源中內部聯結、群組聯結和左方外部聯結的結果。</span><span class="sxs-lookup"><span data-stu-id="814a3-163">The following example compares the results of an inner join, a group join, and a left outer join on the same data sources by using the same matching keys.</span></span> <span data-ttu-id="814a3-164">這些範例中新增了一些額外的程式碼，以釐清主控台顯示中的結果。</span><span class="sxs-lookup"><span data-stu-id="814a3-164">Some extra code is added to these examples to clarify the results in the console display.</span></span>

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a><span data-ttu-id="814a3-165">備註</span><span class="sxs-lookup"><span data-stu-id="814a3-165">Remarks</span></span>

<span data-ttu-id="814a3-166">如果 `join` 子句沒有後接 `into`，則會將該子句轉譯為 <xref:System.Linq.Enumerable.Join%2A> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="814a3-166">A `join` clause that is not followed by `into` is translated into a <xref:System.Linq.Enumerable.Join%2A> method call.</span></span> <span data-ttu-id="814a3-167">如果 `join` 子句後接 `into`，則會將該子句轉譯為 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="814a3-167">A `join` clause that is followed by `into` is translated to a <xref:System.Linq.Enumerable.GroupJoin%2A> method call.</span></span>

## <a name="see-also"></a><span data-ttu-id="814a3-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="814a3-168">See also</span></span>

- [<span data-ttu-id="814a3-169">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="814a3-169">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="814a3-170">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="814a3-170">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="814a3-171">聯結作業</span><span class="sxs-lookup"><span data-stu-id="814a3-171">Join Operations</span></span>](../../programming-guide/concepts/linq/join-operations.md)
- [<span data-ttu-id="814a3-172">group 子句</span><span class="sxs-lookup"><span data-stu-id="814a3-172">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="814a3-173">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-173">Perform left outer joins</span></span>](../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="814a3-174">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-174">Perform inner joins</span></span>](../../linq/perform-inner-joins.md)
- [<span data-ttu-id="814a3-175">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-175">Perform grouped joins</span></span>](../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="814a3-176">排序 Join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="814a3-176">Order the results of a join clause</span></span>](../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="814a3-177">使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="814a3-177">Join by using composite keys</span></span>](../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="814a3-178">適用於 Visual Studio 相容的資料庫系統</span><span class="sxs-lookup"><span data-stu-id="814a3-178">Compatible database systems for Visual Studio</span></span>](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
