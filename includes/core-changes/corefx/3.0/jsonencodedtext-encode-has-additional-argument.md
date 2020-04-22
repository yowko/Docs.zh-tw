---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021598"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText.編碼方法具有額外的JAVAScriptEncoder參數

從 .NET Core 3.0 預覽<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>8 開始<xref:System.Text.Encodings.Web.JavaScriptEncoder>,這些方法包含一個可選參數。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 包括一種新類型,外部參照:系統.Text.Json.JsonEncodedText.Encode%2A?顯示屬性_名稱與類型>。 從 .NET Core 3.0<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>預覽 8 開始,所有方法重<xref:System.Text.Encodings.Web.JavaScriptEncoder>載的簽名已更改為 包含可選參數。 進行此更改是為了允許其他編碼器或自定義編碼器。

.NET Core `Encode` 3.0 預覽 7 中方法的簽名是:

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

在 .NET `Encode` Core 3.0 預覽版 8 和更高版本中的相同方法的簽名是:

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

這隻是二進位中斷更改;針對 .NET Core 3.0 預覽版或更高版本重新編譯將修復任何運行時問題。

#### <a name="category"></a>類別

核心 .NET 函式庫

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
