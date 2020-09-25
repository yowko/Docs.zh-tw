---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 9433e7a7ffdc3a7e32900981dca95eefde32f290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204433"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="bce23-102">Entity SQL 與 Transact-sql 有何不同</span><span class="sxs-lookup"><span data-stu-id="bce23-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="bce23-103">本文描述 Entity SQL 和 Transact-sql 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="bce23-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="bce23-104">繼承和關聯性支援</span><span class="sxs-lookup"><span data-stu-id="bce23-104">Inheritance and Relationships Support</span></span>  

 <span data-ttu-id="bce23-105">Entity SQL 直接與概念實體架構一起運作並支援概念模型功能，例如繼承和關聯性。</span><span class="sxs-lookup"><span data-stu-id="bce23-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="bce23-106">當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。</span><span class="sxs-lookup"><span data-stu-id="bce23-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="bce23-107">Entity SQL (中的 [oftype](oftype-entity-sql.md) 運算子類似于 `oftype` c # 序列) 提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="bce23-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="bce23-108">集合的支援</span><span class="sxs-lookup"><span data-stu-id="bce23-108">Support for Collections</span></span>  

 <span data-ttu-id="bce23-109">Entity SQL 會將集合視為第一個類別的實體。</span><span class="sxs-lookup"><span data-stu-id="bce23-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="bce23-110">例如：</span><span class="sxs-lookup"><span data-stu-id="bce23-110">For example:</span></span>  
  
- <span data-ttu-id="bce23-111">集合運算式在 `from` 子句中是有效的。</span><span class="sxs-lookup"><span data-stu-id="bce23-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="bce23-112">`in` 和 `exists` 子查詢已通用化，可允許任何集合。</span><span class="sxs-lookup"><span data-stu-id="bce23-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="bce23-113">子查詢是一種集合。</span><span class="sxs-lookup"><span data-stu-id="bce23-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="bce23-114">`e1 in e2` 和 `exists(e)` 是用來執行這些作業的 Entity SQL 結構。</span><span class="sxs-lookup"><span data-stu-id="bce23-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="bce23-115">Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。</span><span class="sxs-lookup"><span data-stu-id="bce23-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="bce23-116">聯結可針對集合操作。</span><span class="sxs-lookup"><span data-stu-id="bce23-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="bce23-117">運算式的支援</span><span class="sxs-lookup"><span data-stu-id="bce23-117">Support for Expressions</span></span>  

 <span data-ttu-id="bce23-118">Transact-sql 有 (資料表) 和運算式 (資料列和資料行) 的子查詢。</span><span class="sxs-lookup"><span data-stu-id="bce23-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="bce23-119">為了支援集合和嵌套集合，Entity SQL 會將所有專案都設為運算式。</span><span class="sxs-lookup"><span data-stu-id="bce23-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="bce23-120">Entity SQL 比 Transact-sql 更具可組合，每個運算式都可以在任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="bce23-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="bce23-121">查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="bce23-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="bce23-122">如需 Entity SQL 中不支援之 Transact-sql 運算式的詳細資訊，請參閱 [不](unsupported-expressions-entity-sql.md)支援的運算式。</span><span class="sxs-lookup"><span data-stu-id="bce23-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="bce23-123">以下是所有有效的 Entity SQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="bce23-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="bce23-124">子查詢的統一處理</span><span class="sxs-lookup"><span data-stu-id="bce23-124">Uniform Treatment of Subqueries</span></span>  

 <span data-ttu-id="bce23-125">基於資料表的強調，Transact-sql 會執行子查詢的內容相關轉譯。</span><span class="sxs-lookup"><span data-stu-id="bce23-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="bce23-126">例如，子句中的子查詢 `from` 會視為 (資料表) 的多重集。</span><span class="sxs-lookup"><span data-stu-id="bce23-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="bce23-127">但是 `select` 子句中使用的相同子查詢會視為純量子查詢。</span><span class="sxs-lookup"><span data-stu-id="bce23-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="bce23-128">同樣地，在運算子左邊使用的子查詢會 `in` 視為純量子查詢，而右邊則應為多重集子查詢。</span><span class="sxs-lookup"><span data-stu-id="bce23-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="bce23-129">Entity SQL 消除了這些差異。</span><span class="sxs-lookup"><span data-stu-id="bce23-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="bce23-130">運算式的統一解譯不依賴使用此運算式的內容。</span><span class="sxs-lookup"><span data-stu-id="bce23-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="bce23-131">Entity SQL 會將所有子查詢視為多重集子查詢。</span><span class="sxs-lookup"><span data-stu-id="bce23-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="bce23-132">如果自子查詢需要純量值，Entity SQL 會提供在 `anyelement` 集合上操作的運算子 (在此案例中為子查詢) ，然後從集合中解壓縮單一值。</span><span class="sxs-lookup"><span data-stu-id="bce23-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="bce23-133">避免子查詢的隱含強制型轉</span><span class="sxs-lookup"><span data-stu-id="bce23-133">Avoiding Implicit Coercions for Subqueries</span></span>  

 <span data-ttu-id="bce23-134">統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。</span><span class="sxs-lookup"><span data-stu-id="bce23-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="bce23-135">具體而言，在 Transact-sql 中，資料列的多重集 (具有單一欄位) 會隱含地轉換成純量值，其資料類型為欄位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bce23-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="bce23-136">Entity SQL 不支援這個隱含強制型轉。</span><span class="sxs-lookup"><span data-stu-id="bce23-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="bce23-137">Entity SQL 提供 `ANYELEMENT` 從集合中解壓縮單一值的運算子，以及可避免在 `select value` 查詢運算式期間建立資料列包裝函式的子句。</span><span class="sxs-lookup"><span data-stu-id="bce23-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="bce23-138">Select Value：避免隱含資料列包裝函式</span><span class="sxs-lookup"><span data-stu-id="bce23-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  

 <span data-ttu-id="bce23-139">Transact-sql 子查詢中的 select 子句會隱含地在子句中的專案周圍建立資料列包裝函式。</span><span class="sxs-lookup"><span data-stu-id="bce23-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="bce23-140">這意味我們無法建立純量或物件的集合。</span><span class="sxs-lookup"><span data-stu-id="bce23-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="bce23-141">Transact-sql 允許在 `rowtype` 具有相同資料類型的一個欄位與單一值之間進行隱含強制型轉。</span><span class="sxs-lookup"><span data-stu-id="bce23-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="bce23-142">Entity SQL 提供 `select value` 子句來略過隱含資料列結構。</span><span class="sxs-lookup"><span data-stu-id="bce23-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="bce23-143">`select value` 子句中只能指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="bce23-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="bce23-144">使用這類子句時，不會針對子句中的專案來建立資料列包裝函式， `select` 而且可能會產生所需形狀的集合（例如） `select value a` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="bce23-145">Entity SQL 也提供資料列的函式來建立任意的資料列。</span><span class="sxs-lookup"><span data-stu-id="bce23-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="bce23-146">`select` 接受投影中的一或多個專案，並產生具有欄位的資料記錄：</span><span class="sxs-lookup"><span data-stu-id="bce23-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="bce23-147">左邊相互關聯與別名</span><span class="sxs-lookup"><span data-stu-id="bce23-147">Left Correlation and Aliasing</span></span>  

 <span data-ttu-id="bce23-148">在 Transact-sql 中，指定範圍內的運算式 (單一子句 `select` ，例如或 `from`) 無法參考先前在相同範圍中定義的運算式。</span><span class="sxs-lookup"><span data-stu-id="bce23-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="bce23-149">某些 SQL (方言（包括 Transact-sql) ）在子句中支援這些功能的有限形式 `from` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="bce23-150">Entity SQL 一般化子句中的左 `from` 相互關聯，並一致地處理它們。</span><span class="sxs-lookup"><span data-stu-id="bce23-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="bce23-151">`from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。</span><span class="sxs-lookup"><span data-stu-id="bce23-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="bce23-152">Entity SQL 也會對牽涉到子句的查詢施加額外限制 `group by` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="bce23-153">`select`這類查詢的子句和子句中的運算式， `having` 只能透過其別名來參考索引 `group by` 鍵。</span><span class="sxs-lookup"><span data-stu-id="bce23-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="bce23-154">下列結構在 Transact-sql 中是有效的，但不在 Entity SQL 中：</span><span class="sxs-lookup"><span data-stu-id="bce23-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="bce23-155">若要在 Entity SQL 中執行此動作：</span><span class="sxs-lookup"><span data-stu-id="bce23-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="bce23-156">參考資料表 (集合) 的資料行 (屬性)</span><span class="sxs-lookup"><span data-stu-id="bce23-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  

 <span data-ttu-id="bce23-157">Entity SQL 中的所有資料行參考都必須使用資料表別名來限定。</span><span class="sxs-lookup"><span data-stu-id="bce23-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="bce23-158">下列結構 (假設 `a` 是資料表) 的有效資料行 `T` 在 transact-sql 中有效，而不是在 Entity SQL 中。</span><span class="sxs-lookup"><span data-stu-id="bce23-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="bce23-159">Entity SQL 表單為</span><span class="sxs-lookup"><span data-stu-id="bce23-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="bce23-160">資料表別名在 `from` 子句中為選擇性。</span><span class="sxs-lookup"><span data-stu-id="bce23-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="bce23-161">資料表名稱會當做隱含別名使用。</span><span class="sxs-lookup"><span data-stu-id="bce23-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="bce23-162">Entity SQL 也會允許下列表單：</span><span class="sxs-lookup"><span data-stu-id="bce23-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="bce23-163">導覽物件</span><span class="sxs-lookup"><span data-stu-id="bce23-163">Navigation Through Objects</span></span>  

 <span data-ttu-id="bce23-164">Transact-sql 使用 "." 標記法來參考 (資料表) 資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="bce23-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="bce23-165">Entity SQL 會擴充這個標記法 (從程式設計語言中借用) 以支援透過物件的屬性進行導覽。</span><span class="sxs-lookup"><span data-stu-id="bce23-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="bce23-166">例如，如果 `p` 是 person 型別的運算式，則以下是用來參考此人員位址之城市的 Entity SQL 語法。</span><span class="sxs-lookup"><span data-stu-id="bce23-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="bce23-167">不支援 \*</span><span class="sxs-lookup"><span data-stu-id="bce23-167">No Support for \*</span></span>  

 <span data-ttu-id="bce23-168">Transact-sql 支援使用不合格的 \* 語法做為整個資料列的別名，而限定 \* 語法 (t. \*) 作為該資料表欄位的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="bce23-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="bce23-169">此外，Transact-sql 也可 () 匯總的特殊計數 \* ，包括 null。</span><span class="sxs-lookup"><span data-stu-id="bce23-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="bce23-170">Entity SQL 不支援 \* 結構。</span><span class="sxs-lookup"><span data-stu-id="bce23-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="bce23-171">表單的 transact-SQL 查詢 `select * from T` 和 `select T1.* from T1, T2...` 可以分別以和 Entity SQL 表示 `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="bce23-172">此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。</span><span class="sxs-lookup"><span data-stu-id="bce23-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="bce23-173">Entity SQL 不支援 `count(*)` 匯總。</span><span class="sxs-lookup"><span data-stu-id="bce23-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="bce23-174">請改用 `count(0)`。</span><span class="sxs-lookup"><span data-stu-id="bce23-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="bce23-175">變更成 Group By</span><span class="sxs-lookup"><span data-stu-id="bce23-175">Changes to Group By</span></span>  

 <span data-ttu-id="bce23-176">Entity SQL 支援索引鍵的別名 `group by` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="bce23-177">`select`子句和子句中的運算式 `having` 必須透過這些別名來參考索引 `group by` 鍵。</span><span class="sxs-lookup"><span data-stu-id="bce23-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="bce23-178">例如，此 Entity SQL 語法：</span><span class="sxs-lookup"><span data-stu-id="bce23-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="bce23-179">...相當於下列 Transact-sql：</span><span class="sxs-lookup"><span data-stu-id="bce23-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="bce23-180">以集合為基礎的彙總</span><span class="sxs-lookup"><span data-stu-id="bce23-180">Collection-Based Aggregates</span></span>  

 <span data-ttu-id="bce23-181">Entity SQL 支援兩種類型的匯總。</span><span class="sxs-lookup"><span data-stu-id="bce23-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="bce23-182">以集合為基礎的彙總會針對集合運作，並產生彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="bce23-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="bce23-183">這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。</span><span class="sxs-lookup"><span data-stu-id="bce23-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="bce23-184">例如：</span><span class="sxs-lookup"><span data-stu-id="bce23-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="bce23-185">Entity SQL 也支援 SQL 樣式的匯總。</span><span class="sxs-lookup"><span data-stu-id="bce23-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="bce23-186">例如：</span><span class="sxs-lookup"><span data-stu-id="bce23-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="bce23-187">ORDER BY 子句使用方式</span><span class="sxs-lookup"><span data-stu-id="bce23-187">ORDER BY Clause Usage</span></span>  

<span data-ttu-id="bce23-188">Transact-sql `ORDER BY` 只允許在最上層區塊中指定子句 `SELECT .. FROM .. WHERE` 。</span><span class="sxs-lookup"><span data-stu-id="bce23-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="bce23-189">在 Entity SQL 中，您可以使用嵌套的 `ORDER BY` 運算式，並將它放在查詢中的任何位置，但不會保留在巢狀查詢中的順序。</span><span class="sxs-lookup"><span data-stu-id="bce23-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="bce23-190">識別碼</span><span class="sxs-lookup"><span data-stu-id="bce23-190">Identifiers</span></span>  

 <span data-ttu-id="bce23-191">在 Transact-sql 中，識別碼比較是以目前資料庫的定序為基礎。</span><span class="sxs-lookup"><span data-stu-id="bce23-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="bce23-192">在 Entity SQL 中，識別碼一律不區分大小寫且區分重音 (也就是說，Entity SQL 區別重音和非重音字元;例如，' a ' 不等於 ' ấ ' ) 。</span><span class="sxs-lookup"><span data-stu-id="bce23-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="bce23-193">Entity SQL 會將出現相同但不同字碼頁的字母版本視為不同的字元。</span><span class="sxs-lookup"><span data-stu-id="bce23-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="bce23-194">如需詳細資訊，請參閱 [輸入字元集](input-character-set-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="bce23-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="bce23-195">Entity SQL 中無法使用 Transact-SQL 功能</span><span class="sxs-lookup"><span data-stu-id="bce23-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  

 <span data-ttu-id="bce23-196">Entity SQL 不提供下列 Transact-sql 功能。</span><span class="sxs-lookup"><span data-stu-id="bce23-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="bce23-197">DML</span><span class="sxs-lookup"><span data-stu-id="bce23-197">DML</span></span>  
 <span data-ttu-id="bce23-198">Entity SQL 目前未提供 DML 語句的支援 (insert、update、delete) 。</span><span class="sxs-lookup"><span data-stu-id="bce23-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="bce23-199">DDL</span><span class="sxs-lookup"><span data-stu-id="bce23-199">DDL</span></span>  
 <span data-ttu-id="bce23-200">Entity SQL 在目前版本中不支援 DDL。</span><span class="sxs-lookup"><span data-stu-id="bce23-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="bce23-201">命令式程式設計</span><span class="sxs-lookup"><span data-stu-id="bce23-201">Imperative Programming</span></span>  
 <span data-ttu-id="bce23-202">Entity SQL 不會提供命令式程式設計的支援，與 Transact-sql 不同。</span><span class="sxs-lookup"><span data-stu-id="bce23-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="bce23-203">請改用程式語言。</span><span class="sxs-lookup"><span data-stu-id="bce23-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="bce23-204">群組函式</span><span class="sxs-lookup"><span data-stu-id="bce23-204">Grouping Functions</span></span>  
 <span data-ttu-id="bce23-205">Entity SQL 尚未提供群組函式的支援 (例如 CUBE、ROLLUP 和 GROUPING_SET) 。</span><span class="sxs-lookup"><span data-stu-id="bce23-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="bce23-206">分析函式</span><span class="sxs-lookup"><span data-stu-id="bce23-206">Analytic Functions</span></span>  
 <span data-ttu-id="bce23-207">Entity SQL 尚未 () 提供分析功能的支援。</span><span class="sxs-lookup"><span data-stu-id="bce23-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="bce23-208">內建函式，運算子</span><span class="sxs-lookup"><span data-stu-id="bce23-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="bce23-209">Entity SQL 支援 Transact-sql 內建函數和運算子的子集。</span><span class="sxs-lookup"><span data-stu-id="bce23-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="bce23-210">主要存放區提供者可能會支援這些運算子和函式。</span><span class="sxs-lookup"><span data-stu-id="bce23-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="bce23-211">Entity SQL 會使用提供者資訊清單中宣告的存放區特有函式。</span><span class="sxs-lookup"><span data-stu-id="bce23-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="bce23-212">此外，Entity Framework 可讓您宣告內建及使用者定義的現有存放區函數，以供 Entity SQL 使用。</span><span class="sxs-lookup"><span data-stu-id="bce23-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="bce23-213">提示</span><span class="sxs-lookup"><span data-stu-id="bce23-213">Hints</span></span>  
 <span data-ttu-id="bce23-214">Entity SQL 不會提供查詢提示的機制。</span><span class="sxs-lookup"><span data-stu-id="bce23-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="bce23-215">批次處理查詢結果</span><span class="sxs-lookup"><span data-stu-id="bce23-215">Batching Query Results</span></span>  
 <span data-ttu-id="bce23-216">Entity SQL 不支援批次處理查詢結果。</span><span class="sxs-lookup"><span data-stu-id="bce23-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="bce23-217">例如，以下是以批次) 傳送的有效 Transact-sql (：</span><span class="sxs-lookup"><span data-stu-id="bce23-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="bce23-218">但是，不支援對等的 Entity SQL：</span><span class="sxs-lookup"><span data-stu-id="bce23-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="bce23-219">Entity SQL 只針對每個命令支援一個結果產生查詢語句。</span><span class="sxs-lookup"><span data-stu-id="bce23-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce23-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce23-220">See also</span></span>

- [<span data-ttu-id="bce23-221">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="bce23-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="bce23-222">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="bce23-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
