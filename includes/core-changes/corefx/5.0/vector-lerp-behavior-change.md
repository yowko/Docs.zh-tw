---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281291"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="4aae1-101">Vector2 的行為變更。 Lerp 和 Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="4aae1-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="4aae1-102">的執行 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 變更為正確地考慮浮點舍入錯誤。</span><span class="sxs-lookup"><span data-stu-id="4aae1-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4aae1-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="4aae1-103">Change description</span></span>

<span data-ttu-id="4aae1-104">之前， <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和實 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 作為 `value1 + (value2 - value1) * amount` 。</span><span class="sxs-lookup"><span data-stu-id="4aae1-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="4aae1-105">不過，由於浮點舍入錯誤，當為時，此演算法不一定會傳回 `value2` `amount` `1.0f` 。</span><span class="sxs-lookup"><span data-stu-id="4aae1-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="4aae1-106">在 .NET 5.0 和更新版本中，此實作為使用與相同的演算法 <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> ，也就是 `(value1 * (1.0f - amount)) + (value2 * amount)` 。</span><span class="sxs-lookup"><span data-stu-id="4aae1-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="4aae1-107">此演算法會正確地為舍入錯誤提供帳戶。</span><span class="sxs-lookup"><span data-stu-id="4aae1-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="4aae1-108">現在，當 `amount` 是時 `1.0f` ，結果會精確 `value2` 。</span><span class="sxs-lookup"><span data-stu-id="4aae1-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="4aae1-109">更新的演算法也可以讓演算法在可用時，使用來自由優化 <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4aae1-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4aae1-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4aae1-110">Version introduced</span></span>

<span data-ttu-id="4aae1-111">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="4aae1-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4aae1-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4aae1-112">Recommended action</span></span>

<span data-ttu-id="4aae1-113">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="4aae1-113">No action is necessary.</span></span> <span data-ttu-id="4aae1-114">不過，如果您想要保留舊的行為，您可以執行自己的函式， `Lerp` 以使用先前的 `value1 + (value2 - value1) * amount` 演算法。</span><span class="sxs-lookup"><span data-stu-id="4aae1-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="4aae1-115">類別</span><span class="sxs-lookup"><span data-stu-id="4aae1-115">Category</span></span>

<span data-ttu-id="4aae1-116">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="4aae1-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4aae1-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4aae1-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
