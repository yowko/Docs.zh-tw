---
title: 數學函式
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 63f83532c399f77e268913da3198327345b9c2ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143671"
---
# <a name="mathematical-functions"></a><span data-ttu-id="60632-102">數學函式</span><span class="sxs-lookup"><span data-stu-id="60632-102">Mathematical Functions</span></span>

<span data-ttu-id="60632-103">.NET Framework Data Provider for SQL Server (SqlClient) 提供了數學函式，這些函式會在當做引數提供的輸入值上執行計算，並傳回數值結果。</span><span class="sxs-lookup"><span data-stu-id="60632-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="60632-104">這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。</span><span class="sxs-lookup"><span data-stu-id="60632-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="60632-105">提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="60632-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="60632-106">下表將描述 SqlClient 數學函式。</span><span class="sxs-lookup"><span data-stu-id="60632-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="60632-107">ABS(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-107">ABS(expression)</span></span>

<span data-ttu-id="60632-108">執行絕對值函式。</span><span class="sxs-lookup"><span data-stu-id="60632-108">Performs the absolute value function.</span></span>

<span data-ttu-id="60632-109">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-109">**Arguments**</span></span>

<span data-ttu-id="60632-110">`expression`：`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="60632-111">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-111">**Return Value**</span></span>

<span data-ttu-id="60632-112">指定之運算式的絕對值。</span><span class="sxs-lookup"><span data-stu-id="60632-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="60632-113">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="60632-114">ACOS(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-114">ACOS(expression)</span></span>

<span data-ttu-id="60632-115">傳回指定之運算式的反餘弦函數 (Arccosine) 值。</span><span class="sxs-lookup"><span data-stu-id="60632-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="60632-116">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-116">**Arguments**</span></span>

<span data-ttu-id="60632-117">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="60632-118">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-118">**Return Value**</span></span>

<span data-ttu-id="60632-119">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-119">A `Double`.</span></span>

<span data-ttu-id="60632-120">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="60632-121">ASIN(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-121">ASIN(expression)</span></span>

<span data-ttu-id="60632-122">傳回指定之運算式的反正弦函數 (Arcsine) 值。</span><span class="sxs-lookup"><span data-stu-id="60632-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="60632-123">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-123">**Arguments**</span></span>

<span data-ttu-id="60632-124">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="60632-125">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-125">**Return Value**</span></span>

<span data-ttu-id="60632-126">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-126">A `Double`.</span></span>

<span data-ttu-id="60632-127">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="60632-128">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-128">ATAN(expression)</span></span>

<span data-ttu-id="60632-129">傳回指定之數值運算式的反正切函數 (Arctangent) 值。</span><span class="sxs-lookup"><span data-stu-id="60632-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="60632-130">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-130">**Arguments**</span></span>

<span data-ttu-id="60632-131">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="60632-132">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-132">**Return Value**</span></span>

<span data-ttu-id="60632-133">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-133">A `Double`.</span></span>

<span data-ttu-id="60632-134">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="60632-135">ATN2(expression, expression)</span><span class="sxs-lookup"><span data-stu-id="60632-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="60632-136">傳回其正切函數 (Tangent) 介於兩個指定數值運算式之間的角度 (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="60632-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="60632-137">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-137">**Arguments**</span></span>

<span data-ttu-id="60632-138">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="60632-139">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-139">**Return Value**</span></span>

<span data-ttu-id="60632-140">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-140">A `Double`.</span></span>

<span data-ttu-id="60632-141">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="60632-142">CEILING(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-142">CEILING(expression)</span></span>

<span data-ttu-id="60632-143">將指定的運算式轉換成大於或等於它的最小整數。</span><span class="sxs-lookup"><span data-stu-id="60632-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="60632-144">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-144">**Arguments**</span></span>

<span data-ttu-id="60632-145">`expression`：`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="60632-146">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-146">**Return Value**</span></span>

<span data-ttu-id="60632-147">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="60632-148">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="60632-149">COS(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-149">COS(expression)</span></span>

<span data-ttu-id="60632-150">計算指定之角度的三角餘弦函數 (Cosine) (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="60632-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="60632-151">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-151">**Arguments**</span></span> 

<span data-ttu-id="60632-152">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-153">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-153">**Return Value**</span></span> 

<span data-ttu-id="60632-154">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-154">A `Double`.</span></span> 

<span data-ttu-id="60632-155">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="60632-156">COT(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-156">COT(expression)</span></span>

<span data-ttu-id="60632-157">計算指定之角度的三角餘切函數 (Cotangent) (以弧度為單位)。</span><span class="sxs-lookup"><span data-stu-id="60632-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="60632-158">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-158">**Arguments**</span></span> 

<span data-ttu-id="60632-159">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-160">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-160">**Return Value**</span></span> 

<span data-ttu-id="60632-161">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-161">A `Double`.</span></span> 

<span data-ttu-id="60632-162">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="60632-163">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="60632-163">DEGREES(radians)</span></span>

<span data-ttu-id="60632-164">傳回以度數表示的對應角度。</span><span class="sxs-lookup"><span data-stu-id="60632-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="60632-165">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-165">**Arguments**</span></span> 

<span data-ttu-id="60632-166">`expression`：`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="60632-167">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-167">**Return Value**</span></span> 

<span data-ttu-id="60632-168">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="60632-169">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="60632-170">EXP(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-170">EXP(expression)</span></span>

<span data-ttu-id="60632-171">計算指定之數值運算式的指數值。</span><span class="sxs-lookup"><span data-stu-id="60632-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="60632-172">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-172">**Arguments**</span></span> 

<span data-ttu-id="60632-173">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-174">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-174">**Return Value**</span></span> 

<span data-ttu-id="60632-175">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-175">A `Double`.</span></span> 

<span data-ttu-id="60632-176">**範例** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="60632-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="60632-177">FLOOR(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-177">FLOOR(expression)</span></span>

<span data-ttu-id="60632-178">將指定的運算式轉換成小於或等於它的最大整數。</span><span class="sxs-lookup"><span data-stu-id="60632-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="60632-179">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-179">**Arguments**</span></span> 

<span data-ttu-id="60632-180">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-181">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-181">**Return Value**</span></span> 

<span data-ttu-id="60632-182">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-182">A `Double`.</span></span> 

<span data-ttu-id="60632-183">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="60632-184">LOG(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-184">LOG(expression)</span></span>

<span data-ttu-id="60632-185">計算指定之 `float` 運算式的自然對數。</span><span class="sxs-lookup"><span data-stu-id="60632-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="60632-186">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-186">**Arguments**</span></span> 

<span data-ttu-id="60632-187">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-188">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-188">**Return Value**</span></span> 

<span data-ttu-id="60632-189">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-189">A `Double`.</span></span> 

<span data-ttu-id="60632-190">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="60632-191">LOG10(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-191">LOG10(expression)</span></span>

<span data-ttu-id="60632-192">傳回指定 `Double` 運算式的以 10 為基底之對數。</span><span class="sxs-lookup"><span data-stu-id="60632-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="60632-193">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-193">**Arguments**</span></span> 

<span data-ttu-id="60632-194">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-195">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-195">**Return Value**</span></span> 

<span data-ttu-id="60632-196">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-196">A `Double`.</span></span> 

<span data-ttu-id="60632-197">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="60632-198">PI （)</span><span class="sxs-lookup"><span data-stu-id="60632-198">PI()</span></span>

<span data-ttu-id="60632-199">以 `Double` 形式傳回 pi 的常數值。</span><span class="sxs-lookup"><span data-stu-id="60632-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="60632-200">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-200">**Return Value**</span></span> 

<span data-ttu-id="60632-201">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-201">A `Double`.</span></span> 

<span data-ttu-id="60632-202">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="60632-203">POWER （numeric_expression，power_expression）</span><span class="sxs-lookup"><span data-stu-id="60632-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="60632-204">將指定之運算式的值計算至指定的乘冪。</span><span class="sxs-lookup"><span data-stu-id="60632-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="60632-205">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="60632-206">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="60632-207">A`Double`表示要引發 power `numeric_expression`。</span><span class="sxs-lookup"><span data-stu-id="60632-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="60632-208">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-208">**Return Value**</span></span> 

<span data-ttu-id="60632-209">指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。</span><span class="sxs-lookup"><span data-stu-id="60632-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="60632-210">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="60632-211">RADIANS(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-211">RADIANS(expression)</span></span>

<span data-ttu-id="60632-212">將度數轉換成弧度。</span><span class="sxs-lookup"><span data-stu-id="60632-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="60632-213">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-213">**Arguments**</span></span> 

<span data-ttu-id="60632-214">`expression`：`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="60632-215">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-215">**Return Value**</span></span> 

<span data-ttu-id="60632-216">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="60632-217">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="60632-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="60632-218">RAND([seed])</span></span>

<span data-ttu-id="60632-219">傳回 0 到 1 的隨機值。</span><span class="sxs-lookup"><span data-stu-id="60632-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="60632-220">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-220">**Arguments**</span></span> 

<span data-ttu-id="60632-221">初始值為`Int32`。</span><span class="sxs-lookup"><span data-stu-id="60632-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="60632-222">如果沒有指定初始值，SQL Server Database Engine 就會隨機指派一個初始值。</span><span class="sxs-lookup"><span data-stu-id="60632-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="60632-223">只要指定初始值之後，傳回的結果一律相同。</span><span class="sxs-lookup"><span data-stu-id="60632-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="60632-224">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-224">**Return Value**</span></span> 

<span data-ttu-id="60632-225">0 到 1 的隨機 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="60632-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="60632-226">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="60632-227">ROUND(numeric_expression, length[,function])</span><span class="sxs-lookup"><span data-stu-id="60632-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="60632-228">傳回已經進位到指定長度或有效位數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="60632-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="60632-229">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="60632-230">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="60632-231">`Int32`，代表 `numeric_expression` 要四捨五入的精確度。</span><span class="sxs-lookup"><span data-stu-id="60632-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="60632-232">當 `length` 是正數時，`numeric_expression` 會四捨五入到 `length` 所指定的十進位數。</span><span class="sxs-lookup"><span data-stu-id="60632-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="60632-233">當 `length` 是負數時，`numeric_expression` 會依照 `length` 所指定，在小數點左側四捨五入。</span><span class="sxs-lookup"><span data-stu-id="60632-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="60632-234">選擇性。</span><span class="sxs-lookup"><span data-stu-id="60632-234">Optional.</span></span> <span data-ttu-id="60632-235">`Int32` ，表示要執行的作業類型。</span><span class="sxs-lookup"><span data-stu-id="60632-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="60632-236">當函式遭到省略或者值為 0 （預設）、`numeric_expression`會捨入。</span><span class="sxs-lookup"><span data-stu-id="60632-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="60632-237">指定 0 以外的值時，`numeric_expression`會被截斷。</span><span class="sxs-lookup"><span data-stu-id="60632-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="60632-238">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-238">**Return Value**</span></span> 

<span data-ttu-id="60632-239">指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。</span><span class="sxs-lookup"><span data-stu-id="60632-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="60632-240">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="60632-241">SIGN(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-241">SIGN(expression)</span></span> 

<span data-ttu-id="60632-242">傳回指定運算式的正 (+1)、零 (0) 或負 (-1) 號。</span><span class="sxs-lookup"><span data-stu-id="60632-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="60632-243">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-243">**Arguments**</span></span> 

<span data-ttu-id="60632-244">`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`</span><span class="sxs-lookup"><span data-stu-id="60632-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="60632-245">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-245">**Return Value**</span></span> 

<span data-ttu-id="60632-246">`Int32`， `Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60632-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="60632-247">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="60632-248">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-248">SIN(expression)</span></span>

<span data-ttu-id="60632-249">計算指定之角度的三角正弦函數 (Sine) (以弧度為單位)，並傳回 `Double` 運算式。</span><span class="sxs-lookup"><span data-stu-id="60632-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="60632-250">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-250">**Arguments**</span></span> 

<span data-ttu-id="60632-251">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-252">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-252">**Return Value**</span></span> 

<span data-ttu-id="60632-253">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-253">A `Double`.</span></span> 

<span data-ttu-id="60632-254">**範例** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="60632-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="60632-255">SQRT(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-255">SQRT(expression)</span></span>

<span data-ttu-id="60632-256">傳回指定之運算式的平方根。</span><span class="sxs-lookup"><span data-stu-id="60632-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="60632-257">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-257">**Arguments**</span></span> 

<span data-ttu-id="60632-258">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-259">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-259">**Return Value**</span></span> 

<span data-ttu-id="60632-260">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-260">A `Double`.</span></span> 

<span data-ttu-id="60632-261">**範例** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="60632-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="60632-262">SQUARE(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-262">SQUARE(expression)</span></span>

<span data-ttu-id="60632-263">傳回指定之運算式的平方。</span><span class="sxs-lookup"><span data-stu-id="60632-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="60632-264">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-264">**Arguments**</span></span> 

<span data-ttu-id="60632-265">`expression`：`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="60632-266">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-266">**Return Value**</span></span> 

<span data-ttu-id="60632-267">`Double`。</span><span class="sxs-lookup"><span data-stu-id="60632-267">A `Double`.</span></span> 

<span data-ttu-id="60632-268">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="60632-269">TAN(expression)</span><span class="sxs-lookup"><span data-stu-id="60632-269">TAN(expression)</span></span>

<span data-ttu-id="60632-270">計算指定之運算式的正切函數。</span><span class="sxs-lookup"><span data-stu-id="60632-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="60632-271">**引數**</span><span class="sxs-lookup"><span data-stu-id="60632-271">**Arguments**</span></span> 

<span data-ttu-id="60632-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="60632-272">`expression`: `Double`</span></span> 

<span data-ttu-id="60632-273">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="60632-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="60632-274">**範例**</span><span class="sxs-lookup"><span data-stu-id="60632-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="60632-275">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60632-275">See also</span></span>

<span data-ttu-id="60632-276">如需 SqlClient 支援之數學函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定之 SQL Server 版本的說明文件：</span><span class="sxs-lookup"><span data-stu-id="60632-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="60632-277">**SQL Server 2005:**[數學函數 & Amp;#40;transact-SQL&AMP;#41](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="60632-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="60632-278">**SQL Server 2008：**[數學函數 & Amp;#40;transact-SQL&AMP;#41](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="60632-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="60632-279">**SQL Server 2012 和更新版本：**[數學函數 & Amp;#40;transact-SQL&AMP;#41](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="60632-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="60632-280">適用於 Entity Framework 的 SqlClient 函式</span><span class="sxs-lookup"><span data-stu-id="60632-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
