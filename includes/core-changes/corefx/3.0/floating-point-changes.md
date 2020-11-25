---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032012"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>浮點數格式化和剖析行為已變更

和類型)  (的浮點剖析和格式化 <xref:System.Double> 行為 <xref:System.Single> 現在符合 IEEE 標準。

#### <a name="change-description"></a>變更描述

在 .net Core 2.2 及更早版本中，使用和進行格式化， <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType> 並使用、、和進行剖析，並 <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 不符合 IEEE 規範。 如此一來，就無法保證某個值會往返任何支援的標準或自訂格式字串。 針對某些輸入，嘗試剖析格式化的值可能會失敗，而針對其他輸入，剖析的值不等於原始值。

從 .NET Core 3.0 開始，剖析和格式化作業符合 IEEE 754 規範。 這可確保 .NET 中的浮點類型行為符合符合 IEEE 標準的語言，例如 c #。 如需詳細資訊，請參閱 [.Net Core 3.0 blog 文章中的浮點剖析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

[.Net core 3.0 的浮點剖析和格式化增強功能](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的「對現有程式碼的潛在影響」一節會建議您變更程式碼，如果您在與 .net core 2.2 應用程式相較之下觀察到行為有所改變，則需要使用不同的標準或自訂格式字串來強制執行所需的行為。 如果先前的結果不正確，則可能無法解決此問題。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
