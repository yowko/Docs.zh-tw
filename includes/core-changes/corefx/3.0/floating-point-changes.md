---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568241"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>更改了浮點格式和分析行為

浮點解析和格式設置行為（按<xref:System.Double>和<xref:System.Single>類型）現在符合 IEEE。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和早期<xref:System.Double.ToString%2A?displayProperty=nameWithType>版本中<xref:System.Single.ToString%2A?displayProperty=nameWithType>，使用 和<xref:System.Double.Parse%2A?displayProperty=nameWithType>進行<xref:System.Double.TryParse%2A?displayProperty=nameWithType>格式化<xref:System.Single.Parse%2A?displayProperty=nameWithType>，以及<xref:System.Single.TryParse%2A?displayProperty=nameWithType>使用 、和 進行解析，不符合 IEEE。 因此，無法保證值將隨行任何支援的標準或自訂格式字串。 對於某些輸入，嘗試分析格式化的值可能會失敗，而對於其他輸入，解析的值不等於原始值。

從 .NET Core 3.0 開始，解析和格式化操作符合 IEEE 754 標準。 這可確保 .NET 中的浮點類型的行為與 IEEE 相容語言（如 C#）的行為匹配。 有關詳細資訊，請參閱[.NET Core 3.0 博客文章中的浮點解析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

[.NET Core 3.0 博客文章中的浮點解析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的"對現有代碼的潛在影響"部分建議，如果觀察到行為更改與 .NET Core 2.2 應用程式相比，則更改代碼。 如果某些結果以前不正確，則可能無法使用解決方法。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
