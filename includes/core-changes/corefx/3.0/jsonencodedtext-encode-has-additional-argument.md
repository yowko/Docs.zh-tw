---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021598"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="2c42e-101">JsonEncodedText.編碼方法具有額外的JAVAScriptEncoder參數</span><span class="sxs-lookup"><span data-stu-id="2c42e-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="2c42e-102">從 .NET Core 3.0 預覽<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>8 開始<xref:System.Text.Encodings.Web.JavaScriptEncoder>,這些方法包含一個可選參數。</span><span class="sxs-lookup"><span data-stu-id="2c42e-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2c42e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="2c42e-103">Change description</span></span>

<span data-ttu-id="2c42e-104">.NET Core 3.0 包括一種新類型,外部參照:系統.Text.Json.JsonEncodedText.Encode%2A?顯示屬性_名稱與類型>。</span><span class="sxs-lookup"><span data-stu-id="2c42e-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c42e-105">從 .NET Core 3.0<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>預覽 8 開始,所有方法重<xref:System.Text.Encodings.Web.JavaScriptEncoder>載的簽名已更改為 包含可選參數。</span><span class="sxs-lookup"><span data-stu-id="2c42e-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="2c42e-106">進行此更改是為了允許其他編碼器或自定義編碼器。</span><span class="sxs-lookup"><span data-stu-id="2c42e-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="2c42e-107">.NET Core `Encode` 3.0 預覽 7 中方法的簽名是:</span><span class="sxs-lookup"><span data-stu-id="2c42e-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="2c42e-108">在 .NET `Encode` Core 3.0 預覽版 8 和更高版本中的相同方法的簽名是:</span><span class="sxs-lookup"><span data-stu-id="2c42e-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="2c42e-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="2c42e-109">Version introduced</span></span>

<span data-ttu-id="2c42e-110">.NET 核心 3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="2c42e-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2c42e-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2c42e-111">Recommended action</span></span>

<span data-ttu-id="2c42e-112">這隻是二進位中斷更改;針對 .NET Core 3.0 預覽版或更高版本重新編譯將修復任何運行時問題。</span><span class="sxs-lookup"><span data-stu-id="2c42e-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="2c42e-113">類別</span><span class="sxs-lookup"><span data-stu-id="2c42e-113">Category</span></span>

<span data-ttu-id="2c42e-114">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="2c42e-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2c42e-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2c42e-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
