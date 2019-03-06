---
title: 從命令樹產生 SQL - 最佳作法
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 6ac46b577f071bca6c79e23b8b77f9b267ac879b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369665"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="5eb14-102">從命令樹產生 SQL - 最佳作法</span><span class="sxs-lookup"><span data-stu-id="5eb14-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="5eb14-103">輸出查詢命令樹會仔細地建立可用 SQL 表示之查詢的模型。</span><span class="sxs-lookup"><span data-stu-id="5eb14-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="5eb14-104">不過，從輸出命令樹產生 SQL 時，提供者寫入器會面臨某些常見的挑戰。</span><span class="sxs-lookup"><span data-stu-id="5eb14-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="5eb14-105">本主題將討論這些挑戰。</span><span class="sxs-lookup"><span data-stu-id="5eb14-105">This topic discusses these challenges.</span></span> <span data-ttu-id="5eb14-106">在下一個主題中，範例提供者將示範如何處理這些挑戰。</span><span class="sxs-lookup"><span data-stu-id="5eb14-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="5eb14-107">在 SQL SELECT 陳述式中分組 DbExpression 節點</span><span class="sxs-lookup"><span data-stu-id="5eb14-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="5eb14-108">一般 SQL 陳述式具有下列形狀的巢狀結構：</span><span class="sxs-lookup"><span data-stu-id="5eb14-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="5eb14-109">一個或多個子句可能是空的。</span><span class="sxs-lookup"><span data-stu-id="5eb14-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="5eb14-110">巢狀 SELECT 陳述式可能會出現於任何一行。</span><span class="sxs-lookup"><span data-stu-id="5eb14-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="5eb14-111">將查詢命令樹轉譯成 SQL SELECT 陳述式的可能轉譯方式會針對每個關係運算子產生一個子查詢。</span><span class="sxs-lookup"><span data-stu-id="5eb14-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="5eb14-112">不過，這種結果可能會導致難以讀取的非必要巢狀子查詢。</span><span class="sxs-lookup"><span data-stu-id="5eb14-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="5eb14-113">在某些資料存放區上，查詢的執行效能可能會不佳。</span><span class="sxs-lookup"><span data-stu-id="5eb14-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="5eb14-114">例如，請考量下列查詢命令樹：</span><span class="sxs-lookup"><span data-stu-id="5eb14-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="5eb14-115">沒有效率的轉譯會產生：</span><span class="sxs-lookup"><span data-stu-id="5eb14-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="5eb14-116">請注意，每個關聯運算式節點都會成為新的 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5eb14-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="5eb14-117">因此，請務必盡可能將運算式節點彙總成單一 SQL SELECT 陳述式，同時保留正確性。</span><span class="sxs-lookup"><span data-stu-id="5eb14-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="5eb14-118">上述範例的這種彙總結果為：</span><span class="sxs-lookup"><span data-stu-id="5eb14-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="5eb14-119">在 SQL SELECT 陳述式中扁平化聯結</span><span class="sxs-lookup"><span data-stu-id="5eb14-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="5eb14-120">將多個節點彙總成單一 SQL SELECT 陳述式的其中一個案例就是將多個聯結運算式彙總成單一 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5eb14-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="5eb14-121">DbJoinExpression 代表介於兩個輸入之間的單一聯結。</span><span class="sxs-lookup"><span data-stu-id="5eb14-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="5eb14-122">不過，您可以將多個聯結指定為單一 SQL SELECT 陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="5eb14-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="5eb14-123">在該案例中，這些聯結會依照指定的順序執行。</span><span class="sxs-lookup"><span data-stu-id="5eb14-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="5eb14-124">您可以更輕鬆地將左背面聯結 (顯示為另一個聯結之左子系的聯結) 扁平化為單一 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5eb14-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="5eb14-125">例如，請考量下列查詢命令樹：</span><span class="sxs-lookup"><span data-stu-id="5eb14-125">For example, consider the following query command tree:</span></span>

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="5eb14-126">這個命令樹可正確轉譯成：</span><span class="sxs-lookup"><span data-stu-id="5eb14-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="5eb14-127">不過，您無法輕鬆地扁平化非左背面聯結，而且不應該嘗試扁平化這些聯結。</span><span class="sxs-lookup"><span data-stu-id="5eb14-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="5eb14-128">例如，下列查詢命令樹中的聯結：</span><span class="sxs-lookup"><span data-stu-id="5eb14-128">For example, the joins in the following query command tree:</span></span>

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="5eb14-129">會轉譯成具有子查詢的 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5eb14-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="5eb14-130">輸入別名重新導向</span><span class="sxs-lookup"><span data-stu-id="5eb14-130">Input Alias Redirecting</span></span>

<span data-ttu-id="5eb14-131">為了說明輸入別名重新導向，請考量關聯運算式的結構，例如 DbFilterExpression、DbProjectExpression、DbCrossJoinExpression、DbJoinExpression、DbSortExpression、DbGroupByExpression、DbApplyExpression 和 DbSkipExpression。</span><span class="sxs-lookup"><span data-stu-id="5eb14-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="5eb14-132">其中每一個型別都具有一個或多個描述輸入集合的 Input 屬性，而且對應至每個輸入的繫結變數會在集合周遊期間用來代表該輸入的每個項目。</span><span class="sxs-lookup"><span data-stu-id="5eb14-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="5eb14-133">例如，參考 DbFilterExpression 之 Predicate 屬性或 DbProjectExpression 之 Projection 屬性中的輸入項目時，就會使用此繫結變數。</span><span class="sxs-lookup"><span data-stu-id="5eb14-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="5eb14-134">將多個關聯運算式節點彙總成單一 SQL SELECT 陳述式，並且評估屬於關聯運算式一部分的運算式 (例如，屬於 DbProjectExpression 之 Projection 屬性的一部分) 時，它所使用的繫結變數可能不會與輸入的別名相同，因為多個運算式繫結必須重新導向至單一範圍。</span><span class="sxs-lookup"><span data-stu-id="5eb14-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="5eb14-135">這個問題就稱為別名重新命名。</span><span class="sxs-lookup"><span data-stu-id="5eb14-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="5eb14-136">請考量本主題的第一個範例。</span><span class="sxs-lookup"><span data-stu-id="5eb14-136">Consider the first example in this topic.</span></span> <span data-ttu-id="5eb14-137">如果要進行自然轉譯並且轉譯 Projection a.x (DbPropertyExpression(a, x))，將它轉譯成 `a.x` 是正確的作法，因為我們已經將輸入的別名指定為 "a"，以符合繫結變數。</span><span class="sxs-lookup"><span data-stu-id="5eb14-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="5eb14-138">不過，將這兩個節點彙總成單一 SQL SELECT 陳述式時，您就必須將相同的 DbPropertyExpression 轉譯成 `b.x`，因為輸入已經具有 "b" 的別名。</span><span class="sxs-lookup"><span data-stu-id="5eb14-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="5eb14-139">聯結別名扁平化</span><span class="sxs-lookup"><span data-stu-id="5eb14-139">Join Alias Flattening</span></span>

<span data-ttu-id="5eb14-140">與輸出命令樹中任何其他關聯運算式不同的是，DbJoinExpression 所輸出的結果型別是包含兩個資料行的資料列，而且其中每一個資料行都會對應至其中一個輸入。</span><span class="sxs-lookup"><span data-stu-id="5eb14-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="5eb14-141">當 DbPropertyExpression 建置為存取源自聯結的純量屬性時，則透過另一個 DbPropertyExpression。</span><span class="sxs-lookup"><span data-stu-id="5eb14-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="5eb14-142">範例包括範例 2 中的 "a.b.y" 以及範例 3 中的 "b.c.y"。</span><span class="sxs-lookup"><span data-stu-id="5eb14-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="5eb14-143">不過，在對應的 SQL 陳述式中，這些項目都會當做 "b.y" 參考。</span><span class="sxs-lookup"><span data-stu-id="5eb14-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="5eb14-144">這種重新指定別名的作業稱為聯結別名扁平化。</span><span class="sxs-lookup"><span data-stu-id="5eb14-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="5eb14-145">資料行名稱和範圍別名重新命名</span><span class="sxs-lookup"><span data-stu-id="5eb14-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="5eb14-146">如果某個具有聯結的 SQL SELECT 查詢必須透過投影完成，從輸入列舉所有參與的資料行時，可能會發生名稱衝突，因為多個輸入可能具有相同的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="5eb14-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="5eb14-147">若要避免衝突，請針對資料行使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="5eb14-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="5eb14-148">此外，在扁平化聯結時，參與的資料表 (或子查詢) 可能會具有衝突的別名，因此必須重新命名這些別名。</span><span class="sxs-lookup"><span data-stu-id="5eb14-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="5eb14-149">避免使用 SELECT \*</span><span class="sxs-lookup"><span data-stu-id="5eb14-149">Avoid SELECT \*</span></span>

<span data-ttu-id="5eb14-150">請勿使用 `SELECT *`，從基底資料表中選取。</span><span class="sxs-lookup"><span data-stu-id="5eb14-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="5eb14-151">中的儲存體模型[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]應用程式可能只包含資料庫資料表中的資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="5eb14-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="5eb14-152">在此情況下，`SELECT *` 可能會產生錯誤的結果。</span><span class="sxs-lookup"><span data-stu-id="5eb14-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="5eb14-153">因此，您應該改用參與運算式之結果型別中的資料行名稱來指定所有參與的資料行。</span><span class="sxs-lookup"><span data-stu-id="5eb14-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="5eb14-154">重複使用運算式</span><span class="sxs-lookup"><span data-stu-id="5eb14-154">Reuse of Expressions</span></span>

<span data-ttu-id="5eb14-155">您可以在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 所傳遞的查詢命令樹中重複使用運算式。</span><span class="sxs-lookup"><span data-stu-id="5eb14-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5eb14-156">請勿假設每個運算式都只會出現在查詢命令樹中一次。</span><span class="sxs-lookup"><span data-stu-id="5eb14-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="5eb14-157">對應基本型別</span><span class="sxs-lookup"><span data-stu-id="5eb14-157">Mapping Primitive Types</span></span>

<span data-ttu-id="5eb14-158">將概念 (EDM) 型別對應至提供者型別時，您應該對應至最廣泛的型別 (Int32)，以便容納所有可能的值。</span><span class="sxs-lookup"><span data-stu-id="5eb14-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="5eb14-159">此外，請避免對應至型別無法用於許多作業，例如 BLOB 型別 (例如`ntext`SQL Server 中)。</span><span class="sxs-lookup"><span data-stu-id="5eb14-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="5eb14-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb14-160">See also</span></span>

- [<span data-ttu-id="5eb14-161">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="5eb14-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
