---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721063"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>浮點格式設定和剖析行為已變更

浮點剖析和格式化行為（依 <xref:System.Double> 和 <xref:System.Single> 類型）現在是與 IEEE 相容。

#### <a name="change-description"></a>變更描述

在 .net Core 2.2 和更早版本中，使用和進行的格式設定 <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType> 和以 <xref:System.Double.Parse%2A?displayProperty=nameWithType> 、 <xref:System.Double.TryParse%2A?displayProperty=nameWithType> 、 <xref:System.Single.Parse%2A?displayProperty=nameWithType> 和進行剖析並 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 不符合 IEEE 規範。 因此，無法保證值會與任何支援的標準或自訂格式字串往返。 對於某些輸入，剖析格式化值的嘗試可能會失敗，而針對其他專案，則剖析的值不等於原始值。

從 .NET Core 3.0 開始，剖析和格式化作業與 IEEE 754 相容。 這可確保 .NET 中浮點類型的行為符合與 IEEE 相容的語言（例如 c #）的行為。 如需詳細資訊，請參閱[.Net Core 3.0 中的浮點剖析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)文章。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

[.Net core 3.0 中的浮點剖析和格式化改善](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的「對現有程式碼的潛在影響」一節會建議您對程式碼所做的變更，如果您在與 .net Core 2.2 應用程式相比，觀察到行為的變更，這牽涉到使用不同的標準或自訂格式字串來強制執行所需的行為。 某些結果若先前不正確，可能不會有因應措施。

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
