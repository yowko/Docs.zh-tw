---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302700"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector 一律會擲回 \<T> 不支援之類型的 NotSupportedException

<xref:System.Numerics.Vector%601?displayProperty=nameWithType><xref:System.NotSupportedException>針對不支援的型別參數，現在一律會擲回。

#### <a name="change-description"></a>變更描述

先前，的成員 <xref:System.Numerics.Vector%601> 不一定會在不 <xref:System.NotSupportedException> 支援的型別時擲回 `T` 。 [unsupported type](#unsupported-types) 不一定會擲回例外狀況，因為支援硬體加速的程式碼路徑。 例如， `Vector<bool> + Vector<bool>` 會傳回， `default` 而不是在沒有硬體加速的平臺上擲回例外狀況，例如 ARM32。 對於不支援的類型， <xref:System.Numerics.Vector%601> 成員會在不同的平臺和硬體設定中呈現不一致的行為。

從 .NET 5.0 開始， <xref:System.Numerics.Vector%601> 當不是 <xref:System.NotSupportedException> `T` 受支援的類型時，成員一律會在所有硬體設定上擲回。

##### <a name="unsupported-types"></a>不支援的類型

的類型參數支援的類型為 <xref:System.Numerics.Vector%601> ：

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

但支援的類型尚未變更，但未來可能會變更。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

請勿針對的類型參數使用不支援的類型 <xref:System.Numerics.Vector%601> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Numerics.Vector%601?displayProperty=fullName>及其所有成員

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
