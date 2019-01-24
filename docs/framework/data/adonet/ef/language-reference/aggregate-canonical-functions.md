---
title: 彙總標準函式
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f65557703070a43f586a668903d049a374ef70d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708970"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="29311-102">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="29311-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="29311-103">彙總 (Aggregate) 是指將一連串輸入值縮減成單一值的運算式。</span><span class="sxs-lookup"><span data-stu-id="29311-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="29311-104">彙總通常會與 SELECT 運算式的 GROUP BY 子句搭配使用，而且它們的使用位置具有一些條件約束 (Constraint)。</span><span class="sxs-lookup"><span data-stu-id="29311-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggegate-entity-sql-canonical-functions"></a><span data-ttu-id="29311-105">Aggegate Entity SQL 標準函式</span><span class="sxs-lookup"><span data-stu-id="29311-105">Aggegate Entity SQL canonical functions</span></span>

<span data-ttu-id="29311-106">以下是彙總的 Entity SQL 標準函式。</span><span class="sxs-lookup"><span data-stu-id="29311-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="29311-107">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-107">Avg(expression)</span></span>

<span data-ttu-id="29311-108">傳回非 null 值的平均。</span><span class="sxs-lookup"><span data-stu-id="29311-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="29311-109">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-109">**Arguments**</span></span>

<span data-ttu-id="29311-110">`Int32`， `Int64`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="29311-111">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-111">**Return Value**</span></span>

<span data-ttu-id="29311-112">型別`expression`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-113">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="29311-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-114">BigCount(expression)</span></span>

<span data-ttu-id="29311-115">傳回包含 null 和重複值的彙總大小。</span><span class="sxs-lookup"><span data-stu-id="29311-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="29311-116">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-116">**Arguments**</span></span>

<span data-ttu-id="29311-117">任何型別。</span><span class="sxs-lookup"><span data-stu-id="29311-117">Any type.</span></span>

<span data-ttu-id="29311-118">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-118">**Return Value**</span></span>

<span data-ttu-id="29311-119">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="29311-119">An `Int64`.</span></span>

<span data-ttu-id="29311-120">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="29311-121">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-121">Count(expression)</span></span> 

<span data-ttu-id="29311-122">傳回包含 null 和重複值的彙總大小。</span><span class="sxs-lookup"><span data-stu-id="29311-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="29311-123">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-123">**Arguments**</span></span>

<span data-ttu-id="29311-124">任何型別。</span><span class="sxs-lookup"><span data-stu-id="29311-124">Any type.</span></span>

<span data-ttu-id="29311-125">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-125">**Return Value**</span></span>

<span data-ttu-id="29311-126">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="29311-126">An `Int32`.</span></span>

<span data-ttu-id="29311-127">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="29311-128">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-128">Max(expression)</span></span>

<span data-ttu-id="29311-129">傳回非 null 值的最大值。</span><span class="sxs-lookup"><span data-stu-id="29311-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="29311-130">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-130">**Arguments**</span></span>

<span data-ttu-id="29311-131">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="29311-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="29311-132">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-132">**Return Value**</span></span>

<span data-ttu-id="29311-133">型別`expression`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-134">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="29311-135">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-135">Min(expression)</span></span>

<span data-ttu-id="29311-136">傳回非 null 值的最小值。</span><span class="sxs-lookup"><span data-stu-id="29311-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="29311-137">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-137">**Arguments**</span></span>

<span data-ttu-id="29311-138">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="29311-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="29311-139">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-139">**Return Value**</span></span>

<span data-ttu-id="29311-140">型別`expression`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-141">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="29311-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-142">StDev(expression)</span></span>

<span data-ttu-id="29311-143">傳回非 Null 值的標準差。</span><span class="sxs-lookup"><span data-stu-id="29311-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="29311-144">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-144">**Arguments**</span></span>

<span data-ttu-id="29311-145">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="29311-146">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-146">**Return Value**</span></span>

<span data-ttu-id="29311-147">`Double`。</span><span class="sxs-lookup"><span data-stu-id="29311-147">A `Double`.</span></span> <span data-ttu-id="29311-148">如果所有輸入值是 `Null` 值，則為 `null`。</span><span class="sxs-lookup"><span data-stu-id="29311-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="29311-149">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="29311-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-150">StDevP(expression)</span></span>

<span data-ttu-id="29311-151">傳回所有值的母體擴展標準差。</span><span class="sxs-lookup"><span data-stu-id="29311-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="29311-152">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-152">**Arguments**</span></span>

<span data-ttu-id="29311-153">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="29311-154">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-154">**Return Value**</span></span>

<span data-ttu-id="29311-155">A `Double`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-156">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="29311-157">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-157">Sum(expression)</span></span>

<span data-ttu-id="29311-158">傳回非 null 值的總和。</span><span class="sxs-lookup"><span data-stu-id="29311-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="29311-159">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-159">**Arguments**</span></span>

<span data-ttu-id="29311-160">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="29311-161">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-161">**Return Value**</span></span>

<span data-ttu-id="29311-162">A `Double`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-163">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="29311-164">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-164">Var(expression)</span></span>

<span data-ttu-id="29311-165">傳回所有非 NULL 值的變異數。</span><span class="sxs-lookup"><span data-stu-id="29311-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="29311-166">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-166">**Arguments**</span></span>

<span data-ttu-id="29311-167">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="29311-168">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-168">**Return Value**</span></span>

<span data-ttu-id="29311-169">A `Double`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-170">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="29311-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="29311-171">VarP(expression)</span></span>

<span data-ttu-id="29311-172">傳回所有非 NULL 值的母體變異數。</span><span class="sxs-lookup"><span data-stu-id="29311-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="29311-173">**引數**</span><span class="sxs-lookup"><span data-stu-id="29311-173">**Arguments**</span></span>

<span data-ttu-id="29311-174">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="29311-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="29311-175">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="29311-175">**Return Value**</span></span>

<span data-ttu-id="29311-176">A `Double`，或`null`如果所有輸入的值為`null`值。</span><span class="sxs-lookup"><span data-stu-id="29311-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="29311-177">**範例**</span><span class="sxs-lookup"><span data-stu-id="29311-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

<span data-ttu-id="29311-178">Microsoft SQL Client Managed Provider 中提供了對等的功能。</span><span class="sxs-lookup"><span data-stu-id="29311-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="29311-179">如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="29311-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="29311-180">以集合為基礎的彙總</span><span class="sxs-lookup"><span data-stu-id="29311-180">Collection-based aggregates</span></span>

<span data-ttu-id="29311-181">以集合為基礎的彙總 (集合函式) 會針對集合運作並傳回一個值。</span><span class="sxs-lookup"><span data-stu-id="29311-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="29311-182">比方說如果 ORDERS 是所有訂單的集合，您可以計算最早的出貨日期，使用下列運算式：</span><span class="sxs-lookup"><span data-stu-id="29311-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="29311-183">以集合為基礎之彙總內部的運算式是在目前的環境名稱解析範圍內評估。</span><span class="sxs-lookup"><span data-stu-id="29311-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="29311-184">群組為基礎的彙總</span><span class="sxs-lookup"><span data-stu-id="29311-184">Group-based aggregates</span></span>

<span data-ttu-id="29311-185">以群組為基礎的彙總會計算 GROUP BY 子句所定義的整個群組。</span><span class="sxs-lookup"><span data-stu-id="29311-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="29311-186">系統會針對結果中的每個群組，使用每個群組中的項目當做彙總計算的輸入來計算個別的彙總。</span><span class="sxs-lookup"><span data-stu-id="29311-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="29311-187">當 group-by 子句用於 select 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影或 order-by 子句中。</span><span class="sxs-lookup"><span data-stu-id="29311-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="29311-188">下列範例會計算針對每個產品訂購的平均數量：</span><span class="sxs-lookup"><span data-stu-id="29311-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

<span data-ttu-id="29311-189">可以在 SELECT 運算式中以群組為基礎的彙總，而不需要明確 group-by 子句。</span><span class="sxs-lookup"><span data-stu-id="29311-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="29311-190">在此情況下，所有項目會視為單一群組。</span><span class="sxs-lookup"><span data-stu-id="29311-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="29311-191">這是指定群組，根據常數的對等項目。</span><span class="sxs-lookup"><span data-stu-id="29311-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="29311-192">以下列運算式為例：</span><span class="sxs-lookup"><span data-stu-id="29311-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="29311-193">這個運算式就相當於下列運算式：</span><span class="sxs-lookup"><span data-stu-id="29311-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="29311-194">以群組為基礎之彙總內部的運算式是在 WHERE 子句運算式可見的名稱解析範圍內評估。</span><span class="sxs-lookup"><span data-stu-id="29311-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="29311-195">依照[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]，群組為基礎的彙總也可以指定 ALL 或 DISTINCT 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="29311-195">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="29311-196">如果有指定 DISTINCT 修飾詞，系統就會在計算彙總之前，從彙總輸入集合中刪除重複項目。</span><span class="sxs-lookup"><span data-stu-id="29311-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="29311-197">如果指定的是 ALL 修飾詞 (或沒有指定任何修飾詞)，就不會執行重複項目刪除作業。</span><span class="sxs-lookup"><span data-stu-id="29311-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>  

## <a name="see-also"></a><span data-ttu-id="29311-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29311-198">See also</span></span>

- [<span data-ttu-id="29311-199">標準函式</span><span class="sxs-lookup"><span data-stu-id="29311-199">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
