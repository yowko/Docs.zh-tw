---
title: 彙總函式 (適用於 Entity Framework 的 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150645"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="5eae0-102">彙總函式 (適用於 Entity Framework 的 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="5eae0-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="5eae0-103">.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。</span><span class="sxs-lookup"><span data-stu-id="5eae0-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="5eae0-104">彙總函式會對一組輸入值執行計算，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="5eae0-105">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="5eae0-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="5eae0-106">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="5eae0-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="5eae0-107">以下是 SqlClient 彙總函式。</span><span class="sxs-lookup"><span data-stu-id="5eae0-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="5eae0-108">AVG（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-108">AVG(expression)</span></span>

<span data-ttu-id="5eae0-109">傳回集合中各個值的平均值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="5eae0-110">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-110">Null values are ignored.</span></span>

<span data-ttu-id="5eae0-111">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-111">**Arguments**</span></span>

<span data-ttu-id="5eae0-112">`Int32`、、`Int64``Double`和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="5eae0-113">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-113">**Return Value**</span></span>

<span data-ttu-id="5eae0-114">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="5eae0-114">The type of `expression`.</span></span>

<span data-ttu-id="5eae0-115">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="5eae0-116">CHECKSUM_AGG（收藏）</span><span class="sxs-lookup"><span data-stu-id="5eae0-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="5eae0-117">傳回集合中值的總和檢查碼 (Checksum)。</span><span class="sxs-lookup"><span data-stu-id="5eae0-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="5eae0-118">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-118">Null values are ignored.</span></span>

 <span data-ttu-id="5eae0-119">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-119">**Arguments**</span></span>

 <span data-ttu-id="5eae0-120">集合（`Int32`</span><span class="sxs-lookup"><span data-stu-id="5eae0-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="5eae0-121">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-121">**Return Value**</span></span>

 <span data-ttu-id="5eae0-122">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-122">An `Int32`.</span></span>

 <span data-ttu-id="5eae0-123">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="5eae0-124">COUNT（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-124">COUNT(expression)</span></span>

<span data-ttu-id="5eae0-125">以 `Int32` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="5eae0-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="5eae0-126">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-126">**Arguments**</span></span>

<span data-ttu-id="5eae0-127">集合\<T>，其中 T 是以下類型之一：</span><span class="sxs-lookup"><span data-stu-id="5eae0-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="5eae0-128">`Guid`（未在 SQL Server 2000 中返回）</span><span class="sxs-lookup"><span data-stu-id="5eae0-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="5eae0-129">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-129">**Return Value**</span></span>

<span data-ttu-id="5eae0-130">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-130">An `Int32`.</span></span>

<span data-ttu-id="5eae0-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="5eae0-132">COUNT_BIG（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="5eae0-133">以 `bigint` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="5eae0-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="5eae0-134">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-134">**Arguments**</span></span>

 <span data-ttu-id="5eae0-135">集合 （T），其中 T 是以下類型之一：</span><span class="sxs-lookup"><span data-stu-id="5eae0-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="5eae0-136">`Guid`（未在 SQL Server 2000 中返回）</span><span class="sxs-lookup"><span data-stu-id="5eae0-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="5eae0-137">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-137">**Return Value**</span></span>

<span data-ttu-id="5eae0-138">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-138">An `Int64`.</span></span>

<span data-ttu-id="5eae0-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="5eae0-140">最大（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-140">MAX(expression)</span></span>

<span data-ttu-id="5eae0-141">傳回集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="5eae0-142">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-142">**Arguments**</span></span>

<span data-ttu-id="5eae0-143">集合 （T），其中 T 是以下類型之一：</span><span class="sxs-lookup"><span data-stu-id="5eae0-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="5eae0-144">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-144">**Return Value**</span></span>

<span data-ttu-id="5eae0-145">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="5eae0-145">The type of `expression`.</span></span>

<span data-ttu-id="5eae0-146">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="5eae0-147">MIN（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-147">MIN(expression)</span></span>

<span data-ttu-id="5eae0-148">傳回集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="5eae0-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="5eae0-149">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-149">**Arguments**</span></span>

<span data-ttu-id="5eae0-150">集合 （T），其中 T 是以下類型之一：</span><span class="sxs-lookup"><span data-stu-id="5eae0-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="5eae0-151">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-151">**Return Value**</span></span>

<span data-ttu-id="5eae0-152">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="5eae0-152">The type of `expression`.</span></span>

<span data-ttu-id="5eae0-153">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="5eae0-154">STDEV（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-154">STDEV(expression)</span></span>

<span data-ttu-id="5eae0-155">傳回指定運算式中之所有值的統計標準差。</span><span class="sxs-lookup"><span data-stu-id="5eae0-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="5eae0-156">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-156">**Arguments**</span></span>

<span data-ttu-id="5eae0-157">集合（`Double`</span><span class="sxs-lookup"><span data-stu-id="5eae0-157">A Collection(`Double`).</span></span>

<span data-ttu-id="5eae0-158">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-158">**Return Value**</span></span>

<span data-ttu-id="5eae0-159">`Double`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-159">A `Double`.</span></span>

<span data-ttu-id="5eae0-160">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="5eae0-161">STDEVP（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-161">STDEVP(expression)</span></span>

<span data-ttu-id="5eae0-162">傳回指定運算式中之所有值的母體統計標準差。</span><span class="sxs-lookup"><span data-stu-id="5eae0-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="5eae0-163">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-163">**Arguments**</span></span>

<span data-ttu-id="5eae0-164">集合（`Double`</span><span class="sxs-lookup"><span data-stu-id="5eae0-164">A Collection(`Double`).</span></span>

<span data-ttu-id="5eae0-165">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-165">**Return Value**</span></span>

<span data-ttu-id="5eae0-166">`Double`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-166">A `Double`.</span></span>

<span data-ttu-id="5eae0-167">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="5eae0-168">SUM（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-168">SUM(expression)</span></span>

<span data-ttu-id="5eae0-169">傳回集合中所有值的總和。</span><span class="sxs-lookup"><span data-stu-id="5eae0-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="5eae0-170">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-170">**Arguments**</span></span>

<span data-ttu-id="5eae0-171">其中 T 是以下類型之一的集合`Int32`（T）： `Int64`、 `Double`、 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5eae0-172">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-172">**Return Value**</span></span>

<span data-ttu-id="5eae0-173">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="5eae0-173">The type of `expression`.</span></span>

<span data-ttu-id="5eae0-174">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="5eae0-175">VAR（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-175">VAR(expression)</span></span>

<span data-ttu-id="5eae0-176">傳回指定運算式中之所有值的統計變異數。</span><span class="sxs-lookup"><span data-stu-id="5eae0-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="5eae0-177">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-177">**Arguments**</span></span>

<span data-ttu-id="5eae0-178">集合（`Double`</span><span class="sxs-lookup"><span data-stu-id="5eae0-178">A Collection(`Double`).</span></span>

<span data-ttu-id="5eae0-179">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-179">**Return Value**</span></span>

<span data-ttu-id="5eae0-180">`Double`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-180">A `Double`.</span></span>

<span data-ttu-id="5eae0-181">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="5eae0-182">VARP（運算式）</span><span class="sxs-lookup"><span data-stu-id="5eae0-182">VARP(expression)</span></span>

<span data-ttu-id="5eae0-183">傳回指定運算式中之所有值的母體擴展的統計變異數。</span><span class="sxs-lookup"><span data-stu-id="5eae0-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="5eae0-184">**參數**</span><span class="sxs-lookup"><span data-stu-id="5eae0-184">**Arguments**</span></span>

<span data-ttu-id="5eae0-185">集合（`Double`</span><span class="sxs-lookup"><span data-stu-id="5eae0-185">A Collection(`Double`).</span></span>

<span data-ttu-id="5eae0-186">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="5eae0-186">**Return Value**</span></span>

<span data-ttu-id="5eae0-187">`Double`。</span><span class="sxs-lookup"><span data-stu-id="5eae0-187">A `Double`.</span></span>

<span data-ttu-id="5eae0-188">**範例**</span><span class="sxs-lookup"><span data-stu-id="5eae0-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="5eae0-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eae0-189">See also</span></span>

- [<span data-ttu-id="5eae0-190">彙總函式 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5eae0-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="5eae0-191">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="5eae0-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="5eae0-192">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="5eae0-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
