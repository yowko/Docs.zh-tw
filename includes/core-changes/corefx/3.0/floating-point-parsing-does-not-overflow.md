---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568193"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>浮點分析操作不再失敗或引發溢出異常

浮點解析方法在解析其<xref:System.OverflowException>數值超出`false`<xref:System.Single>或<xref:System.Double>浮點類型範圍的字串時不再引發 或返回。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和<xref:System.Double.Parse%2A?displayProperty=nameWithType>早期<xref:System.Single.Parse%2A?displayProperty=nameWithType>版本中，和<xref:System.OverflowException>方法將為其各自類型範圍之外的值引發 。 和<xref:System.Double.TryParse%2A?displayProperty=nameWithType><xref:System.Single.TryParse%2A?displayProperty=nameWithType>方法返回`false`範圍外數值的字串表示形式。

從 .NET Core 3.0 <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>開始<xref:System.Single.Parse%2A?displayProperty=nameWithType>， <xref:System.Single.TryParse%2A?displayProperty=nameWithType> ， 和 方法在分析範圍外的數位字串時不再失敗。 <xref:System.Double>相反，分析方法返回<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>超過<xref:System.Double.MaxValue?displayProperty=nameWithType>的值，並且返回<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>小於<xref:System.Double.MinValue?displayProperty=nameWithType>的值。 <xref:System.Single>同樣，分析方法返回<xref:System.Single.PositiveInfinity?displayProperty=nameWithType>超過<xref:System.Single.MaxValue?displayProperty=nameWithType>的值，並且返回<xref:System.Single.NegativeInfinity?displayProperty=nameWithType>小於<xref:System.Single.MinValue?displayProperty=nameWithType>的值。

此更改是為了改進 IEEE 754：2008 合規性。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

此更改可以通過兩種方式之一影響代碼：

- 代碼取決於在發生溢出時<xref:System.OverflowException>要執行的處理常式。 在這種情況下，應刪除 語句`catch`，並將任何必要的代碼放在測試 是否`If`<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>為<xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>`true`的語句中。

- 您的代碼假定浮點值不是`Infinity`。 在這種情況下，應添加必要的代碼來檢查 和`PositiveInfinity``NegativeInfinity`的浮點值。

#### <a name="category"></a>類別

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
