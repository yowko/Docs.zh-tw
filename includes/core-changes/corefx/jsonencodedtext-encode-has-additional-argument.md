---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237315"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText 方法有額外的 JavaScriptEncoder 引數

從 .NET Core 3.0 Preview 8 開始，@no__t 0 的方法包含選擇性的 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 引數。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 包含新的類型 x： JsonEncodedText。編碼% 2A？ displayProperty = Namewithtype> >。 從 .NET Core 3.0 Preview 8 開始，所有 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 方法多載的簽章已變更為包含選擇性的 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 參數。 已進行這種變更，以允許不同或自訂的編碼器。

.NET Core 3.0 Preview 7 中 `Encode` 方法的簽章是：

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

.NET Core 3.0 Preview 8 和更新版本中相同 `Encode` 方法的簽章為：

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

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

這只是二進位的重大變更;針對 .NET Core 3.0 Preview 8 或更新版本進行重新編譯將會修正任何執行時間問題。

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>受影響的 API

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
