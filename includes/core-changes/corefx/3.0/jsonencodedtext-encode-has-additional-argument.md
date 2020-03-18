---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147584"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText.編碼方法具有額外的JavaScriptEncoder參數

從 .NET Core 3.0 預覽<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>8 開始<xref:System.Text.Encodings.Web.JavaScriptEncoder>，這些方法包含一個可選參數。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 包括一種新類型，外部參照：系統.Text.Json.JsonEncodedText.Encode%2A？顯示內容_名稱與類型>。 從 .NET Core 3.0 預覽 8<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>開始，所有方法重載的簽名已更改為<xref:System.Text.Encodings.Web.JavaScriptEncoder>包含可選參數。 進行此更改是為了允許其他編碼器或自訂編碼器。

.NET Core `Encode` 3.0 預覽 7 中方法的簽名是：

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

在 .NET `Encode` Core 3.0 預覽版 8 和更高版本中的相同方法的簽名是：

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a>介紹的版本

.NET 核心 3.0 預覽 8

#### <a name="recommended-action"></a>建議的動作

這只是二進位中斷更改;針對 .NET Core 3.0 預覽版或更高版本重新編譯將修復任何運行時問題。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
