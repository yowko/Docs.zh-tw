---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568173"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="e5902-101">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="e5902-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="e5902-102">從 .NET Core 3.0 Preview 8 開始，<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 方法包含選擇性的 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 引數。</span><span class="sxs-lookup"><span data-stu-id="e5902-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e5902-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e5902-103">Change description</span></span>

<span data-ttu-id="e5902-104">.NET Core 3.0 包含新的類型 x： JsonEncodedText。編碼% 2A？ displayProperty = Namewithtype> >。</span><span class="sxs-lookup"><span data-stu-id="e5902-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e5902-105">從 .NET Core 3.0 Preview 8 開始，所有 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 方法多載的簽章已變更為包含選擇性的 <xref:System.Text.Encodings.Web.JavaScriptEncoder> 參數。</span><span class="sxs-lookup"><span data-stu-id="e5902-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="e5902-106">已進行這種變更，以允許不同或自訂的編碼器。</span><span class="sxs-lookup"><span data-stu-id="e5902-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="e5902-107">.NET Core 3.0 Preview 7 中 `Encode` 方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="e5902-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="e5902-108">.NET Core 3.0 Preview 8 和更新版本中相同 `Encode` 方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="e5902-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="e5902-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e5902-109">Version introduced</span></span>

<span data-ttu-id="e5902-110">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e5902-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5902-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e5902-111">Recommended action</span></span>

<span data-ttu-id="e5902-112">這只是二進位的重大變更;針對 .NET Core 3.0 Preview 8 或更新版本進行重新編譯將會修正任何執行時間問題。</span><span class="sxs-lookup"><span data-stu-id="e5902-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="e5902-113">Category</span><span class="sxs-lookup"><span data-stu-id="e5902-113">Category</span></span>

<span data-ttu-id="e5902-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e5902-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5902-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e5902-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
