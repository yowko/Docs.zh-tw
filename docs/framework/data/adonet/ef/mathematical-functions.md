---
title: 數學函式
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697876"
---
# <a name="mathematical-functions"></a><span data-ttu-id="cd935-102">數學函式</span><span class="sxs-lookup"><span data-stu-id="cd935-102">Mathematical Functions</span></span>

<span data-ttu-id="cd935-103">.NET Framework Data Provider for SQL Server (SqlClient) 提供了數學函式，這些函式會在當做引數提供的輸入值上執行計算，並傳回數值結果。</span><span class="sxs-lookup"><span data-stu-id="cd935-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="cd935-104">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="cd935-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="cd935-105">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。下表將描述 SqlClient 數學函式。</span><span class="sxs-lookup"><span data-stu-id="cd935-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="cd935-106">ABS(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-106">ABS(expression)</span></span>

<span data-ttu-id="cd935-107">執行絕對值函式。</span><span class="sxs-lookup"><span data-stu-id="cd935-107">Performs the absolute value function.</span></span>

<span data-ttu-id="cd935-108">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-108">**Arguments**</span></span>

<span data-ttu-id="cd935-109">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd935-110">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-110">**Return Value**</span></span>

<span data-ttu-id="cd935-111">指定之運算式的絕對值。</span><span class="sxs-lookup"><span data-stu-id="cd935-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="cd935-112">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="cd935-113">ACOS(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-113">ACOS(expression)</span></span>

<span data-ttu-id="cd935-114">傳回指定之運算式的反餘弦函數 (Arccosine) 值。</span><span class="sxs-lookup"><span data-stu-id="cd935-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="cd935-115">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-115">**Arguments**</span></span>

<span data-ttu-id="cd935-116">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd935-117">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-117">**Return Value**</span></span>

<span data-ttu-id="cd935-118">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-118">A `Double`.</span></span>

<span data-ttu-id="cd935-119">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="cd935-120">ASIN(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-120">ASIN(expression)</span></span>

<span data-ttu-id="cd935-121">傳回指定之運算式的反正弦函數 (Arcsine) 值。</span><span class="sxs-lookup"><span data-stu-id="cd935-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="cd935-122">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-122">**Arguments**</span></span>

<span data-ttu-id="cd935-123">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd935-124">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-124">**Return Value**</span></span>

<span data-ttu-id="cd935-125">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-125">A `Double`.</span></span>

<span data-ttu-id="cd935-126">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="cd935-127">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-127">ATAN(expression)</span></span>

<span data-ttu-id="cd935-128">傳回指定之數值運算式的反正切函數 (Arctangent) 值。</span><span class="sxs-lookup"><span data-stu-id="cd935-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="cd935-129">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-129">**Arguments**</span></span>

<span data-ttu-id="cd935-130">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd935-131">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-131">**Return Value**</span></span>

<span data-ttu-id="cd935-132">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-132">A `Double`.</span></span>

<span data-ttu-id="cd935-133">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="cd935-134">ATN2(expression, expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="cd935-135">傳回其正切函數 (Tangent) 介於兩個指定數值運算式之間的角度 (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="cd935-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="cd935-136">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-136">**Arguments**</span></span>

<span data-ttu-id="cd935-137">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd935-138">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-138">**Return Value**</span></span>

<span data-ttu-id="cd935-139">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-139">A `Double`.</span></span>

<span data-ttu-id="cd935-140">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="cd935-141">CEILING(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-141">CEILING(expression)</span></span>

<span data-ttu-id="cd935-142">將指定的運算式轉換成大於或等於它的最小整數。</span><span class="sxs-lookup"><span data-stu-id="cd935-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="cd935-143">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-143">**Arguments**</span></span>

<span data-ttu-id="cd935-144">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd935-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-145">**Return Value**</span></span>

<span data-ttu-id="cd935-146">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd935-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="cd935-148">COS(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-148">COS(expression)</span></span>

<span data-ttu-id="cd935-149">計算指定之角度的三角餘弦函數 (Cosine) (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="cd935-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="cd935-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-150">**Arguments**</span></span> 

<span data-ttu-id="cd935-151">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-152">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-152">**Return Value**</span></span> 

<span data-ttu-id="cd935-153">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-153">A `Double`.</span></span> 

<span data-ttu-id="cd935-154">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="cd935-155">COT(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-155">COT(expression)</span></span>

<span data-ttu-id="cd935-156">計算指定之角度的三角餘切函數 (Cotangent) (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="cd935-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="cd935-157">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-157">**Arguments**</span></span> 

<span data-ttu-id="cd935-158">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-159">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-159">**Return Value**</span></span> 

<span data-ttu-id="cd935-160">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-160">A `Double`.</span></span> 

<span data-ttu-id="cd935-161">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="cd935-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="cd935-162">DEGREES(radians)</span></span>

<span data-ttu-id="cd935-163">傳回以度數表示的對應角度。</span><span class="sxs-lookup"><span data-stu-id="cd935-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="cd935-164">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-164">**Arguments**</span></span> 

<span data-ttu-id="cd935-165">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd935-166">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-166">**Return Value**</span></span> 

<span data-ttu-id="cd935-167">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd935-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="cd935-169">EXP(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-169">EXP(expression)</span></span>

<span data-ttu-id="cd935-170">計算指定之數值運算式的指數值。</span><span class="sxs-lookup"><span data-stu-id="cd935-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="cd935-171">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-171">**Arguments**</span></span> 

<span data-ttu-id="cd935-172">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-173">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-173">**Return Value**</span></span> 

<span data-ttu-id="cd935-174">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-174">A `Double`.</span></span> 

<span data-ttu-id="cd935-175">**範例** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="cd935-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="cd935-176">FLOOR(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-176">FLOOR(expression)</span></span>

<span data-ttu-id="cd935-177">將指定的運算式轉換成小於或等於它的最大整數。</span><span class="sxs-lookup"><span data-stu-id="cd935-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="cd935-178">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-178">**Arguments**</span></span> 

<span data-ttu-id="cd935-179">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-180">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-180">**Return Value**</span></span> 

<span data-ttu-id="cd935-181">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-181">A `Double`.</span></span> 

<span data-ttu-id="cd935-182">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="cd935-183">LOG(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-183">LOG(expression)</span></span>

<span data-ttu-id="cd935-184">計算指定之 `float` 運算式的自然對數。</span><span class="sxs-lookup"><span data-stu-id="cd935-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="cd935-185">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-185">**Arguments**</span></span> 

<span data-ttu-id="cd935-186">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-187">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-187">**Return Value**</span></span> 

<span data-ttu-id="cd935-188">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-188">A `Double`.</span></span> 

<span data-ttu-id="cd935-189">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="cd935-190">LOG10(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-190">LOG10(expression)</span></span>

<span data-ttu-id="cd935-191">傳回指定 `Double` 運算式的以 10 為基底之對數。</span><span class="sxs-lookup"><span data-stu-id="cd935-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="cd935-192">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-192">**Arguments**</span></span> 

<span data-ttu-id="cd935-193">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-194">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-194">**Return Value**</span></span> 

<span data-ttu-id="cd935-195">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-195">A `Double`.</span></span> 

<span data-ttu-id="cd935-196">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="cd935-197">PI （)</span><span class="sxs-lookup"><span data-stu-id="cd935-197">PI()</span></span>

<span data-ttu-id="cd935-198">以 `Double` 形式傳回 pi 的常數值。</span><span class="sxs-lookup"><span data-stu-id="cd935-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="cd935-199">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-199">**Return Value**</span></span> 

<span data-ttu-id="cd935-200">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-200">A `Double`.</span></span> 

<span data-ttu-id="cd935-201">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="cd935-202">POWER （numeric_expression，power_expression）</span><span class="sxs-lookup"><span data-stu-id="cd935-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="cd935-203">將指定之運算式的值計算至指定的乘冪。</span><span class="sxs-lookup"><span data-stu-id="cd935-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="cd935-204">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="cd935-205">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="cd935-206">A`Double`表示要引發 power `numeric_expression`。</span><span class="sxs-lookup"><span data-stu-id="cd935-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="cd935-207">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-207">**Return Value**</span></span> 

<span data-ttu-id="cd935-208">指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。</span><span class="sxs-lookup"><span data-stu-id="cd935-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="cd935-209">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="cd935-210">RADIANS(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-210">RADIANS(expression)</span></span>

<span data-ttu-id="cd935-211">將度數轉換成弧度。</span><span class="sxs-lookup"><span data-stu-id="cd935-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="cd935-212">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-212">**Arguments**</span></span> 

<span data-ttu-id="cd935-213">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd935-214">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-214">**Return Value**</span></span> 

<span data-ttu-id="cd935-215">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd935-216">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="cd935-217">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="cd935-217">RAND([seed])</span></span>

<span data-ttu-id="cd935-218">傳回 0 到 1 的隨機值。</span><span class="sxs-lookup"><span data-stu-id="cd935-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="cd935-219">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-219">**Arguments**</span></span> 

<span data-ttu-id="cd935-220">初始值為`Int32`。</span><span class="sxs-lookup"><span data-stu-id="cd935-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="cd935-221">如果沒有指定初始值，SQL Server Database Engine 就會隨機指派一個初始值。</span><span class="sxs-lookup"><span data-stu-id="cd935-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="cd935-222">只要指定初始值之後，傳回的結果一律相同。</span><span class="sxs-lookup"><span data-stu-id="cd935-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="cd935-223">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-223">**Return Value**</span></span> 

<span data-ttu-id="cd935-224">0 到 1 的隨機 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="cd935-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="cd935-225">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="cd935-226">ROUND(numeric_expression, length[,function])</span><span class="sxs-lookup"><span data-stu-id="cd935-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="cd935-227">傳回已經進位到指定長度或有效位數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="cd935-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="cd935-228">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="cd935-229">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="cd935-230">`Int32`，代表 `numeric_expression` 要四捨五入的精確度。</span><span class="sxs-lookup"><span data-stu-id="cd935-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="cd935-231">當 `length` 是正數時，`numeric_expression` 會四捨五入到 `length` 所指定的十進位數。</span><span class="sxs-lookup"><span data-stu-id="cd935-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="cd935-232">當 `length` 是負數時，`numeric_expression` 會依照 `length` 所指定，在小數點左側四捨五入。</span><span class="sxs-lookup"><span data-stu-id="cd935-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="cd935-233">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cd935-233">Optional.</span></span> <span data-ttu-id="cd935-234">`Int32` ，表示要執行的作業類型。</span><span class="sxs-lookup"><span data-stu-id="cd935-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="cd935-235">當函式遭到省略或者值為 0 （預設）、`numeric_expression`會捨入。</span><span class="sxs-lookup"><span data-stu-id="cd935-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="cd935-236">指定 0 以外的值時，`numeric_expression`會被截斷。</span><span class="sxs-lookup"><span data-stu-id="cd935-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="cd935-237">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-237">**Return Value**</span></span> 

<span data-ttu-id="cd935-238">指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。</span><span class="sxs-lookup"><span data-stu-id="cd935-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="cd935-239">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="cd935-240">SIGN(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-240">SIGN(expression)</span></span> 

<span data-ttu-id="cd935-241">傳回指定運算式的正 (+1)、零 (0) 或負 (-1) 號。</span><span class="sxs-lookup"><span data-stu-id="cd935-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="cd935-242">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-242">**Arguments**</span></span> 

<span data-ttu-id="cd935-243">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`</span><span class="sxs-lookup"><span data-stu-id="cd935-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="cd935-244">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-244">**Return Value**</span></span> 

<span data-ttu-id="cd935-245">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cd935-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd935-246">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="cd935-247">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-247">SIN(expression)</span></span>

<span data-ttu-id="cd935-248">計算指定之角度的三角正弦函數 (Sine) (以弧度為單位)，並傳回 `Double` 運算式。</span><span class="sxs-lookup"><span data-stu-id="cd935-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="cd935-249">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-249">**Arguments**</span></span> 

<span data-ttu-id="cd935-250">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-251">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-251">**Return Value**</span></span> 

<span data-ttu-id="cd935-252">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-252">A `Double`.</span></span> 

<span data-ttu-id="cd935-253">**範例** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="cd935-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="cd935-254">SQRT(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-254">SQRT(expression)</span></span>

<span data-ttu-id="cd935-255">傳回指定之運算式的平方根。</span><span class="sxs-lookup"><span data-stu-id="cd935-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="cd935-256">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-256">**Arguments**</span></span> 

<span data-ttu-id="cd935-257">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-258">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-258">**Return Value**</span></span> 

<span data-ttu-id="cd935-259">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-259">A `Double`.</span></span> 

<span data-ttu-id="cd935-260">**範例** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="cd935-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="cd935-261">SQUARE(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-261">SQUARE(expression)</span></span>

<span data-ttu-id="cd935-262">傳回指定之運算式的平方。</span><span class="sxs-lookup"><span data-stu-id="cd935-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="cd935-263">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-263">**Arguments**</span></span> 

<span data-ttu-id="cd935-264">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd935-265">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-265">**Return Value**</span></span> 

<span data-ttu-id="cd935-266">`Double`。</span><span class="sxs-lookup"><span data-stu-id="cd935-266">A `Double`.</span></span> 

<span data-ttu-id="cd935-267">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="cd935-268">TAN(expression)</span><span class="sxs-lookup"><span data-stu-id="cd935-268">TAN(expression)</span></span>

<span data-ttu-id="cd935-269">計算指定之運算式的正切函數。</span><span class="sxs-lookup"><span data-stu-id="cd935-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="cd935-270">**引數**</span><span class="sxs-lookup"><span data-stu-id="cd935-270">**Arguments**</span></span> 

<span data-ttu-id="cd935-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="cd935-271">`expression`: `Double`</span></span> 

<span data-ttu-id="cd935-272">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cd935-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="cd935-273">**範例**</span><span class="sxs-lookup"><span data-stu-id="cd935-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="cd935-274">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd935-274">See also</span></span>

<span data-ttu-id="cd935-275">如需 SqlClient 支援之數學函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定之 SQL Server 版本的說明文件：</span><span class="sxs-lookup"><span data-stu-id="cd935-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="cd935-276">**SQL Server 2005:** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="cd935-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="cd935-277">**SQL Server 2008:** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="cd935-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="cd935-278">**SQL Server 2012 及更新版本：** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="cd935-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="cd935-279">適用於 Entity Framework 的 SqlClient 函式</span><span class="sxs-lookup"><span data-stu-id="cd935-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
