---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 75ce0b00962526b76ea9f4b9fdfb0d1e1e564cdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774741"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="8c745-102">Entity SQL 與 Transact-SQL 的相異之處</span><span class="sxs-lookup"><span data-stu-id="8c745-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="8c745-103">本主題描述之間的差異[!INCLUDE[esql](../../../../../../includes/esql-md.md)]和[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c745-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="8c745-104">繼承和關聯性支援</span><span class="sxs-lookup"><span data-stu-id="8c745-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-105">可直接配合概念實體結構描述運作，並支援概念模型功能，例如繼承和關聯性。</span><span class="sxs-lookup"><span data-stu-id="8c745-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="8c745-106">當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。</span><span class="sxs-lookup"><span data-stu-id="8c745-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="8c745-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)中的運算子[!INCLUDE[esql](../../../../../../includes/esql-md.md)](類似於`oftype`在C#序列) 提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="8c745-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="8c745-108">集合的支援</span><span class="sxs-lookup"><span data-stu-id="8c745-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-109">您可以將集合視為第一級實體。</span><span class="sxs-lookup"><span data-stu-id="8c745-109">treats collections as first-class entities.</span></span> <span data-ttu-id="8c745-110">例如: </span><span class="sxs-lookup"><span data-stu-id="8c745-110">For example:</span></span>  
  
- <span data-ttu-id="8c745-111">集合運算式在 `from` 子句中是有效的。</span><span class="sxs-lookup"><span data-stu-id="8c745-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="8c745-112">`in` 和 `exists` 子查詢已通用化，可允許任何集合。</span><span class="sxs-lookup"><span data-stu-id="8c745-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="8c745-113">子查詢是一種集合。</span><span class="sxs-lookup"><span data-stu-id="8c745-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="8c745-114">`e1 in e2` 和 `exists(e)` 是用來執行這些作業的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 建構。</span><span class="sxs-lookup"><span data-stu-id="8c745-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="8c745-115">Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。</span><span class="sxs-lookup"><span data-stu-id="8c745-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="8c745-116">聯結可針對集合操作。</span><span class="sxs-lookup"><span data-stu-id="8c745-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="8c745-117">運算式的支援</span><span class="sxs-lookup"><span data-stu-id="8c745-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-118">具有子查詢 （資料表） 和運算式 （資料列和資料行）。</span><span class="sxs-lookup"><span data-stu-id="8c745-118">has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="8c745-119">為了支援集合和巢狀的集合，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]將所有東西變成運算式。</span><span class="sxs-lookup"><span data-stu-id="8c745-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> <span data-ttu-id="8c745-120">與 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 相比，[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 更容易撰寫 - 每一個運算式都可在任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="8c745-120">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="8c745-121">查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="8c745-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="8c745-122">如需[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]中不支援的運算式[!INCLUDE[esql](../../../../../../includes/esql-md.md)]，請參閱[不支援的運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8c745-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="8c745-123">下列全都是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢：</span><span class="sxs-lookup"><span data-stu-id="8c745-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="8c745-124">子查詢的統一處理</span><span class="sxs-lookup"><span data-stu-id="8c745-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="8c745-125">在資料表上，強調[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]執行子查詢的內容解譯。</span><span class="sxs-lookup"><span data-stu-id="8c745-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="8c745-126">例如，在子查詢`from`子句數字會被視為多重集 （資料表）。</span><span class="sxs-lookup"><span data-stu-id="8c745-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="8c745-127">但是 `select` 子句中使用的相同子查詢會視為純量子查詢。</span><span class="sxs-lookup"><span data-stu-id="8c745-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="8c745-128">同樣地，使用左邊的子查詢`in`運算子會被視為純量子查詢，而右側必須是多重集子的查詢。</span><span class="sxs-lookup"><span data-stu-id="8c745-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-129">會消除這些差異。</span><span class="sxs-lookup"><span data-stu-id="8c745-129">eliminates these differences.</span></span> <span data-ttu-id="8c745-130">運算式的統一解譯不依賴使用此運算式的內容。</span><span class="sxs-lookup"><span data-stu-id="8c745-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-131">會考量所有的子查詢視為多重集子的查詢。</span><span class="sxs-lookup"><span data-stu-id="8c745-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="8c745-132">如果子查詢，從想要的純量值[!INCLUDE[esql](../../../../../../includes/esql-md.md)]提供`anyelement`作業集合 （在此情況下，子查詢），而且從集合中擷取單一值的運算子。</span><span class="sxs-lookup"><span data-stu-id="8c745-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="8c745-133">避免子查詢的隱含強制型轉</span><span class="sxs-lookup"><span data-stu-id="8c745-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="8c745-134">統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。</span><span class="sxs-lookup"><span data-stu-id="8c745-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="8c745-135">明確地說，[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中的資料列多重集 (具有單一欄位) 會隱含地轉換成一個純量值，這個值的資料型別是此欄位的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8c745-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-136">不支援這種隱含強制型轉。</span><span class="sxs-lookup"><span data-stu-id="8c745-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-137">提供了可從集合中擷取單一值的 ANYELEMENT 運算子，以及一個可在查詢運算式期間避免建立資料列包裝函式的 `select value` 子句。</span><span class="sxs-lookup"><span data-stu-id="8c745-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="8c745-138">選取值：避免隱含資料列包裝函式</span><span class="sxs-lookup"><span data-stu-id="8c745-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="8c745-139">Select 子句中的[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]子查詢子句中隱含建立的項目周圍的資料列包裝函式。</span><span class="sxs-lookup"><span data-stu-id="8c745-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="8c745-140">這意味我們無法建立純量或物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8c745-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-141">可讓具有一個欄位的資料列型別與相同的資料類型的單一值之間的隱含強制型轉。</span><span class="sxs-lookup"><span data-stu-id="8c745-141">allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-142">提供 `select value` 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="8c745-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="8c745-143">`select value` 子句中只能指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="8c745-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="8c745-144">使用這類子句時，將不會建構包含 `select` 子句中這個項目的資料列包裝函式，並且可以產生所需形狀的集合，例如：`select value a`。</span><span class="sxs-lookup"><span data-stu-id="8c745-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-145">也提供資料列建構函式來建構任意資料列。</span><span class="sxs-lookup"><span data-stu-id="8c745-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="8c745-146">`select` 會擷取投影中的一個或多個項目，並產生具有欄位的資料記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c745-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="8c745-147">左邊相互關聯與別名</span><span class="sxs-lookup"><span data-stu-id="8c745-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="8c745-148">在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中，給定範圍中的運算式 (類似 `select` 或 `from` 的單一子句) 無法參考之前在相同範圍中所定義的運算式。</span><span class="sxs-lookup"><span data-stu-id="8c745-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="8c745-149">SQL 的某些 Dialect (包括 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) 確實支援 `from` 子句中受限形式的這些運算式。</span><span class="sxs-lookup"><span data-stu-id="8c745-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-150">在左邊相互關聯通用化`from`子句，並將它們視為一致的方式。</span><span class="sxs-lookup"><span data-stu-id="8c745-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="8c745-151">`from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。</span><span class="sxs-lookup"><span data-stu-id="8c745-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-152">也會針對與 `group by` 子句有關的查詢做出其他限制。</span><span class="sxs-lookup"><span data-stu-id="8c745-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="8c745-153">中的運算式`select`子句和`having`這類查詢子句只能參考`group by`透過其別名的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8c745-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="8c745-154">下列建構中是有效[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]但不是處於[!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8c745-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="8c745-155">若要在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中進行這項處理：</span><span class="sxs-lookup"><span data-stu-id="8c745-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="8c745-156">參考資料表 (集合) 的資料行 (屬性)</span><span class="sxs-lookup"><span data-stu-id="8c745-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="8c745-157">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的所有資料行參考都必須以資料表別名來限定。</span><span class="sxs-lookup"><span data-stu-id="8c745-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="8c745-158">下列建構 (假設`a`是有效的資料行的資料表`T`) 中是有效[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]但無法顯示於[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c745-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="8c745-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 格式如下：</span><span class="sxs-lookup"><span data-stu-id="8c745-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="8c745-160">資料表別名在 `from` 子句中為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8c745-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="8c745-161">資料表名稱會當做隱含別名使用。</span><span class="sxs-lookup"><span data-stu-id="8c745-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-162">也會顯示下列格式：</span><span class="sxs-lookup"><span data-stu-id="8c745-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="8c745-163">導覽物件</span><span class="sxs-lookup"><span data-stu-id="8c745-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-164">會使用標記法來參考資料表 (之資料列) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="8c745-164">uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-165">會擴充這個標記法 (從程式語言借用) 來支援物件之屬性的導覽。</span><span class="sxs-lookup"><span data-stu-id="8c745-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="8c745-166">例如，如果 `p` 是 Person 型別的運算式，下列是用來參考這個人之地址所在城市的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法。</span><span class="sxs-lookup"><span data-stu-id="8c745-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="8c745-167">\* 表示不支援</span><span class="sxs-lookup"><span data-stu-id="8c745-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-168">支援使用資格不符 \* 語法當做整個資料列中，和完整的別名\*語法 (t.\*) 的捷徑，該資料表的欄位。</span><span class="sxs-lookup"><span data-stu-id="8c745-168">supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="8c745-169">颾魤 ㄛ[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]允許特殊 count (\*) 彙總，其中包含 null。</span><span class="sxs-lookup"><span data-stu-id="8c745-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-170">不支援 \* 建構。</span><span class="sxs-lookup"><span data-stu-id="8c745-170">does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-171">和 `select * from T` 格式的 `select T1.* from T1, T2...` 查詢可以分別在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中表示為 `select value t from T as t` 和 `select value t1 from T1 as t1, T2 as t2...`。</span><span class="sxs-lookup"><span data-stu-id="8c745-171">queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="8c745-172">此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。</span><span class="sxs-lookup"><span data-stu-id="8c745-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-173">不支援 `count(*)` 彙總，</span><span class="sxs-lookup"><span data-stu-id="8c745-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="8c745-174">請改用 `count(0)`。</span><span class="sxs-lookup"><span data-stu-id="8c745-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="8c745-175">變更成 Group By</span><span class="sxs-lookup"><span data-stu-id="8c745-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-176">支援 `group by` 索引鍵的別名。</span><span class="sxs-lookup"><span data-stu-id="8c745-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="8c745-177">中的運算式`select`子句和`having`子句必須參考`group by`透過這些別名的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8c745-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="8c745-178">例如，這個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法：</span><span class="sxs-lookup"><span data-stu-id="8c745-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="8c745-179">...等於下列 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="8c745-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="8c745-180">以集合為基礎的彙總</span><span class="sxs-lookup"><span data-stu-id="8c745-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-181">支援兩種彙總。</span><span class="sxs-lookup"><span data-stu-id="8c745-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="8c745-182">以集合為基礎的彙總會針對集合運作，並產生彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="8c745-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="8c745-183">這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。</span><span class="sxs-lookup"><span data-stu-id="8c745-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="8c745-184">例如：</span><span class="sxs-lookup"><span data-stu-id="8c745-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-185">也支援 SQL 樣式彙總。</span><span class="sxs-lookup"><span data-stu-id="8c745-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="8c745-186">例如: </span><span class="sxs-lookup"><span data-stu-id="8c745-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="8c745-187">ORDER BY 子句使用方式</span><span class="sxs-lookup"><span data-stu-id="8c745-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="8c745-188">允許只能在最上層 SELECT ..FROM .. WHERE 區塊中指定 ORDER BY</span><span class="sxs-lookup"><span data-stu-id="8c745-188">allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="8c745-189">子句</span><span class="sxs-lookup"><span data-stu-id="8c745-189">FROM ..</span></span> <span data-ttu-id="8c745-190">。</span><span class="sxs-lookup"><span data-stu-id="8c745-190">WHERE block.</span></span> <span data-ttu-id="8c745-191">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，您可以使用巢狀 ORDER BY 運算式，並將它放在查詢內的任何地方，但是巢狀查詢中的排序並不會保留下來。</span><span class="sxs-lookup"><span data-stu-id="8c745-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="8c745-192">識別項</span><span class="sxs-lookup"><span data-stu-id="8c745-192">Identifiers</span></span>  
 <span data-ttu-id="8c745-193">在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中，識別項比較是以目前資料庫的定序 (Collation) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="8c745-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="8c745-194">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，識別項一律不會區分大小寫，但是會區分腔調字 (Accent Sensitive) (亦即，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會區別有腔調和無腔調字元。例如，'a' 不等於 'ấ')。</span><span class="sxs-lookup"><span data-stu-id="8c745-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-195">會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。</span><span class="sxs-lookup"><span data-stu-id="8c745-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="8c745-196">如需詳細資訊，請參閱 <<c0> [ 輸入字元集](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8c745-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="8c745-197">Entity SQL 中無法使用 Transact-SQL 功能</span><span class="sxs-lookup"><span data-stu-id="8c745-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="8c745-198">下列 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 功能無法在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中使用。</span><span class="sxs-lookup"><span data-stu-id="8c745-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="8c745-199">DML</span><span class="sxs-lookup"><span data-stu-id="8c745-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-200">目前不提供支援 DML 陳述式 （插入、 更新及刪除）。</span><span class="sxs-lookup"><span data-stu-id="8c745-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="8c745-201">DDL</span><span class="sxs-lookup"><span data-stu-id="8c745-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-202">不提供目前版本中的任何 DDL 支援。</span><span class="sxs-lookup"><span data-stu-id="8c745-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="8c745-203">命令式程式設計</span><span class="sxs-lookup"><span data-stu-id="8c745-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-204">不提供命令式程式設計的任何支援，與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 不同。</span><span class="sxs-lookup"><span data-stu-id="8c745-204">provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8c745-205">請改用程式語言。</span><span class="sxs-lookup"><span data-stu-id="8c745-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="8c745-206">群組函式</span><span class="sxs-lookup"><span data-stu-id="8c745-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-207">尚未提供群組函式 (如 CUBE、ROLLUP 和 GROUPING_SET) 的支援。</span><span class="sxs-lookup"><span data-stu-id="8c745-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="8c745-208">分析函式</span><span class="sxs-lookup"><span data-stu-id="8c745-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-209">尚未提供分析函式的支援。</span><span class="sxs-lookup"><span data-stu-id="8c745-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="8c745-210">內建函式，運算子</span><span class="sxs-lookup"><span data-stu-id="8c745-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-211">支援的子集[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]之內建函數和運算子。</span><span class="sxs-lookup"><span data-stu-id="8c745-211">supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="8c745-212">主要存放區提供者可能會支援這些運算子和函式。</span><span class="sxs-lookup"><span data-stu-id="8c745-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-213">使用提供者資訊清單中宣告的存放區特有函式。</span><span class="sxs-lookup"><span data-stu-id="8c745-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="8c745-214">此外，[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]可讓您宣告內建和使用者定義的現有存放區函式，如[!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="8c745-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="8c745-215">提示</span><span class="sxs-lookup"><span data-stu-id="8c745-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-216">不提供查詢提示的機制。</span><span class="sxs-lookup"><span data-stu-id="8c745-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="8c745-217">批次處理查詢結果</span><span class="sxs-lookup"><span data-stu-id="8c745-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-218">不支援批次處理查詢結果。</span><span class="sxs-lookup"><span data-stu-id="8c745-218">does not support batching query results.</span></span> <span data-ttu-id="8c745-219">例如，以下是有效[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]（傳送做為批次）：</span><span class="sxs-lookup"><span data-stu-id="8c745-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="8c745-220">但是，同等的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 未受到支援：</span><span class="sxs-lookup"><span data-stu-id="8c745-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8c745-221">在每個命令中只支援一個產生結果的查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c745-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c745-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c745-222">See also</span></span>

- [<span data-ttu-id="8c745-223">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="8c745-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="8c745-224">不支援的運算式</span><span class="sxs-lookup"><span data-stu-id="8c745-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
