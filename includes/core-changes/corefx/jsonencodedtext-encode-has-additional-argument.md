---
ms.openlocfilehash: 377f22409558c21d1c57f6214c13572dedf9e419
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217070"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText 方法有額外的 JavaScriptEncoder 引數

從 .net Core 3.0 Preview 8 開始， <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>方法包含選擇性<xref:System.Text.Encodings.Web.JavaScriptEncoder>的引數。

#### <a name="details"></a>詳細資料

.NET Core 3.0 包含新的類型 x： JsonEncodedText。編碼% 2A？ displayProperty = Namewithtype> >。 從 .net Core 3.0 Preview 8 開始，所有<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>方法多載的簽章已變更為包含選擇性<xref:System.Text.Encodings.Web.JavaScriptEncoder>參數。 已進行這種變更，以允許不同或自訂的編碼器。

.Net Core 3.0 Preview 7 中的方法簽章為：`Encode`

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

.Net Core 3.0 Preview 8 `Encode`和更新版本中相同方法的簽章為：

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

#### <a name="category"></a>分類

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
