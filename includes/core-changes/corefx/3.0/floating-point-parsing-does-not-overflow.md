---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720974"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>浮點剖析作業不再失敗或擲回 OverflowException

<xref:System.OverflowException> `false` 當它們剖析的字串的數值超出 <xref:System.Single> 或 <xref:System.Double> 浮點數類型的範圍時，浮點剖析方法不會再擲回或傳回。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和更早版本中， <xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法 <xref:System.OverflowException> 會針對超出其各自類型範圍的值擲回。 <xref:System.Double.TryParse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會 `false` 針對超出範圍的數值，傳回字串表示。

從 .net Core 3.0 開始，在 <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 剖析超出範圍的數值字串時，、、和方法不會再失敗。 相反地， <xref:System.Double> 剖析方法 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 會針對超過的值傳回 <xref:System.Double.MaxValue?displayProperty=nameWithType> ，而它們 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 會針對小於的值傳回 <xref:System.Double.MinValue?displayProperty=nameWithType> 。 同樣地， <xref:System.Single> 剖析方法 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> 會針對超過的值傳回 <xref:System.Single.MaxValue?displayProperty=nameWithType> ，而它們 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> 會針對小於的值傳回 <xref:System.Single.MinValue?displayProperty=nameWithType> 。

這是為了改善 IEEE 754:2008 合規性而進行的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更可能會影響您的程式碼，方法有兩種：

- 您的程式碼相依于的處理常式， <xref:System.OverflowException> 以便在發生溢位時執行。 在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 測試是否為的語句中 <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` 。

- 您的程式碼假設浮點值不是 `Infinity` 。 在此情況下，您應該加入必要的程式碼，以檢查和的浮點 `PositiveInfinity` 值 `NegativeInfinity` 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
