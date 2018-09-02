---
title: 彙總函式 (適用於 Entity Framework 的 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 8ed9a58da9914724fe312876d6594cb526f2e0e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452895"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="933fd-102">彙總函式 (適用於 Entity Framework 的 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="933fd-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="933fd-103">.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。</span><span class="sxs-lookup"><span data-stu-id="933fd-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="933fd-104">彙總函式會對一組輸入值執行計算，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="933fd-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="933fd-105">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="933fd-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="933fd-106">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="933fd-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="933fd-107">以下是 SqlClient 彙總函式。</span><span class="sxs-lookup"><span data-stu-id="933fd-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="933fd-108">AVG(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-108">AVG(expression)</span></span>

<span data-ttu-id="933fd-109">傳回集合中各個值的平均值。</span><span class="sxs-lookup"><span data-stu-id="933fd-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="933fd-110">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="933fd-110">Null values are ignored.</span></span>

<span data-ttu-id="933fd-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-111">**Arguments**</span></span>

<span data-ttu-id="933fd-112">`Int32`， `Int64`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="933fd-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="933fd-113">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-113">**Return Value**</span></span>

<span data-ttu-id="933fd-114">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="933fd-114">The type of `expression`.</span></span>

<span data-ttu-id="933fd-115">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="933fd-116">CHECKSUM_AGG(collection)</span><span class="sxs-lookup"><span data-stu-id="933fd-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="933fd-117">傳回集合中值的總和檢查碼 (Checksum)。</span><span class="sxs-lookup"><span data-stu-id="933fd-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="933fd-118">會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="933fd-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="933fd-119">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-119">**Arguments**</span></span>
 
 <span data-ttu-id="933fd-120">集合 (`Int32`)。</span><span class="sxs-lookup"><span data-stu-id="933fd-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="933fd-121">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-121">**Return Value**</span></span>
 
 <span data-ttu-id="933fd-122">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="933fd-122">An `Int32`.</span></span>
 
 <span data-ttu-id="933fd-123">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="933fd-124">COUNT(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-124">COUNT(expression)</span></span>

<span data-ttu-id="933fd-125">以 `Int32` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="933fd-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="933fd-126">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-126">**Arguments**</span></span>

<span data-ttu-id="933fd-127">集合\<T >，其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="933fd-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="933fd-128">`Guid` （SQL Server 2000 中不會傳回）</span><span class="sxs-lookup"><span data-stu-id="933fd-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="933fd-129">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-129">**Return Value**</span></span>

<span data-ttu-id="933fd-130">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="933fd-130">An `Int32`.</span></span>

<span data-ttu-id="933fd-131">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="933fd-132">[！ 的程式碼 sql[DP EntityServices 概念 #SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="933fd-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="933fd-133">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="933fd-134">以 `bigint` 形式傳回集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="933fd-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="933fd-135">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-135">**Arguments**</span></span>
 
 <span data-ttu-id="933fd-136">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="933fd-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="933fd-137">`Guid` （SQL Server 2000 中不會傳回）</span><span class="sxs-lookup"><span data-stu-id="933fd-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="933fd-138">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-138">**Return Value**</span></span>

<span data-ttu-id="933fd-139">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="933fd-139">An `Int64`.</span></span>

<span data-ttu-id="933fd-140">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="933fd-141">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-141">MAX(expression)</span></span>

<span data-ttu-id="933fd-142">傳回集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="933fd-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="933fd-143">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-143">**Arguments**</span></span>

<span data-ttu-id="933fd-144">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="933fd-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="933fd-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-145">**Return Value**</span></span>

<span data-ttu-id="933fd-146">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="933fd-146">The type of `expression`.</span></span>

<span data-ttu-id="933fd-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="933fd-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-148">MIN(expression)</span></span>

<span data-ttu-id="933fd-149">傳回集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="933fd-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="933fd-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-150">**Arguments**</span></span>

<span data-ttu-id="933fd-151">這種 Collection(T) 其中 T 是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="933fd-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="933fd-152">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-152">**Return Value**</span></span>

<span data-ttu-id="933fd-153">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="933fd-153">The type of `expression`.</span></span>

<span data-ttu-id="933fd-154">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="933fd-155">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-155">STDEV(expression)</span></span>

<span data-ttu-id="933fd-156">傳回指定運算式中之所有值的統計標準差。</span><span class="sxs-lookup"><span data-stu-id="933fd-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="933fd-157">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-157">**Arguments**</span></span>

<span data-ttu-id="933fd-158">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="933fd-158">A Collection(`Double`).</span></span>

<span data-ttu-id="933fd-159">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-159">**Return Value**</span></span>

<span data-ttu-id="933fd-160">`Double`。</span><span class="sxs-lookup"><span data-stu-id="933fd-160">A `Double`.</span></span>

<span data-ttu-id="933fd-161">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="933fd-162">STDEVP(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-162">STDEVP(expression)</span></span>

<span data-ttu-id="933fd-163">傳回指定運算式中所有值的母體擴展統計標準差。</span><span class="sxs-lookup"><span data-stu-id="933fd-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="933fd-164">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-164">**Arguments**</span></span>

<span data-ttu-id="933fd-165">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="933fd-165">A Collection(`Double`).</span></span>

<span data-ttu-id="933fd-166">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-166">**Return Value**</span></span>

<span data-ttu-id="933fd-167">`Double`。</span><span class="sxs-lookup"><span data-stu-id="933fd-167">A `Double`.</span></span>

<span data-ttu-id="933fd-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="933fd-169">SUM(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-169">SUM(expression)</span></span>

<span data-ttu-id="933fd-170">傳回集合中所有值的總和。</span><span class="sxs-lookup"><span data-stu-id="933fd-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="933fd-171">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-171">**Arguments**</span></span>

<span data-ttu-id="933fd-172">Collection(T)，其中 T 是下列類型之一： `Int32`， `Int64`， `Double`， `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="933fd-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="933fd-173">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-173">**Return Value**</span></span>

<span data-ttu-id="933fd-174">`expression` 的類型。</span><span class="sxs-lookup"><span data-stu-id="933fd-174">The type of `expression`.</span></span>

<span data-ttu-id="933fd-175">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="933fd-176">VAR(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-176">VAR(expression)</span></span>

<span data-ttu-id="933fd-177">傳回指定運算式中之所有值的統計變異數。</span><span class="sxs-lookup"><span data-stu-id="933fd-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="933fd-178">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-178">**Arguments**</span></span>

<span data-ttu-id="933fd-179">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="933fd-179">A Collection(`Double`).</span></span>

<span data-ttu-id="933fd-180">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-180">**Return Value**</span></span>

<span data-ttu-id="933fd-181">`Double`。</span><span class="sxs-lookup"><span data-stu-id="933fd-181">A `Double`.</span></span>

<span data-ttu-id="933fd-182">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="933fd-183">VARP(expression)</span><span class="sxs-lookup"><span data-stu-id="933fd-183">VARP(expression)</span></span>

<span data-ttu-id="933fd-184">傳回指定之運算式中所有值的母體擴展統計變異數。</span><span class="sxs-lookup"><span data-stu-id="933fd-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="933fd-185">**引數**</span><span class="sxs-lookup"><span data-stu-id="933fd-185">**Arguments**</span></span>

<span data-ttu-id="933fd-186">集合 (`Double`)。</span><span class="sxs-lookup"><span data-stu-id="933fd-186">A Collection(`Double`).</span></span>

<span data-ttu-id="933fd-187">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="933fd-187">**Return Value**</span></span>

<span data-ttu-id="933fd-188">`Double`。</span><span class="sxs-lookup"><span data-stu-id="933fd-188">A `Double`.</span></span>

<span data-ttu-id="933fd-189">**範例**</span><span class="sxs-lookup"><span data-stu-id="933fd-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="933fd-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="933fd-190">See also</span></span>

<span data-ttu-id="933fd-191">如需 SqlClient 所支援彙總函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定 SQL Server 版本的說明文件：</span><span class="sxs-lookup"><span data-stu-id="933fd-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="933fd-192">**SQL Server 2005**:[彙總函式 & Amp;#40;transact-SQL&AMP;#41;](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="933fd-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="933fd-193">**SQL Server 2008 及更新版本**:[彙總函式 & Amp;#40;transact-SQL&AMP;#41;](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="933fd-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
[<span data-ttu-id="933fd-194">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="933fd-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
[<span data-ttu-id="933fd-195">彙總標準函式</span><span class="sxs-lookup"><span data-stu-id="933fd-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
