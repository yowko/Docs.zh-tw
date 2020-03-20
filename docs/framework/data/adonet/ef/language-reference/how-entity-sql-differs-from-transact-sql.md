---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150227"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="aef92-102">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="aef92-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="aef92-103">本主題介紹和交易[!INCLUDE[esql](../../../../../../includes/esql-md.md)]SQL 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="aef92-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="aef92-104">繼承和關聯性支援</span><span class="sxs-lookup"><span data-stu-id="aef92-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-105">直接與概念實體架構配合使用，並支援概念模型功能，如繼承和關係。</span><span class="sxs-lookup"><span data-stu-id="aef92-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="aef92-106">當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。</span><span class="sxs-lookup"><span data-stu-id="aef92-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="aef92-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中的[類型](oftype-entity-sql.md)運算子（類似于`oftype`C# 序列中）提供此功能。</span><span class="sxs-lookup"><span data-stu-id="aef92-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="aef92-108">集合的支援</span><span class="sxs-lookup"><span data-stu-id="aef92-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-109">將集合視為一流的實體。</span><span class="sxs-lookup"><span data-stu-id="aef92-109">treats collections as first-class entities.</span></span> <span data-ttu-id="aef92-110">例如：</span><span class="sxs-lookup"><span data-stu-id="aef92-110">For example:</span></span>  
  
- <span data-ttu-id="aef92-111">集合運算式在 `from` 子句中是有效的。</span><span class="sxs-lookup"><span data-stu-id="aef92-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="aef92-112">`in` 和 `exists` 子查詢已通用化，可允許任何集合。</span><span class="sxs-lookup"><span data-stu-id="aef92-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="aef92-113">子查詢是一種集合。</span><span class="sxs-lookup"><span data-stu-id="aef92-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="aef92-114">`e1 in e2` 和 `exists(e)` 是用來執行這些作業的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 建構。</span><span class="sxs-lookup"><span data-stu-id="aef92-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="aef92-115">Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。</span><span class="sxs-lookup"><span data-stu-id="aef92-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="aef92-116">聯結可針對集合操作。</span><span class="sxs-lookup"><span data-stu-id="aef92-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="aef92-117">運算式的支援</span><span class="sxs-lookup"><span data-stu-id="aef92-117">Support for Expressions</span></span>  
 <span data-ttu-id="aef92-118">Transact-SQL 具有子查詢（表）和運算式（行和列）。</span><span class="sxs-lookup"><span data-stu-id="aef92-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="aef92-119">要支援集合和嵌套集合，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]使一切成為運算式。</span><span class="sxs-lookup"><span data-stu-id="aef92-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-120">比 Transact-SQL 更可組合， 每個運算式都可以在任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="aef92-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="aef92-121">查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="aef92-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="aef92-122">有關 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不支援的 Transact SQL 運算式的資訊，請參閱[。](unsupported-expressions-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="aef92-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="aef92-123">下列全都是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢：</span><span class="sxs-lookup"><span data-stu-id="aef92-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="aef92-124">子查詢的統一處理</span><span class="sxs-lookup"><span data-stu-id="aef92-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="aef92-125">鑒於它強調表，Transact-SQL 對子查詢執行上下文解釋。</span><span class="sxs-lookup"><span data-stu-id="aef92-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="aef92-126">例如，子句中的`from`子查詢被視為多集（表）。</span><span class="sxs-lookup"><span data-stu-id="aef92-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="aef92-127">但是 `select` 子句中使用的相同子查詢會視為純量子查詢。</span><span class="sxs-lookup"><span data-stu-id="aef92-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="aef92-128">同樣，運算子左側`in`使用的子查詢被視為標量子查詢，而右側應被視為多集子查詢。</span><span class="sxs-lookup"><span data-stu-id="aef92-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-129">會消除這些差異。</span><span class="sxs-lookup"><span data-stu-id="aef92-129">eliminates these differences.</span></span> <span data-ttu-id="aef92-130">運算式的統一解譯不依賴使用此運算式的內容。</span><span class="sxs-lookup"><span data-stu-id="aef92-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-131">將所有子查詢視為多集子查詢。</span><span class="sxs-lookup"><span data-stu-id="aef92-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="aef92-132">如果需要子查詢中的標量值，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]請提供對集合操作的`anyelement`運算子（在本例中為子查詢），並從集合中提取單例值。</span><span class="sxs-lookup"><span data-stu-id="aef92-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="aef92-133">避免子查詢的隱含強制型轉</span><span class="sxs-lookup"><span data-stu-id="aef92-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="aef92-134">統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。</span><span class="sxs-lookup"><span data-stu-id="aef92-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="aef92-135">具體而言，在 Transact-SQL 中，多組行（具有單個欄位）隱式轉換為資料類型為欄位的標量值。</span><span class="sxs-lookup"><span data-stu-id="aef92-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-136">不支援這種隱含強制型轉。</span><span class="sxs-lookup"><span data-stu-id="aef92-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-137">提供了可從集合中擷取單一值的 ANYELEMENT 運算子，以及一個可在查詢運算式期間避免建立資料列包裝函式的 `select value` 子句。</span><span class="sxs-lookup"><span data-stu-id="aef92-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="aef92-138">Select Value：避免隱含資料列包裝函式</span><span class="sxs-lookup"><span data-stu-id="aef92-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="aef92-139">Transact-SQL 子查詢中的 select 子查詢中隱式創建圍繞子句中的項的行包裝器。</span><span class="sxs-lookup"><span data-stu-id="aef92-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="aef92-140">這意味我們無法建立純量或物件的集合。</span><span class="sxs-lookup"><span data-stu-id="aef92-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="aef92-141">Transact-SQL 允許在具有一個欄位的行型和相同資料類型的單例值之間隱式強制。</span><span class="sxs-lookup"><span data-stu-id="aef92-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-142">提供 `select value` 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="aef92-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="aef92-143">`select value` 子句中只能指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="aef92-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="aef92-144">使用這類子句時，將不會建構包含 `select` 子句中這個項目的資料列包裝函式，並且可以產生所需形狀的集合，例如：`select value a`。</span><span class="sxs-lookup"><span data-stu-id="aef92-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-145">也提供資料列建構函式來建構任意資料列。</span><span class="sxs-lookup"><span data-stu-id="aef92-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="aef92-146">`select` 會擷取投影中的一個或多個項目，並產生具有欄位的資料記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aef92-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="aef92-147">左邊相互關聯與別名</span><span class="sxs-lookup"><span data-stu-id="aef92-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="aef92-148">在 Transact-SQL 中，給定作用域中的運算式（單個子句`select`（`from`如 或 ） 不能引用之前在同一作用域中定義的運算式。</span><span class="sxs-lookup"><span data-stu-id="aef92-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="aef92-149">SQL 的某些方言（包括 Transact-SQL）確實支援`from`子句中的有限形式。</span><span class="sxs-lookup"><span data-stu-id="aef92-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-150">概括子句中的`from`左相關性，並統一處理它們。</span><span class="sxs-lookup"><span data-stu-id="aef92-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="aef92-151">`from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。</span><span class="sxs-lookup"><span data-stu-id="aef92-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-152">也會針對與 `group by` 子句有關的查詢做出其他限制。</span><span class="sxs-lookup"><span data-stu-id="aef92-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="aef92-153">此類查詢的`select`子句和`having`子句中的運算式只能通過其別名引用`group by`鍵。</span><span class="sxs-lookup"><span data-stu-id="aef92-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="aef92-154">以下構造在 Transact-SQL 中有效，但不在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中：</span><span class="sxs-lookup"><span data-stu-id="aef92-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="aef92-155">若要在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中進行這項處理：</span><span class="sxs-lookup"><span data-stu-id="aef92-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="aef92-156">參考資料表 (集合) 的資料行 (屬性)</span><span class="sxs-lookup"><span data-stu-id="aef92-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="aef92-157">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的所有資料行參考都必須以資料表別名來限定。</span><span class="sxs-lookup"><span data-stu-id="aef92-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="aef92-158">以下構造（假設是`a`表`T`的有效列）在 Transact-SQL 中有效，但在 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]無效。</span><span class="sxs-lookup"><span data-stu-id="aef92-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="aef92-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 格式如下：</span><span class="sxs-lookup"><span data-stu-id="aef92-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="aef92-160">資料表別名在 `from` 子句中為選擇性。</span><span class="sxs-lookup"><span data-stu-id="aef92-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="aef92-161">資料表名稱會當做隱含別名使用。</span><span class="sxs-lookup"><span data-stu-id="aef92-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-162">也會顯示下列格式：</span><span class="sxs-lookup"><span data-stu-id="aef92-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="aef92-163">導覽物件</span><span class="sxs-lookup"><span data-stu-id="aef92-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="aef92-164">Transact-SQL 使用"." 標記法來引用表的列（一行）。</span><span class="sxs-lookup"><span data-stu-id="aef92-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-165">會擴充這個標記法 (從程式語言借用) 來支援物件之屬性的導覽。</span><span class="sxs-lookup"><span data-stu-id="aef92-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="aef92-166">例如，如果 `p` 是 Person 型別的運算式，下列是用來參考這個人之地址所在城市的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法。</span><span class="sxs-lookup"><span data-stu-id="aef92-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="aef92-167">\* 表示不支援</span><span class="sxs-lookup"><span data-stu-id="aef92-167">No Support for \*</span></span>  
 <span data-ttu-id="aef92-168">Transact-SQL 支援將限定的 + 語法作為整個行的別名，並將\*限定語法 （t.\*） 作為該表字段的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="aef92-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="aef92-169">此外，Transact-SQL 允許特殊計數 （\*） 聚合，其中包括 null。</span><span class="sxs-lookup"><span data-stu-id="aef92-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-170">不支援 \* 建構。</span><span class="sxs-lookup"><span data-stu-id="aef92-170">does not support the \* construct.</span></span> <span data-ttu-id="aef92-171">`select * from T`表單的轉算 SQL 查詢，`select T1.* from T1, T2...`並可以分別以[!INCLUDE[esql](../../../../../../includes/esql-md.md)]和`select value t from T as t``select value t1 from T1 as t1, T2 as t2...`表示。</span><span class="sxs-lookup"><span data-stu-id="aef92-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="aef92-172">此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。</span><span class="sxs-lookup"><span data-stu-id="aef92-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-173">不支援 `count(*)` 彙總，</span><span class="sxs-lookup"><span data-stu-id="aef92-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="aef92-174">請改用 `count(0)`。</span><span class="sxs-lookup"><span data-stu-id="aef92-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="aef92-175">變更成 Group By</span><span class="sxs-lookup"><span data-stu-id="aef92-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-176">支援 `group by` 索引鍵的別名。</span><span class="sxs-lookup"><span data-stu-id="aef92-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="aef92-177">子句和`select``having`子句中的運算式必須通過這些別名引用`group by`鍵。</span><span class="sxs-lookup"><span data-stu-id="aef92-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="aef92-178">例如，這個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法：</span><span class="sxs-lookup"><span data-stu-id="aef92-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="aef92-179">...等效于以下交易 SQL：</span><span class="sxs-lookup"><span data-stu-id="aef92-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="aef92-180">以集合為基礎的彙總</span><span class="sxs-lookup"><span data-stu-id="aef92-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-181">支援兩種彙總。</span><span class="sxs-lookup"><span data-stu-id="aef92-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="aef92-182">以集合為基礎的彙總會針對集合運作，並產生彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="aef92-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="aef92-183">這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。</span><span class="sxs-lookup"><span data-stu-id="aef92-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="aef92-184">例如：</span><span class="sxs-lookup"><span data-stu-id="aef92-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-185">也支援 SQL 樣式彙總。</span><span class="sxs-lookup"><span data-stu-id="aef92-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="aef92-186">例如：</span><span class="sxs-lookup"><span data-stu-id="aef92-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="aef92-187">ORDER BY 子句使用方式</span><span class="sxs-lookup"><span data-stu-id="aef92-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="aef92-188">Transact-SQL`ORDER BY`允許僅在最`SELECT .. FROM .. WHERE`頂層塊中指定子句。</span><span class="sxs-lookup"><span data-stu-id="aef92-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="aef92-189">在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中可以使用嵌套`ORDER BY`運算式，它可以放置在查詢的任意位置，但不會保留巢狀查詢中的排序。</span><span class="sxs-lookup"><span data-stu-id="aef92-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="aef92-190">識別碼</span><span class="sxs-lookup"><span data-stu-id="aef92-190">Identifiers</span></span>  
 <span data-ttu-id="aef92-191">在 Transact-SQL 中，識別碼比較基於當前資料庫的排序規則。</span><span class="sxs-lookup"><span data-stu-id="aef92-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="aef92-192">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，識別項一律不會區分大小寫，但是會區分腔調字 (Accent Sensitive) (亦即，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會區別有腔調和無腔調字元。例如，'a' 不等於 'ấ')。</span><span class="sxs-lookup"><span data-stu-id="aef92-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-193">會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。</span><span class="sxs-lookup"><span data-stu-id="aef92-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="aef92-194">有關詳細資訊，請參閱[輸入字元集](input-character-set-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="aef92-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="aef92-195">Entity SQL 中無法使用 Transact-SQL 功能</span><span class="sxs-lookup"><span data-stu-id="aef92-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="aef92-196">以下 Transact-SQL 功能在 中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不可用。</span><span class="sxs-lookup"><span data-stu-id="aef92-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="aef92-197">DML</span><span class="sxs-lookup"><span data-stu-id="aef92-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-198">目前不支援 DML 語句（插入、更新、刪除）。</span><span class="sxs-lookup"><span data-stu-id="aef92-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="aef92-199">DDL</span><span class="sxs-lookup"><span data-stu-id="aef92-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-200">不提供目前版本中的任何 DDL 支援。</span><span class="sxs-lookup"><span data-stu-id="aef92-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="aef92-201">命令式程式設計</span><span class="sxs-lookup"><span data-stu-id="aef92-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-202">與 Transact-SQL 不同，不提供命令式程式設計的支援。</span><span class="sxs-lookup"><span data-stu-id="aef92-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="aef92-203">請改用程式語言。</span><span class="sxs-lookup"><span data-stu-id="aef92-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="aef92-204">群組函式</span><span class="sxs-lookup"><span data-stu-id="aef92-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-205">尚未提供群組函式 (如 CUBE、ROLLUP 和 GROUPING_SET) 的支援。</span><span class="sxs-lookup"><span data-stu-id="aef92-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="aef92-206">分析函式</span><span class="sxs-lookup"><span data-stu-id="aef92-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-207">尚未提供分析函式的支援。</span><span class="sxs-lookup"><span data-stu-id="aef92-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="aef92-208">內建函式，運算子</span><span class="sxs-lookup"><span data-stu-id="aef92-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-209">支援 Transact-SQL 內建函數和運算子的子集。</span><span class="sxs-lookup"><span data-stu-id="aef92-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="aef92-210">主要存放區提供者可能會支援這些運算子和函式。</span><span class="sxs-lookup"><span data-stu-id="aef92-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="aef92-211">使用提供程式清單中聲明的特定于存儲的函數。</span><span class="sxs-lookup"><span data-stu-id="aef92-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="aef92-212">此外，實體框架允許您聲明要使用的內置和使用者定義的現有存儲函數[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aef92-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="aef92-213">提示</span><span class="sxs-lookup"><span data-stu-id="aef92-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-214">不提供查詢提示的機制。</span><span class="sxs-lookup"><span data-stu-id="aef92-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="aef92-215">批次處理查詢結果</span><span class="sxs-lookup"><span data-stu-id="aef92-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-216">不支援批次處理查詢結果。</span><span class="sxs-lookup"><span data-stu-id="aef92-216">does not support batching query results.</span></span> <span data-ttu-id="aef92-217">例如，以下是有效的 Transact-SQL（作為批次處理發送）：</span><span class="sxs-lookup"><span data-stu-id="aef92-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="aef92-218">但是，同等的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 未受到支援：</span><span class="sxs-lookup"><span data-stu-id="aef92-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aef92-219">在每個命令中只支援一個產生結果的查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="aef92-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef92-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aef92-220">See also</span></span>

- [<span data-ttu-id="aef92-221">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="aef92-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="aef92-222">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="aef92-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
