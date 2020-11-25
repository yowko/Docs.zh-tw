---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031997"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>UriBuilder 屬性不再加上前置字元

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 不會再加上前置 `#` 字元，而且 <xref:System.UriBuilder.Query?displayProperty=nameWithType> `?` 如果其中一個字元已存在，就不會再加上前置字元。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 和 <xref:System.UriBuilder.Query?displayProperty=nameWithType> 屬性一律會 `#` 分別在 `?` 所儲存的值前面加上 or 字元。 `#` `?` 如果字串已經包含這些前導字元的其中一個，則此行為可能會在儲存的值中產生多個字元或多個字元。 例如，的值可能會 <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 變成 `##main` 。

從 .NET Core 1.0 開始，這些屬性不 `#` `?` 會再于預存值的前面加上字元（如果字串開頭已經有的話）。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

在設定屬性值時，您不再需要明確移除這些開頭的任何字元。 這在您附加值時特別有用，因為您不再需要移除附加的前置 `#` 或 `?` 每次。

例如，下列程式碼片段顯示 .NET Framework 和 .NET Core 之間的行為差異。

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- 在 .NET Framework 中，輸出為 `????one=1&two=2&three=3&four=4` 。
- 在 .NET Core 中，輸出為 `?one=1&two=2&three=3&four=4` 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
