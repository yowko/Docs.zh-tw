---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302700"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> 現在一律會 <xref:System.NotSupportedException> 針對不支援的類型參數擲回。

#### <a name="change-description"></a>變更描述

先前的成員 <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> 在不 `T` [受支援的類型](#unsupported-types)時，不一定會擲回。 由於支援硬體加速的程式碼路徑，因此不一定會擲回例外狀況。 例如， `Vector<bool> + Vector<bool>` 會傳回， `default` 而不是在沒有硬體加速的平臺上擲回例外狀況，例如 ARM32。 針對不支援的類型， <xref:System.Numerics.Vector%601> 成員會在不同的平臺和硬體設定之間呈現不一致的行為。

從 .NET 5.0 開始， <xref:System.Numerics.Vector%601> 當不是支援的類型時，成員一律 <xref:System.NotSupportedException> 會在所有硬體設定上擲回 `T` 。

##### <a name="unsupported-types"></a>不支援的類型

的類型參數支援的類型 <xref:System.Numerics.Vector%601> 為：

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

請勿針對的型別參數使用不支援的類型 <xref:System.Numerics.Vector%601> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Numerics.Vector%601?displayProperty=fullName> 及其所有成員

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
