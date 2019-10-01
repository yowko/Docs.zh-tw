---
title: 彙總函式 (適用於 Entity Framework 的 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700049"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="c6846-102">彙總函式 (適用於 Entity Framework 的 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="c6846-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="c6846-103">.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。</span><span class="sxs-lookup"><span data-stu-id="c6846-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="c6846-104">彙總函式會對一組輸入值執行計算，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="c6846-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="c6846-105">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="c6846-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="c6846-106">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="c6846-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="c6846-107">以下是 SqlClient 彙總函式。</span><span class="sxs-lookup"><span data-stu-id="c6846-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="c6846-108">AVG （expression）</span><span class="sxs-lookup"><span data-stu-id="c6846-108">AVG(expression)</span></span>

<span data-ttu-id="c6846-109">傳回集合中各個值的平均值。</span><span class="sxs-lookup"><span data-stu-id="c6846-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="c6846-110">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c6846-110">Null values are ignored.</span></span>

<span data-ttu-id="c6846-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-111">**Arguments**</span></span>

<span data-ttu-id="c6846-112">@No__t-0、`Int64`、`Double` 和 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="c6846-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="c6846-113">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-113">**Return Value**</span></span>

<span data-ttu-id="c6846-114">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="c6846-114">The type of `expression`.</span></span>

<span data-ttu-id="c6846-115">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="c6846-116">CHECKSUM_AGG （集合）</span><span class="sxs-lookup"><span data-stu-id="c6846-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="c6846-117">傳回集合中值的總和檢查碼 (Checksum)。</span><span class="sxs-lookup"><span data-stu-id="c6846-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="c6846-118">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c6846-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="c6846-119">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-119">**Arguments**</span></span>
 
 <span data-ttu-id="c6846-120">集合（`Int32`）。</span><span class="sxs-lookup"><span data-stu-id="c6846-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="c6846-121">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-121">**Return Value**</span></span>
 
 <span data-ttu-id="c6846-122">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="c6846-122">An `Int32`.</span></span>
 
 <span data-ttu-id="c6846-123">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-123">**Example**</span></span>
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="c6846-124">計數（運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-124">COUNT(expression)</span></span>

<span data-ttu-id="c6846-125">以 `Int32` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c6846-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="c6846-126">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-126">**Arguments**</span></span>

<span data-ttu-id="c6846-127">集合 @ no__t-0T >，其中 T 是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="c6846-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="c6846-128">`Guid` （SQL Server 2000 中未傳回）</span><span class="sxs-lookup"><span data-stu-id="c6846-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="c6846-129">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-129">**Return Value**</span></span>

<span data-ttu-id="c6846-130">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="c6846-130">An `Int32`.</span></span>

<span data-ttu-id="c6846-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a><span data-ttu-id="c6846-132">COUNT_BIG （運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-132">COUNT_BIG(expression)</span></span>
 
<span data-ttu-id="c6846-133">以 `bigint` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c6846-133">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="c6846-134">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-134">**Arguments**</span></span>
 
 <span data-ttu-id="c6846-135">集合（T），其中 T 是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="c6846-135">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="c6846-136">`Guid` （SQL Server 2000 中未傳回）</span><span class="sxs-lookup"><span data-stu-id="c6846-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="c6846-137">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-137">**Return Value**</span></span>

<span data-ttu-id="c6846-138">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="c6846-138">An `Int64`.</span></span>

<span data-ttu-id="c6846-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="c6846-140">最大值（運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-140">MAX(expression)</span></span>

<span data-ttu-id="c6846-141">傳回集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="c6846-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="c6846-142">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-142">**Arguments**</span></span>

<span data-ttu-id="c6846-143">集合（T），其中 T 是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="c6846-143">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="c6846-144">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-144">**Return Value**</span></span>

<span data-ttu-id="c6846-145">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="c6846-145">The type of `expression`.</span></span>

<span data-ttu-id="c6846-146">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="c6846-147">最小值（運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-147">MIN(expression)</span></span>

<span data-ttu-id="c6846-148">傳回集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="c6846-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="c6846-149">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-149">**Arguments**</span></span>

<span data-ttu-id="c6846-150">集合（T），其中 T 是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="c6846-150">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="c6846-151">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-151">**Return Value**</span></span>

<span data-ttu-id="c6846-152">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="c6846-152">The type of `expression`.</span></span>

<span data-ttu-id="c6846-153">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="c6846-154">STDEV （運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-154">STDEV(expression)</span></span>

<span data-ttu-id="c6846-155">傳回指定運算式中之所有值的統計標準差。</span><span class="sxs-lookup"><span data-stu-id="c6846-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="c6846-156">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-156">**Arguments**</span></span>

<span data-ttu-id="c6846-157">集合（`Double`）。</span><span class="sxs-lookup"><span data-stu-id="c6846-157">A Collection(`Double`).</span></span>

<span data-ttu-id="c6846-158">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-158">**Return Value**</span></span>

<span data-ttu-id="c6846-159">`Double`。</span><span class="sxs-lookup"><span data-stu-id="c6846-159">A `Double`.</span></span>

<span data-ttu-id="c6846-160">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="c6846-161">STDEVP （運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-161">STDEVP(expression)</span></span>

<span data-ttu-id="c6846-162">傳回指定運算式中所有值的母體擴展統計標準差。</span><span class="sxs-lookup"><span data-stu-id="c6846-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="c6846-163">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-163">**Arguments**</span></span>

<span data-ttu-id="c6846-164">集合（`Double`）。</span><span class="sxs-lookup"><span data-stu-id="c6846-164">A Collection(`Double`).</span></span>

<span data-ttu-id="c6846-165">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-165">**Return Value**</span></span>

<span data-ttu-id="c6846-166">`Double`。</span><span class="sxs-lookup"><span data-stu-id="c6846-166">A `Double`.</span></span>

<span data-ttu-id="c6846-167">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="c6846-168">SUM （expression）</span><span class="sxs-lookup"><span data-stu-id="c6846-168">SUM(expression)</span></span>

<span data-ttu-id="c6846-169">傳回集合中所有值的總和。</span><span class="sxs-lookup"><span data-stu-id="c6846-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="c6846-170">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-170">**Arguments**</span></span>

<span data-ttu-id="c6846-171">集合（T），其中 T 是下列其中一個類型： `Int32`，`Int64`，`Double`，`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="c6846-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="c6846-172">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-172">**Return Value**</span></span>

<span data-ttu-id="c6846-173">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="c6846-173">The type of `expression`.</span></span>

<span data-ttu-id="c6846-174">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="c6846-175">VAR （expression）</span><span class="sxs-lookup"><span data-stu-id="c6846-175">VAR(expression)</span></span>

<span data-ttu-id="c6846-176">傳回指定運算式中之所有值的統計變異數。</span><span class="sxs-lookup"><span data-stu-id="c6846-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="c6846-177">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-177">**Arguments**</span></span>

<span data-ttu-id="c6846-178">集合（`Double`）。</span><span class="sxs-lookup"><span data-stu-id="c6846-178">A Collection(`Double`).</span></span>

<span data-ttu-id="c6846-179">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-179">**Return Value**</span></span>

<span data-ttu-id="c6846-180">`Double`。</span><span class="sxs-lookup"><span data-stu-id="c6846-180">A `Double`.</span></span>

<span data-ttu-id="c6846-181">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="c6846-182">VARP （運算式）</span><span class="sxs-lookup"><span data-stu-id="c6846-182">VARP(expression)</span></span>

<span data-ttu-id="c6846-183">傳回指定之運算式中所有值的母體擴展統計變異數。</span><span class="sxs-lookup"><span data-stu-id="c6846-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="c6846-184">**引數**</span><span class="sxs-lookup"><span data-stu-id="c6846-184">**Arguments**</span></span>

<span data-ttu-id="c6846-185">集合（`Double`）。</span><span class="sxs-lookup"><span data-stu-id="c6846-185">A Collection(`Double`).</span></span>

<span data-ttu-id="c6846-186">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="c6846-186">**Return Value**</span></span>

<span data-ttu-id="c6846-187">`Double`。</span><span class="sxs-lookup"><span data-stu-id="c6846-187">A `Double`.</span></span>

<span data-ttu-id="c6846-188">**範例**</span><span class="sxs-lookup"><span data-stu-id="c6846-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="c6846-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6846-189">See also</span></span>

- [<span data-ttu-id="c6846-190">彙總函式 (transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c6846-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="c6846-191">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="c6846-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="c6846-192">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="c6846-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
