---
title: 重大變更： Vector2. Lerp 和 Vector4 的行為變更。 Lerp
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 Vector2. Lerp 和 Vector4. Lerp 的執行變更為正確地考慮浮點舍入錯誤。
ms.date: 11/01/2020
ms.openlocfilehash: 8e363a559dba8b7563c40637c47f101d59951216
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760469"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="de982-103">Vector2. Lerp 和 Vector4 的行為變更。 Lerp</span><span class="sxs-lookup"><span data-stu-id="de982-103">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="de982-104">的執行 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 已變更為正確地考慮浮點舍入錯誤。</span><span class="sxs-lookup"><span data-stu-id="de982-104">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

## <a name="change-description"></a><span data-ttu-id="de982-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="de982-105">Change description</span></span>

<span data-ttu-id="de982-106">之前 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 已實作為 `value1 + (value2 - value1) * amount` 。</span><span class="sxs-lookup"><span data-stu-id="de982-106">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="de982-107">不過，由於浮點舍入錯誤，在為時，此演算法不一定會傳回 `value2` `amount` `1.0f` 。</span><span class="sxs-lookup"><span data-stu-id="de982-107">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="de982-108">在 .NET 5.0 和更新版本中，執行會使用與相同的演算法 <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> ，也就是 `(value1 * (1.0f - amount)) + (value2 * amount)` 。</span><span class="sxs-lookup"><span data-stu-id="de982-108">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="de982-109">此演算法會正確地將舍入錯誤的帳戶提供給。</span><span class="sxs-lookup"><span data-stu-id="de982-109">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="de982-110">現在，當 `amount` 為時 `1.0f` ，結果會精確 `value2` 。</span><span class="sxs-lookup"><span data-stu-id="de982-110">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="de982-111">更新的演算法也可讓您在可用時，使用演算法自由地優化 <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="de982-111">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="de982-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="de982-112">Version introduced</span></span>

<span data-ttu-id="de982-113">5.0</span><span class="sxs-lookup"><span data-stu-id="de982-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="de982-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="de982-114">Recommended action</span></span>

<span data-ttu-id="de982-115">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="de982-115">No action is necessary.</span></span> <span data-ttu-id="de982-116">但是，如果您想要維護舊的行為，則可以 `Lerp` 使用先前的演算法來執行您自己的函式 `value1 + (value2 - value1) * amount` 。</span><span class="sxs-lookup"><span data-stu-id="de982-116">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="de982-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="de982-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
