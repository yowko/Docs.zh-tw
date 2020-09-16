---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281291"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Vector2. Lerp 和 Vector4 的行為變更。 Lerp

的執行 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 已變更為正確地考慮浮點舍入錯誤。

#### <a name="change-description"></a>變更描述

之前 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 已實作為 `value1 + (value2 - value1) * amount` 。 不過，由於浮點舍入錯誤，在為時，此演算法不一定會傳回 `value2` `amount` `1.0f` 。

在 .NET 5.0 和更新版本中，執行會使用與相同的演算法 <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> ，也就是 `(value1 * (1.0f - amount)) + (value2 * amount)` 。 此演算法會正確地將舍入錯誤的帳戶提供給。 現在，當 `amount` 為時 `1.0f` ，結果會精確 `value2` 。 更新的演算法也可讓您在可用時，使用演算法自由地優化 <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> 。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 7

#### <a name="recommended-action"></a>建議的動作

不需要採取任何動作。 但是，如果您想要維護舊的行為，則可以 `Lerp` 使用先前的演算法來執行您自己的函式 `value1 + (value2 - value1) * amount` 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
