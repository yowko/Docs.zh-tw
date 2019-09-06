---
title: 數學標準函式
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250312"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="cccc2-102">數學標準函式</span><span class="sxs-lookup"><span data-stu-id="cccc2-102">Math Canonical Functions</span></span>

<span data-ttu-id="cccc2-103">Entity SQL 包含下列數學標準函式：</span><span class="sxs-lookup"><span data-stu-id="cccc2-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="cccc2-104">Abs(value)</span><span class="sxs-lookup"><span data-stu-id="cccc2-104">Abs(value)</span></span>

<span data-ttu-id="cccc2-105">傳回 `value` 的絕對值。</span><span class="sxs-lookup"><span data-stu-id="cccc2-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="cccc2-106">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-106">**Arguments**</span></span>

<span data-ttu-id="cccc2-107">`Int16`、 、、`Int64`、 、和`Decimal`。 `Int32` `Byte` `Single` `Double`</span><span class="sxs-lookup"><span data-stu-id="cccc2-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="cccc2-108">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-108">**Return Value**</span></span>

<span data-ttu-id="cccc2-109">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-109">The type of `value`.</span></span>

<span data-ttu-id="cccc2-110">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="cccc2-111">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="cccc2-111">Ceiling(value)</span></span>

<span data-ttu-id="cccc2-112">傳回大於或等於 `value` 的最小整數。</span><span class="sxs-lookup"><span data-stu-id="cccc2-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="cccc2-113">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-113">**Arguments**</span></span>

<span data-ttu-id="cccc2-114">`Single` 、`Double`和。`Decimal`</span><span class="sxs-lookup"><span data-stu-id="cccc2-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="cccc2-115">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-115">**Return Value**</span></span>

<span data-ttu-id="cccc2-116">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-116">The type of `value`.</span></span>

<span data-ttu-id="cccc2-117">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="cccc2-118">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="cccc2-118">Floor(value)</span></span>

<span data-ttu-id="cccc2-119">傳回小於或等於 `value` 的最大整數。</span><span class="sxs-lookup"><span data-stu-id="cccc2-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="cccc2-120">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-120">**Arguments**</span></span>

<span data-ttu-id="cccc2-121">`Single` 、`Double`和。`Decimal`</span><span class="sxs-lookup"><span data-stu-id="cccc2-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="cccc2-122">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-122">**Return Value**</span></span>

<span data-ttu-id="cccc2-123">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-123">The type of `value`.</span></span>

<span data-ttu-id="cccc2-124">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="cccc2-125">Power(值、指數)</span><span class="sxs-lookup"><span data-stu-id="cccc2-125">Power(value, exponent)</span></span>

<span data-ttu-id="cccc2-126">傳回指定的 `value` 結果至指定的 `exponent`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="cccc2-127">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="cccc2-128">`Int32, Int64, Double`、或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="cccc2-129">`Int64` 、`Double`或。`Decimal`</span><span class="sxs-lookup"><span data-stu-id="cccc2-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="cccc2-130">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-130">**Return Value**</span></span>

<span data-ttu-id="cccc2-131">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-131">The type of `value`.</span></span>

<span data-ttu-id="cccc2-132">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="cccc2-133">Round(value)</span><span class="sxs-lookup"><span data-stu-id="cccc2-133">Round(value)</span></span>

<span data-ttu-id="cccc2-134">傳回 `value` 的整數部分，四捨五入成最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="cccc2-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="cccc2-135">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-135">**Arguments**</span></span>

<span data-ttu-id="cccc2-136">`Single` 、`Double`和。`Decimal`</span><span class="sxs-lookup"><span data-stu-id="cccc2-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="cccc2-137">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-137">**Return Value**</span></span>

<span data-ttu-id="cccc2-138">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-138">The type of `value`.</span></span>

<span data-ttu-id="cccc2-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="cccc2-140">Round(值、數字)</span><span class="sxs-lookup"><span data-stu-id="cccc2-140">Round(value, digits)</span></span>

<span data-ttu-id="cccc2-141">傳回 `value`，四捨五入至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="cccc2-142">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="cccc2-143">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="cccc2-144">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="cccc2-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-145">**Return Value**</span></span>

<span data-ttu-id="cccc2-146">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-146">The type of `value`.</span></span>

<span data-ttu-id="cccc2-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="cccc2-148">Truncate(值、數字)</span><span class="sxs-lookup"><span data-stu-id="cccc2-148">Truncate(value, digits)</span></span>

<span data-ttu-id="cccc2-149">傳回 `value`，截斷至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="cccc2-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="cccc2-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="cccc2-151">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="cccc2-152">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="cccc2-153">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="cccc2-153">**Return Value**</span></span>

<span data-ttu-id="cccc2-154">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="cccc2-154">The type of `value`.</span></span>

<span data-ttu-id="cccc2-155">**範例**</span><span class="sxs-lookup"><span data-stu-id="cccc2-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="cccc2-156">如果提供 `null` 輸入，這些函式會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="cccc2-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="cccc2-157">Microsoft SQL Client Managed Provider 中提供了對等的功能。</span><span class="sxs-lookup"><span data-stu-id="cccc2-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="cccc2-158">如需詳細資訊，請參閱[SqlClient for Entity Framework 函數](../sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="cccc2-158">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccc2-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cccc2-159">See also</span></span>

- [<span data-ttu-id="cccc2-160">標準函式</span><span class="sxs-lookup"><span data-stu-id="cccc2-160">Canonical Functions</span></span>](canonical-functions.md)
