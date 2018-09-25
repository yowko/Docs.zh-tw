---
title: 數學標準函式
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111645"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="1e889-102">數學標準函式</span><span class="sxs-lookup"><span data-stu-id="1e889-102">Math Canonical Functions</span></span>

<span data-ttu-id="1e889-103">Entity SQL 包含下列的數學標準函式：</span><span class="sxs-lookup"><span data-stu-id="1e889-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="1e889-104">Abs(value)</span><span class="sxs-lookup"><span data-stu-id="1e889-104">Abs(value)</span></span>

<span data-ttu-id="1e889-105">傳回 `value` 的絕對值。</span><span class="sxs-lookup"><span data-stu-id="1e889-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="1e889-106">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-106">**Arguments**</span></span>

<span data-ttu-id="1e889-107">`Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1e889-108">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-108">**Return Value**</span></span>

<span data-ttu-id="1e889-109">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-109">The type of `value`.</span></span>

<span data-ttu-id="1e889-110">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="1e889-111">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="1e889-111">Ceiling(value)</span></span>

<span data-ttu-id="1e889-112">傳回大於或等於 `value` 的最小整數。</span><span class="sxs-lookup"><span data-stu-id="1e889-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="1e889-113">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-113">**Arguments**</span></span>

<span data-ttu-id="1e889-114">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1e889-115">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-115">**Return Value**</span></span>

<span data-ttu-id="1e889-116">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-116">The type of `value`.</span></span>

<span data-ttu-id="1e889-117">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="1e889-118">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="1e889-118">Floor(value)</span></span>

<span data-ttu-id="1e889-119">傳回小於或等於 `value` 的最大整數。</span><span class="sxs-lookup"><span data-stu-id="1e889-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="1e889-120">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-120">**Arguments**</span></span>

<span data-ttu-id="1e889-121">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1e889-122">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-122">**Return Value**</span></span>

<span data-ttu-id="1e889-123">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-123">The type of `value`.</span></span>

<span data-ttu-id="1e889-124">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="1e889-125">Power(值、指數)</span><span class="sxs-lookup"><span data-stu-id="1e889-125">Power(value, exponent)</span></span>

<span data-ttu-id="1e889-126">傳回指定的 `value` 結果至指定的 `exponent`。</span><span class="sxs-lookup"><span data-stu-id="1e889-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="1e889-127">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="1e889-128">`Int32, Int64, Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="1e889-129">`Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="1e889-130">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-130">**Return Value**</span></span>

<span data-ttu-id="1e889-131">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-131">The type of `value`.</span></span>

<span data-ttu-id="1e889-132">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="1e889-133">Round(value)</span><span class="sxs-lookup"><span data-stu-id="1e889-133">Round(value)</span></span>

<span data-ttu-id="1e889-134">傳回 `value` 的整數部分，四捨五入成最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="1e889-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="1e889-135">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-135">**Arguments**</span></span>

<span data-ttu-id="1e889-136">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1e889-137">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-137">**Return Value**</span></span>

<span data-ttu-id="1e889-138">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-138">The type of `value`.</span></span>

<span data-ttu-id="1e889-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="1e889-140">Round(值、數字)</span><span class="sxs-lookup"><span data-stu-id="1e889-140">Round(value, digits)</span></span>

<span data-ttu-id="1e889-141">傳回 `value`，四捨五入至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="1e889-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="1e889-142">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="1e889-143">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="1e889-144">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="1e889-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="1e889-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-145">**Return Value**</span></span>

<span data-ttu-id="1e889-146">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-146">The type of `value`.</span></span>

<span data-ttu-id="1e889-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="1e889-148">Truncate(值、數字)</span><span class="sxs-lookup"><span data-stu-id="1e889-148">Truncate(value, digits)</span></span>

<span data-ttu-id="1e889-149">傳回 `value`，截斷至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="1e889-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="1e889-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="1e889-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="1e889-151">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1e889-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="1e889-152">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="1e889-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="1e889-153">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="1e889-153">**Return Value**</span></span>

<span data-ttu-id="1e889-154">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="1e889-154">The type of `value`.</span></span>

<span data-ttu-id="1e889-155">**範例**</span><span class="sxs-lookup"><span data-stu-id="1e889-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="1e889-156">如果提供 `null` 輸入，這些函式會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="1e889-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="1e889-157">Microsoft SQL Client Managed Provider 中提供了對等的功能。</span><span class="sxs-lookup"><span data-stu-id="1e889-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="1e889-158">如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="1e889-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e889-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e889-159">See Also</span></span>  
 [<span data-ttu-id="1e889-160">標準函式</span><span class="sxs-lookup"><span data-stu-id="1e889-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
