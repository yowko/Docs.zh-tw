---
title: 數學標準函式
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708084"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="52823-102">數學標準函式</span><span class="sxs-lookup"><span data-stu-id="52823-102">Math Canonical Functions</span></span>

<span data-ttu-id="52823-103">Entity SQL 包含下列的數學標準函式：</span><span class="sxs-lookup"><span data-stu-id="52823-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="52823-104">Abs(value)</span><span class="sxs-lookup"><span data-stu-id="52823-104">Abs(value)</span></span>

<span data-ttu-id="52823-105">傳回 `value` 的絕對值。</span><span class="sxs-lookup"><span data-stu-id="52823-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="52823-106">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-106">**Arguments**</span></span>

<span data-ttu-id="52823-107">`Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="52823-108">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-108">**Return Value**</span></span>

<span data-ttu-id="52823-109">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-109">The type of `value`.</span></span>

<span data-ttu-id="52823-110">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="52823-111">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="52823-111">Ceiling(value)</span></span>

<span data-ttu-id="52823-112">傳回大於或等於 `value` 的最小整數。</span><span class="sxs-lookup"><span data-stu-id="52823-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="52823-113">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-113">**Arguments**</span></span>

<span data-ttu-id="52823-114">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="52823-115">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-115">**Return Value**</span></span>

<span data-ttu-id="52823-116">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-116">The type of `value`.</span></span>

<span data-ttu-id="52823-117">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="52823-118">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="52823-118">Floor(value)</span></span>

<span data-ttu-id="52823-119">傳回小於或等於 `value` 的最大整數。</span><span class="sxs-lookup"><span data-stu-id="52823-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="52823-120">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-120">**Arguments**</span></span>

<span data-ttu-id="52823-121">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="52823-122">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-122">**Return Value**</span></span>

<span data-ttu-id="52823-123">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-123">The type of `value`.</span></span>

<span data-ttu-id="52823-124">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="52823-125">Power(值、指數)</span><span class="sxs-lookup"><span data-stu-id="52823-125">Power(value, exponent)</span></span>

<span data-ttu-id="52823-126">傳回指定的 `value` 結果至指定的 `exponent`。</span><span class="sxs-lookup"><span data-stu-id="52823-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="52823-127">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="52823-128">`Int32, Int64, Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="52823-129">`Int64`， `Double`，或`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="52823-130">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-130">**Return Value**</span></span>

<span data-ttu-id="52823-131">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-131">The type of `value`.</span></span>

<span data-ttu-id="52823-132">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="52823-133">Round(value)</span><span class="sxs-lookup"><span data-stu-id="52823-133">Round(value)</span></span>

<span data-ttu-id="52823-134">傳回 `value` 的整數部分，四捨五入成最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="52823-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="52823-135">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-135">**Arguments**</span></span>

<span data-ttu-id="52823-136">A `Single`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="52823-137">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-137">**Return Value**</span></span>

<span data-ttu-id="52823-138">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-138">The type of `value`.</span></span>

<span data-ttu-id="52823-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="52823-140">Round(值、數字)</span><span class="sxs-lookup"><span data-stu-id="52823-140">Round(value, digits)</span></span>

<span data-ttu-id="52823-141">傳回 `value`，四捨五入至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="52823-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="52823-142">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="52823-143">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="52823-144">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="52823-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="52823-145">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-145">**Return Value**</span></span>

<span data-ttu-id="52823-146">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-146">The type of `value`.</span></span>

<span data-ttu-id="52823-147">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="52823-148">Truncate(值、數字)</span><span class="sxs-lookup"><span data-stu-id="52823-148">Truncate(value, digits)</span></span>

<span data-ttu-id="52823-149">傳回 `value`，截斷至最接近的指定 `digits`。</span><span class="sxs-lookup"><span data-stu-id="52823-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="52823-150">**引數**</span><span class="sxs-lookup"><span data-stu-id="52823-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="52823-151">`Double` 或 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="52823-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="52823-152">`Int16` 或 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="52823-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="52823-153">**傳回值**</span><span class="sxs-lookup"><span data-stu-id="52823-153">**Return Value**</span></span>

<span data-ttu-id="52823-154">`value` 的類型。</span><span class="sxs-lookup"><span data-stu-id="52823-154">The type of `value`.</span></span>

<span data-ttu-id="52823-155">**範例**</span><span class="sxs-lookup"><span data-stu-id="52823-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="52823-156">如果提供 `null` 輸入，這些函式會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="52823-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="52823-157">Microsoft SQL Client Managed Provider 中提供了對等的功能。</span><span class="sxs-lookup"><span data-stu-id="52823-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="52823-158">如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="52823-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52823-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52823-159">See Also</span></span>  
 [<span data-ttu-id="52823-160">標準函式</span><span class="sxs-lookup"><span data-stu-id="52823-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
