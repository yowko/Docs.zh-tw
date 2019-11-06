---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198375"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>浮點剖析作業不再失敗或擲回 OverflowException

浮點剖析方法不會再擲回 <xref:System.OverflowException>，或在剖析其數值超出 <xref:System.Single> 或 <xref:System.Double> 浮點類型範圍的字串時傳回 `false`。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和更早版本中，<xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法會針對超出其各自類型範圍的值擲回 <xref:System.OverflowException>。 <xref:System.Double.TryParse%2A?displayProperty=nameWithType> 和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會針對超出範圍的數值，傳回 `false` 的字串表示。

從 .NET Core 3.0 開始，在剖析超出範圍的數值字串時，<xref:System.Double.Parse%2A?displayProperty=nameWithType>、<xref:System.Double.TryParse%2A?displayProperty=nameWithType>、<xref:System.Single.Parse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法不會再失敗。 相反地，<xref:System.Double> 剖析方法會針對超過 <xref:System.Double.MaxValue?displayProperty=nameWithType>的值傳回 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>，而它們會針對小於 <xref:System.Double.MinValue?displayProperty=nameWithType>的值傳回 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>。 同樣地，<xref:System.Single> 剖析方法會針對超過 <xref:System.Single.MaxValue?displayProperty=nameWithType>的值傳回 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType>，而且它們會針對小於 <xref:System.Single.MinValue?displayProperty=nameWithType>的值傳回 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType>。

這是為了改善 IEEE 754:2008 合規性而進行的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更可能會影響您的程式碼，方法有兩種：

- 您的程式碼取決於要在發生溢位時執行 <xref:System.OverflowException> 的處理常式。 在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 語句中，以測試是否 `true`<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> 或 <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>。

- 您的程式碼假設浮點值不 `Infinity`。 在此情況下，您應該加入必要的程式碼，以檢查 `PositiveInfinity` 和 `NegativeInfinity`的浮點值。

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
