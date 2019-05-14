---
title: 彙總函式 (適用於 Entity Framework 的 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: f2f2b557cd9f126ddd513a0f42d3ac95114c3822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606764"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="141ea-102">彙總函式 (適用於 Entity Framework 的 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="141ea-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="141ea-103">.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。</span><span class="sxs-lookup"><span data-stu-id="141ea-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="141ea-104">彙總函式會對一組輸入值執行計算，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="141ea-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="141ea-105">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="141ea-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="141ea-106">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="141ea-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="141ea-107">以下是 SqlClient 彙總函式。</span><span class="sxs-lookup"><span data-stu-id="141ea-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="141ea-108">AVG(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-108">AVG(expression)</span></span>

<span data-ttu-id="141ea-109">傳回集合中各個值的平均值。</span><span class="sxs-lookup"><span data-stu-id="141ea-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="141ea-110">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="141ea-110">Null values are ignored.</span></span>

<span data-ttu-id="141ea-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-111">**Arguments**</span></span>

<span data-ttu-id="141ea-112">`Int32`， `Int64`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="141ea-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="141ea-113">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-113">**Return Value**</span></span>

<span data-ttu-id="141ea-114">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="141ea-114">The type of `expression`.</span></span>

<span data-ttu-id="141ea-115">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="141ea-116">CHECKSUM_AGG(collection)</span><span class="sxs-lookup"><span data-stu-id="141ea-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="141ea-117">傳回集合中值的總和檢查碼 (Checksum)。</span><span class="sxs-lookup"><span data-stu-id="141ea-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="141ea-118">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="141ea-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="141ea-119">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-119">**Arguments**</span></span>
 
 <span data-ttu-id="141ea-120">集合 (`Int32`)。</span><span class="sxs-lookup"><span data-stu-id="141ea-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="141ea-121">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-121">**Return Value**</span></span>
 
 <span data-ttu-id="141ea-122">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="141ea-122">An `Int32`.</span></span>
 
 <span data-ttu-id="141ea-123">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="141ea-124">COUNT(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-124">COUNT(expression)</span></span>

<span data-ttu-id="141ea-125">以 `Int32` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="141ea-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="141ea-126">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-126">**Arguments**</span></span>

<span data-ttu-id="141ea-127">集合\<T >，其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="141ea-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="141ea-128">`Guid` （SQL Server 2000 中不會傳回）</span><span class="sxs-lookup"><span data-stu-id="141ea-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="141ea-129">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-129">**Return Value**</span></span>

<span data-ttu-id="141ea-130">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="141ea-130">An `Int32`.</span></span>

<span data-ttu-id="141ea-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="141ea-132">[！ 的程式碼 sql[DP EntityServices 概念 #SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="141ea-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="141ea-133">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="141ea-134">以 `bigint` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="141ea-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="141ea-135">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-135">**Arguments**</span></span>
 
 <span data-ttu-id="141ea-136">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="141ea-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="141ea-137">`Guid` （SQL Server 2000 中不會傳回）</span><span class="sxs-lookup"><span data-stu-id="141ea-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="141ea-138">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-138">**Return Value**</span></span>

<span data-ttu-id="141ea-139">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="141ea-139">An `Int64`.</span></span>

<span data-ttu-id="141ea-140">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="141ea-141">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-141">MAX(expression)</span></span>

<span data-ttu-id="141ea-142">傳回集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="141ea-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="141ea-143">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-143">**Arguments**</span></span>

<span data-ttu-id="141ea-144">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="141ea-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="141ea-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-145">**Return Value**</span></span>

<span data-ttu-id="141ea-146">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="141ea-146">The type of `expression`.</span></span>

<span data-ttu-id="141ea-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="141ea-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-148">MIN(expression)</span></span>

<span data-ttu-id="141ea-149">傳回集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="141ea-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="141ea-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-150">**Arguments**</span></span>

<span data-ttu-id="141ea-151">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="141ea-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="141ea-152">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-152">**Return Value**</span></span>

<span data-ttu-id="141ea-153">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="141ea-153">The type of `expression`.</span></span>

<span data-ttu-id="141ea-154">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="141ea-155">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-155">STDEV(expression)</span></span>

<span data-ttu-id="141ea-156">傳回指定運算式中之所有值的統計標準差。</span><span class="sxs-lookup"><span data-stu-id="141ea-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="141ea-157">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-157">**Arguments**</span></span>

<span data-ttu-id="141ea-158">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="141ea-158">A Collection(`Double`).</span></span>

<span data-ttu-id="141ea-159">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-159">**Return Value**</span></span>

<span data-ttu-id="141ea-160">`Double`。</span><span class="sxs-lookup"><span data-stu-id="141ea-160">A `Double`.</span></span>

<span data-ttu-id="141ea-161">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="141ea-162">STDEVP(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-162">STDEVP(expression)</span></span>

<span data-ttu-id="141ea-163">傳回指定運算式中所有值的母體擴展統計標準差。</span><span class="sxs-lookup"><span data-stu-id="141ea-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="141ea-164">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-164">**Arguments**</span></span>

<span data-ttu-id="141ea-165">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="141ea-165">A Collection(`Double`).</span></span>

<span data-ttu-id="141ea-166">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-166">**Return Value**</span></span>

<span data-ttu-id="141ea-167">`Double`。</span><span class="sxs-lookup"><span data-stu-id="141ea-167">A `Double`.</span></span>

<span data-ttu-id="141ea-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="141ea-169">SUM(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-169">SUM(expression)</span></span>

<span data-ttu-id="141ea-170">傳回集合中所有值的總和。</span><span class="sxs-lookup"><span data-stu-id="141ea-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="141ea-171">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-171">**Arguments**</span></span>

<span data-ttu-id="141ea-172">Collection(T)，其中 T 是下列類型之一： `Int32`， `Int64`， `Double`， `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="141ea-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="141ea-173">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-173">**Return Value**</span></span>

<span data-ttu-id="141ea-174">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="141ea-174">The type of `expression`.</span></span>

<span data-ttu-id="141ea-175">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="141ea-176">VAR(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-176">VAR(expression)</span></span>

<span data-ttu-id="141ea-177">傳回指定運算式中之所有值的統計變異數。</span><span class="sxs-lookup"><span data-stu-id="141ea-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="141ea-178">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-178">**Arguments**</span></span>

<span data-ttu-id="141ea-179">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="141ea-179">A Collection(`Double`).</span></span>

<span data-ttu-id="141ea-180">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-180">**Return Value**</span></span>

<span data-ttu-id="141ea-181">`Double`。</span><span class="sxs-lookup"><span data-stu-id="141ea-181">A `Double`.</span></span>

<span data-ttu-id="141ea-182">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="141ea-183">VARP(expression)</span><span class="sxs-lookup"><span data-stu-id="141ea-183">VARP(expression)</span></span>

<span data-ttu-id="141ea-184">傳回指定之運算式中所有值的母體擴展統計變異數。</span><span class="sxs-lookup"><span data-stu-id="141ea-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="141ea-185">**引數**</span><span class="sxs-lookup"><span data-stu-id="141ea-185">**Arguments**</span></span>

<span data-ttu-id="141ea-186">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="141ea-186">A Collection(`Double`).</span></span>

<span data-ttu-id="141ea-187">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="141ea-187">**Return Value**</span></span>

<span data-ttu-id="141ea-188">`Double`。</span><span class="sxs-lookup"><span data-stu-id="141ea-188">A `Double`.</span></span>

<span data-ttu-id="141ea-189">**範例**</span><span class="sxs-lookup"><span data-stu-id="141ea-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="141ea-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="141ea-190">See also</span></span>

<span data-ttu-id="141ea-191">如需 SqlClient 所支援彙總函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定 SQL Server 版本的說明文件：</span><span class="sxs-lookup"><span data-stu-id="141ea-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="141ea-192">**SQL Server 2005:**[彙總函式 (transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="141ea-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="141ea-193">**SQL Server 2008 及更新版本：**[彙總函式 (transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="141ea-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="141ea-194">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="141ea-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="141ea-195">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="141ea-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
