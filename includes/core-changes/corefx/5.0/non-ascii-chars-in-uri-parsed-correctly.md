---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720180"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>在 Unix 上正確剖析非 ASCII 字元的 URI 路徑

修正了類別中的 bug <xref:System.Uri?displayProperty=fullName> ，讓包含非 ASCII 字元的絕對 URI 路徑現在在 Unix 平臺上正確地進行剖析。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，包含非 ASCII 字元的絕對 URI 路徑在 Unix 平臺上不正確地剖析，而且會複製路徑的區段。  (絕對路徑是以 "/" 開頭的路徑。 ) 已修正 .NET 5.0 的剖析問題。 如果您從舊版的 .NET 移至 .NET 5.0 或更新版本，則會取得 <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> 、 <xref:System.Uri.ToString?displayProperty=nameWithType> 和其他成員所產生的不同值 <xref:System.Uri> 。

在 Unix 上執行時，請考慮下列程式碼的輸出。

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

先前 .NET 版本的輸出：

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

.NET 5.0 或更新版本的輸出：

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="recommended-action"></a>建議的動作

如果您有需要的程式碼，以及重複路徑區段的帳戶，您可以移除該程式碼。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
