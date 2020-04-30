---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595674"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>UriBuilder 屬性不再前面加上前置字元

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>不會再前面加`#`上前置<xref:System.UriBuilder.Query?displayProperty=nameWithType>字元，而且當其中`?`一個字元已存在時，不會再前面加上前置字元。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， <xref:System.UriBuilder.Fragment?displayProperty=nameWithType>和<xref:System.UriBuilder.Query?displayProperty=nameWithType>屬性一律會分別`#`在`?`所要儲存的值前面加上或字元。 如果字串已包含這些前置`#`字元`?`的其中一個，則此行為可能會在儲存的值中產生多個或字元。 例如，的值<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>可能會變成。 `##main`

從 .NET Core 1.0 開始，如果字串開頭已有一個`#`或`?`多個字元，這些屬性就不會再于預存值前面加上。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

在設定屬性值時，您不再需要明確地移除這些前置字元的任何一個。 當您要附加值時，這個方法特別有用，因為您不再需要移除前置`#`或`?`每次附加的。

例如，下列程式碼片段顯示 .NET Framework 和 .NET Core 之間的行為差異。

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- 在 .NET Framework 中，輸出為`????one=1&two=2&three=3&four=4`。
- 在 .NET Core 中，輸出是`?one=1&two=2&three=3&four=4`。

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
