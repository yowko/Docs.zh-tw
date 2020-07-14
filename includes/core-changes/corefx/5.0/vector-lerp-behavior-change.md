---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281291"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Vector2 的行為變更。 Lerp 和 Vector4. Lerp

的執行 <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 變更為正確地考慮浮點舍入錯誤。

#### <a name="change-description"></a>變更描述

之前， <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> 和實 <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> 作為 `value1 + (value2 - value1) * amount` 。 不過，由於浮點舍入錯誤，當為時，此演算法不一定會傳回 `value2` `amount` `1.0f` 。

在 .NET 5.0 和更新版本中，此實作為使用與相同的演算法 <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> ，也就是 `(value1 * (1.0f - amount)) + (value2 * amount)` 。 此演算法會正確地為舍入錯誤提供帳戶。 現在，當 `amount` 是時 `1.0f` ，結果會精確 `value2` 。 更新的演算法也可以讓演算法在可用時，使用來自由優化 <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> 。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 7

#### <a name="recommended-action"></a>建議的動作

不需要採取任何動作。 不過，如果您想要保留舊的行為，您可以執行自己的函式， `Lerp` 以使用先前的 `value1 + (value2 - value1) * amount` 演算法。

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
