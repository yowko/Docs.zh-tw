---
title: 標準查詢運算子轉譯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 1bba36579fce4fe78289ccb986073280b531420a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661880"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="2d42c-102">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="2d42c-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-103">會將標準查詢運算子轉譯為 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="2d42c-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="2d42c-104">資料庫的查詢處理器會決定執行語意的 SQL 轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d42c-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="2d42c-105">標準查詢運算子中定義*序列*。</span><span class="sxs-lookup"><span data-stu-id="2d42c-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="2d42c-106">是一連串*排序*而且依賴序列的每個元素的參考識別。</span><span class="sxs-lookup"><span data-stu-id="2d42c-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="2d42c-107">如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀 (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或是[標準查詢運算子概觀 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</c0></span><span class="sxs-lookup"><span data-stu-id="2d42c-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="2d42c-108">SQL 主要負責處理*未排序的一組值*。</span><span class="sxs-lookup"><span data-stu-id="2d42c-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="2d42c-109">排序通常是一項明確陳述的後置處理作業，會套用至最終查詢結果 (而非中繼結果)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="2d42c-110">識別是以值來定義。</span><span class="sxs-lookup"><span data-stu-id="2d42c-110">Identity is defined by values.</span></span> <span data-ttu-id="2d42c-111">基於這個理由，SQL 查詢來了解處理用於多重集 (*包*) 而非*設定*。</span><span class="sxs-lookup"><span data-stu-id="2d42c-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="2d42c-112">下列段落說明標準查詢運算子和其因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 針對 SQL Server 提供者進行的 SQL 轉譯之間的差異。</span><span class="sxs-lookup"><span data-stu-id="2d42c-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="2d42c-113">運算子支援</span><span class="sxs-lookup"><span data-stu-id="2d42c-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="2d42c-114">Concat</span><span class="sxs-lookup"><span data-stu-id="2d42c-114">Concat</span></span>

<span data-ttu-id="2d42c-115"><xref:System.Linq.Enumerable.Concat%2A>方法在定義上適用於已排序的多重集，也就是說接收器的順序和引數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="2d42c-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="2d42c-116"><xref:System.Linq.Enumerable.Concat%2A> 的運作原理，是對採用共通順序的多重集執行 `UNION ALL`。</span><span class="sxs-lookup"><span data-stu-id="2d42c-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="2d42c-117">最後一步就是在產生結果前於 SQL 中排序。</span><span class="sxs-lookup"><span data-stu-id="2d42c-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="2d42c-118"><xref:System.Linq.Enumerable.Concat%2A> 不會保留其引數的順序。</span><span class="sxs-lookup"><span data-stu-id="2d42c-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="2d42c-119">若要確保適當的排序，您必須明確排序 <xref:System.Linq.Enumerable.Concat%2A> 的結果。</span><span class="sxs-lookup"><span data-stu-id="2d42c-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="2d42c-120">Intersect、Except、Union</span><span class="sxs-lookup"><span data-stu-id="2d42c-120">Intersect, Except, Union</span></span>

<span data-ttu-id="2d42c-121"><xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Except%2A> 方法在定義上僅適用於集合。</span><span class="sxs-lookup"><span data-stu-id="2d42c-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="2d42c-122">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="2d42c-123"><xref:System.Linq.Enumerable.Union%2A> 方法在定義上適用於多重集，可對多重集做未排序的串連 (其實就是 SQL 中 UNION ALL 子句的結果)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="2d42c-124">Take、Skip</span><span class="sxs-lookup"><span data-stu-id="2d42c-124">Take, Skip</span></span>

<span data-ttu-id="2d42c-125"><xref:System.Linq.Enumerable.Take%2A> 並<xref:System.Linq.Enumerable.Skip%2A>方法在定義只針對適用於*ordered set*。</span><span class="sxs-lookup"><span data-stu-id="2d42c-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="2d42c-126">未定義適用於未排序集合或多重集的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="2d42c-127"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 SQL Server 2000 進行的查詢中時會有一些限制。</span><span class="sxs-lookup"><span data-stu-id="2d42c-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="2d42c-128">如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

<span data-ttu-id="2d42c-129">由於在 SQL 中，排序的限制[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]嘗試將移至方法的結果，這些方法的引數的順序。</span><span class="sxs-lookup"><span data-stu-id="2d42c-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="2d42c-130">例如，請考量下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢：</span><span class="sxs-lookup"><span data-stu-id="2d42c-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="2d42c-131">這個程序碼產生的 SQL 會將排序移至結尾，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2d42c-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="2d42c-132">很明顯地，當 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 鏈結在一起時，所有指定的排序都必須一致。</span><span class="sxs-lookup"><span data-stu-id="2d42c-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="2d42c-133">否則，會有未定義的結果。</span><span class="sxs-lookup"><span data-stu-id="2d42c-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="2d42c-134">根據標準查詢運算子的規格，<xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在定義上適用於非負數的固定整數引數。</span><span class="sxs-lookup"><span data-stu-id="2d42c-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="2d42c-135">不轉譯的運算子</span><span class="sxs-lookup"><span data-stu-id="2d42c-135">Operators with No Translation</span></span>

<span data-ttu-id="2d42c-136">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會轉譯下列方法。</span><span class="sxs-lookup"><span data-stu-id="2d42c-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2d42c-137">最常見的原因在於未排序的多重集與序列之間有差異。</span><span class="sxs-lookup"><span data-stu-id="2d42c-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="2d42c-138">運算子</span><span class="sxs-lookup"><span data-stu-id="2d42c-138">Operators</span></span>|<span data-ttu-id="2d42c-139">基本原理</span><span class="sxs-lookup"><span data-stu-id="2d42c-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="2d42c-140"><xref:System.Linq.Enumerable.TakeWhile%2A>、 <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="2d42c-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="2d42c-141">SQL 查詢可用於多重集而非序列上。</span><span class="sxs-lookup"><span data-stu-id="2d42c-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="2d42c-142">`ORDER BY` 必須是最後一個對結果套用的子句。</span><span class="sxs-lookup"><span data-stu-id="2d42c-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="2d42c-143">因此，這兩個方法不需要普遍受到轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d42c-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="2d42c-144">如果是未排序的集合，則要轉譯這個方法是可行的，但 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 目前不會加以轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d42c-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="2d42c-145"><xref:System.Linq.Enumerable.Last%2A>、 <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="2d42c-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="2d42c-146">如果是未排序的集合，則要轉譯這些方法是可行的，但 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 目前不會加以轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d42c-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="2d42c-147"><xref:System.Linq.Enumerable.ElementAt%2A>、 <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="2d42c-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="2d42c-148">SQL 查詢是用於多重集，而非可建立索引的序列上。</span><span class="sxs-lookup"><span data-stu-id="2d42c-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="2d42c-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (以預設引數多載)</span><span class="sxs-lookup"><span data-stu-id="2d42c-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="2d42c-150">一般而言，如果是任意 Tuple，就不能指定預設值。</span><span class="sxs-lookup"><span data-stu-id="2d42c-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="2d42c-151">在某些情況下，可以透過外部聯結 (Outer Join) 指定 Null 值給 Tuple。</span><span class="sxs-lookup"><span data-stu-id="2d42c-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="2d42c-152">運算式轉譯</span><span class="sxs-lookup"><span data-stu-id="2d42c-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="2d42c-153">Null 語意</span><span class="sxs-lookup"><span data-stu-id="2d42c-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-154">不會對 SQL 加上 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="2d42c-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="2d42c-155">比較運算子會轉譯為語法上的 SQL 對等用法。</span><span class="sxs-lookup"><span data-stu-id="2d42c-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="2d42c-156">基於這個理由，語意會反映伺服器或連接設定所定義的 SQL 語意。</span><span class="sxs-lookup"><span data-stu-id="2d42c-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="2d42c-157">例如，兩個 null 值會視為不相等，在預設 SQL Server 設定 下，但您可以變更設定來變更語意。</span><span class="sxs-lookup"><span data-stu-id="2d42c-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-158">在轉譯查詢時不會考慮伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="2d42c-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="2d42c-159">與常值 null 的比較會轉譯為適當的 SQL 版本 (`is null` 或 `is not null`)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="2d42c-160">定序 (Collation) 中的值 `null` 是由 SQL Server 所定義。</span><span class="sxs-lookup"><span data-stu-id="2d42c-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-161">不會變更這個定序。</span><span class="sxs-lookup"><span data-stu-id="2d42c-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="2d42c-162">彙總</span><span class="sxs-lookup"><span data-stu-id="2d42c-162">Aggregates</span></span>

<span data-ttu-id="2d42c-163">標準查詢運算子彙總方法 <xref:System.Linq.Enumerable.Sum%2A> 會將空序列或只包含 null 的序列評估為零。</span><span class="sxs-lookup"><span data-stu-id="2d42c-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="2d42c-164">中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，SQL 的語意會保留不變，並<xref:System.Linq.Enumerable.Sum%2A>評估為`null`而不是零，將空序列或只包含 null 的序列。</span><span class="sxs-lookup"><span data-stu-id="2d42c-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="2d42c-165">SQL 對中繼結果的限制會套用至 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總。</span><span class="sxs-lookup"><span data-stu-id="2d42c-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2d42c-166">32 位元整數量值的 <xref:System.Linq.Enumerable.Sum%2A> 不會用 64 位元的結果來計算。</span><span class="sxs-lookup"><span data-stu-id="2d42c-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="2d42c-167">即使標準查詢運算子實作並未造成對應的記憶體中序列發生溢位，進行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 <xref:System.Linq.Enumerable.Sum%2A> 轉譯仍可能會發生溢位。</span><span class="sxs-lookup"><span data-stu-id="2d42c-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="2d42c-168">同樣地，轉譯整數值的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 <xref:System.Linq.Enumerable.Average%2A> 時，會以 `integer` 而非 `double` 計算。</span><span class="sxs-lookup"><span data-stu-id="2d42c-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="2d42c-169">實體引數</span><span class="sxs-lookup"><span data-stu-id="2d42c-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-170">可讓實體類型，以供<xref:System.Linq.Enumerable.GroupBy%2A>和<xref:System.Linq.Enumerable.OrderBy%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2d42c-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="2d42c-171">在轉譯這些運算子時，使用型別引數會視為指定該型別的所有成員。</span><span class="sxs-lookup"><span data-stu-id="2d42c-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="2d42c-172">例如，下列程式碼為對等用法：</span><span class="sxs-lookup"><span data-stu-id="2d42c-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="2d42c-173">可相等 / 可比較的引數</span><span class="sxs-lookup"><span data-stu-id="2d42c-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="2d42c-174">實作下列方法時，必須進行引數的等號比較：</span><span class="sxs-lookup"><span data-stu-id="2d42c-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-175">支援和不等比較*一般*引數，而不是或包含序列的引數。</span><span class="sxs-lookup"><span data-stu-id="2d42c-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="2d42c-176">扁平引數是一種可以對應至 SQL 資料列的型別。</span><span class="sxs-lookup"><span data-stu-id="2d42c-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="2d42c-177">如果一個或多個實體型別的投影可以透過靜態方式判斷為不含序列，則這個投影即為扁平引數。</span><span class="sxs-lookup"><span data-stu-id="2d42c-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="2d42c-178">下列是扁平引數的範例：</span><span class="sxs-lookup"><span data-stu-id="2d42c-178">Following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="2d42c-179">下列是非扁平 (階層式) 引數的範例：</span><span class="sxs-lookup"><span data-stu-id="2d42c-179">The following are examples of non-flat (hierarchical) arguments.</span></span>

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="2d42c-180">Visual Basic 函式轉譯</span><span class="sxs-lookup"><span data-stu-id="2d42c-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="2d42c-181">Visual Basic 編譯器 (Compiler) 所用的下列 Helper 函式會轉譯為對應的 SQL 運算子和函式：</span><span class="sxs-lookup"><span data-stu-id="2d42c-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="2d42c-182">轉換方法：</span><span class="sxs-lookup"><span data-stu-id="2d42c-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="2d42c-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="2d42c-183">ToBoolean</span></span>|<span data-ttu-id="2d42c-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="2d42c-184">ToSByte</span></span>|<span data-ttu-id="2d42c-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="2d42c-185">ToByte</span></span>|<span data-ttu-id="2d42c-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="2d42c-186">ToChar</span></span>|
|<span data-ttu-id="2d42c-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="2d42c-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="2d42c-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="2d42c-188">ToDate</span></span>|<span data-ttu-id="2d42c-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="2d42c-189">ToDecimal</span></span>|<span data-ttu-id="2d42c-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="2d42c-190">ToDouble</span></span>|
|<span data-ttu-id="2d42c-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="2d42c-191">ToInteger</span></span>|<span data-ttu-id="2d42c-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="2d42c-192">ToUInteger</span></span>|<span data-ttu-id="2d42c-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="2d42c-193">ToLong</span></span>|<span data-ttu-id="2d42c-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="2d42c-194">ToULong</span></span>|
|<span data-ttu-id="2d42c-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="2d42c-195">ToShort</span></span>|<span data-ttu-id="2d42c-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="2d42c-196">ToUShort</span></span>|<span data-ttu-id="2d42c-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="2d42c-197">ToSingle</span></span>|<span data-ttu-id="2d42c-198">ToString</span><span class="sxs-lookup"><span data-stu-id="2d42c-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="2d42c-199">繼承支援</span><span class="sxs-lookup"><span data-stu-id="2d42c-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="2d42c-200">繼承對應限制</span><span class="sxs-lookup"><span data-stu-id="2d42c-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="2d42c-201">如需詳細資訊，請參閱[如何：對應繼承階層架構](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-201">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="2d42c-202">查詢中的繼承</span><span class="sxs-lookup"><span data-stu-id="2d42c-202">Inheritance in Queries</span></span>

<span data-ttu-id="2d42c-203">僅支援在投影中使用 C# 轉換 (Cast)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="2d42c-204">其他地方使用的轉換 (Cast) 不會受到轉譯而且會予以忽略。</span><span class="sxs-lookup"><span data-stu-id="2d42c-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="2d42c-205">事實上，除了 SQL 函式名稱之外，SQL 只會執行 Common Language Runtime (CLR) <xref:System.Convert> 的對等用法。</span><span class="sxs-lookup"><span data-stu-id="2d42c-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="2d42c-206">也就是說，SQL 可以將某個型別的值變更為另一個值。</span><span class="sxs-lookup"><span data-stu-id="2d42c-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="2d42c-207">因為沒有將相同位元的型別重新解譯為另一個型別的概念，CLR 轉換 (Cast) 沒有對等用法。</span><span class="sxs-lookup"><span data-stu-id="2d42c-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="2d42c-208">這就是 C# 轉換只能在區域執行的原因。</span><span class="sxs-lookup"><span data-stu-id="2d42c-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="2d42c-209">無法遠端處理。</span><span class="sxs-lookup"><span data-stu-id="2d42c-209">It is not remoted.</span></span>

<span data-ttu-id="2d42c-210">運算子 (`is` 和 `as`) 與 `GetType` 方法不僅能用於 `Select` 運算子中，</span><span class="sxs-lookup"><span data-stu-id="2d42c-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="2d42c-211">也可用於其他查詢運算子中。</span><span class="sxs-lookup"><span data-stu-id="2d42c-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="2d42c-212">SQL Server 2008 支援</span><span class="sxs-lookup"><span data-stu-id="2d42c-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="2d42c-213">從 .NET Framework 3.5 SP1 開始，LINQ to SQL 便支援對應至 SQL Server 2008 所導入的新日期和時間型別。</span><span class="sxs-lookup"><span data-stu-id="2d42c-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="2d42c-214">但是，針對對應至這些新型別的值進行作業時，您可以使用的 LINQ to SQL 查詢運算子有一些限制。</span><span class="sxs-lookup"><span data-stu-id="2d42c-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="2d42c-215">不支援的查詢運算子</span><span class="sxs-lookup"><span data-stu-id="2d42c-215">Unsupported Query Operators</span></span>

<span data-ttu-id="2d42c-216">對應至新 SQL Server 日期和時間型別的值不支援下列查詢運算子：`DATETIME2`、`DATE`、`TIME` 和 `DATETIMEOFFSET`。</span><span class="sxs-lookup"><span data-stu-id="2d42c-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="2d42c-217">如需對應至這些 SQL Server 日期和時間類型的詳細資訊，請參閱[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="2d42c-218">SQL Server 2005 支援</span><span class="sxs-lookup"><span data-stu-id="2d42c-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-219">不支援下列 SQL Server 2005 功能：</span><span class="sxs-lookup"><span data-stu-id="2d42c-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="2d42c-220">針對 SQL CLR 撰寫的預存程序 (Stored Procedure)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="2d42c-221">使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="2d42c-221">User-defined type.</span></span>

- <span data-ttu-id="2d42c-222">XML 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="2d42c-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="2d42c-223">SQL Server 2000 支援</span><span class="sxs-lookup"><span data-stu-id="2d42c-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="2d42c-224">下列的 SQL Server 2000 限制 （相較於 Microsoft SQL Server 2005） 會影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援。</span><span class="sxs-lookup"><span data-stu-id="2d42c-224">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="2d42c-225">Cross Apply 和 Outer Apply 運算子</span><span class="sxs-lookup"><span data-stu-id="2d42c-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="2d42c-226">這些運算子不適用於 SQL Server 2000。</span><span class="sxs-lookup"><span data-stu-id="2d42c-226">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2d42c-227">會嘗試進行一連串重寫作業，以便將它們取代成適當的聯結 (Join)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="2d42c-228">`Cross Apply` 和 `Outer Apply` 是為了關聯性 (Relationship) 巡覽而產生的。</span><span class="sxs-lookup"><span data-stu-id="2d42c-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="2d42c-229">會進行這類重寫的查詢集還沒整理出來。</span><span class="sxs-lookup"><span data-stu-id="2d42c-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="2d42c-230">基於這個理由，最小的查詢集支援 SQL Server 2000 會是未牽涉到關聯性導覽的集合。</span><span class="sxs-lookup"><span data-stu-id="2d42c-230">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="2d42c-231">text / ntext</span><span class="sxs-lookup"><span data-stu-id="2d42c-231">text / ntext</span></span>

<span data-ttu-id="2d42c-232">資料型別`text`  /  `ntext`不適用於某些查詢作業`varchar(max)`  /  `nvarchar(max)`，所支援的 Microsoft SQL Server 2005。</span><span class="sxs-lookup"><span data-stu-id="2d42c-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="2d42c-233">這項限制沒有解決方案。</span><span class="sxs-lookup"><span data-stu-id="2d42c-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="2d42c-234">具體來說，如果結果中含有對應至 `Distinct()` 或 `text` 資料行的成員，就不能對該結果使用 `ntext`。</span><span class="sxs-lookup"><span data-stu-id="2d42c-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="2d42c-235">巢狀查詢觸發的行為</span><span class="sxs-lookup"><span data-stu-id="2d42c-235">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="2d42c-236">SQL Server 2000 （透過 SP4) 繫結器具有一些由巢狀查詢觸發的特性。</span><span class="sxs-lookup"><span data-stu-id="2d42c-236">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="2d42c-237">無法妥善定義的 SQL 查詢集，就會觸發這些特性。</span><span class="sxs-lookup"><span data-stu-id="2d42c-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="2d42c-238">基於這個理由，您不能定義一組[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢可能會導致 SQL Server 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2d42c-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="2d42c-239">Skip 和 Take 運算子</span><span class="sxs-lookup"><span data-stu-id="2d42c-239">Skip and Take Operators</span></span>

<span data-ttu-id="2d42c-240"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 SQL Server 2000 進行的查詢中時會有一些限制。</span><span class="sxs-lookup"><span data-stu-id="2d42c-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="2d42c-241">如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="2d42c-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="2d42c-242">物件具體化</span><span class="sxs-lookup"><span data-stu-id="2d42c-242">Object Materialization</span></span>

<span data-ttu-id="2d42c-243">Materialization 作業會針對一個或多個 SQL 查詢傳回的資料列建立 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="2d42c-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="2d42c-244">下列呼叫會*本機執行*具體化的一部分：</span><span class="sxs-lookup"><span data-stu-id="2d42c-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="2d42c-245">建構函式</span><span class="sxs-lookup"><span data-stu-id="2d42c-245">Constructors</span></span>

  - <span data-ttu-id="2d42c-246">投影中的 `ToString` 方法</span><span class="sxs-lookup"><span data-stu-id="2d42c-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="2d42c-247">投影中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="2d42c-247">Type casts in projections</span></span>

- <span data-ttu-id="2d42c-248">請遵循的方法<xref:System.Linq.Enumerable.AsEnumerable%2A>方法會*在本機執行*。</span><span class="sxs-lookup"><span data-stu-id="2d42c-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="2d42c-249">這個方法不會造成立即執行。</span><span class="sxs-lookup"><span data-stu-id="2d42c-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="2d42c-250">您可以使用 `struct` 做為查詢結果的傳回型別或是結果型別的成員。</span><span class="sxs-lookup"><span data-stu-id="2d42c-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="2d42c-251">實體必須為類別。</span><span class="sxs-lookup"><span data-stu-id="2d42c-251">Entities are required to be classes.</span></span> <span data-ttu-id="2d42c-252">匿名型別會具體化成為類別執行個體，但具名 struct (非實體) 則可以用於投影中。</span><span class="sxs-lookup"><span data-stu-id="2d42c-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="2d42c-253">查詢結果所傳回型別的成員可以屬於型別 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="2d42c-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2d42c-254">它會具體化成為本機集合。</span><span class="sxs-lookup"><span data-stu-id="2d42c-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="2d42c-255">下列方法會造成*立即 materialization*方法會套用至序列的：</span><span class="sxs-lookup"><span data-stu-id="2d42c-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="2d42c-256">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d42c-256">See also</span></span>

- [<span data-ttu-id="2d42c-257">參考資料</span><span class="sxs-lookup"><span data-stu-id="2d42c-257">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="2d42c-258">傳回或略過序列中的項目</span><span class="sxs-lookup"><span data-stu-id="2d42c-258">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="2d42c-259">串連兩個序列</span><span class="sxs-lookup"><span data-stu-id="2d42c-259">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)
- [<span data-ttu-id="2d42c-260">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="2d42c-260">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="2d42c-261">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="2d42c-261">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="2d42c-262">傳回兩個序列的集合聯集</span><span class="sxs-lookup"><span data-stu-id="2d42c-262">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
