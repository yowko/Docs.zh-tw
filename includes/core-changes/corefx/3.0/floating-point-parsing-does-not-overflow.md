---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032013"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>浮點數剖析作業不再失敗或擲回 >overflowexception

當浮點剖析方法 <xref:System.OverflowException> `false` 剖析的字串值超出 <xref:System.Single> 或浮點類型的範圍時，不會再擲回或傳回 <xref:System.Double> 。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和較早的版本中， <xref:System.Double.Parse%2A?displayProperty=nameWithType> 和 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 方法 <xref:System.OverflowException> 會針對其各自類型範圍之外的值擲回。 <xref:System.Double.TryParse%2A?displayProperty=nameWithType>和 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 方法會 `false` 針對超出範圍數值的字串表示傳回。

從 .net Core 3.0 開始， <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 當剖析超出範圍的數值字串時，、、和方法不會再失敗。 相反地， <xref:System.Double> 剖析方法 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 會傳回超過的值 <xref:System.Double.MaxValue?displayProperty=nameWithType> ，而且會 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 針對小於 <xref:System.Double.MinValue?displayProperty=nameWithType> 的值傳回。 同樣地， <xref:System.Single> 剖析方法 <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> 會傳回超過的值 <xref:System.Single.MaxValue?displayProperty=nameWithType> ，而且會 <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> 針對小於 <xref:System.Single.MinValue?displayProperty=nameWithType> 的值傳回。

這是為了改善 IEEE 754:2008 合規性所做的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更可能會影響您的程式碼，方法有兩種：

- 您的程式碼取決於在 <xref:System.OverflowException> 發生溢位時要執行的處理常式。 在此情況下，您應該移除 `catch` 語句，並將任何必要的程式碼放在 `If` 測試或是否為的語句中 <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` 。

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
