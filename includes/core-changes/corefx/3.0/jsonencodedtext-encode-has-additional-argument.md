---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147584"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="30215-101">JsonEncodedText.編碼方法具有額外的JavaScriptEncoder參數</span><span class="sxs-lookup"><span data-stu-id="30215-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="30215-102">從 .NET Core 3.0 預覽<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>8 開始<xref:System.Text.Encodings.Web.JavaScriptEncoder>，這些方法包含一個可選參數。</span><span class="sxs-lookup"><span data-stu-id="30215-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30215-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="30215-103">Change description</span></span>

<span data-ttu-id="30215-104">.NET Core 3.0 包括一種新類型，外部參照：系統.Text.Json.JsonEncodedText.Encode%2A？顯示內容_名稱與類型>。</span><span class="sxs-lookup"><span data-stu-id="30215-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30215-105">從 .NET Core 3.0 預覽 8<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>開始，所有方法重載的簽名已更改為<xref:System.Text.Encodings.Web.JavaScriptEncoder>包含可選參數。</span><span class="sxs-lookup"><span data-stu-id="30215-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="30215-106">進行此更改是為了允許其他編碼器或自訂編碼器。</span><span class="sxs-lookup"><span data-stu-id="30215-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="30215-107">.NET Core `Encode` 3.0 預覽 7 中方法的簽名是：</span><span class="sxs-lookup"><span data-stu-id="30215-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="30215-108">在 .NET `Encode` Core 3.0 預覽版 8 和更高版本中的相同方法的簽名是：</span><span class="sxs-lookup"><span data-stu-id="30215-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="30215-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="30215-109">Version introduced</span></span>

<span data-ttu-id="30215-110">.NET 核心 3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="30215-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30215-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="30215-111">Recommended action</span></span>

<span data-ttu-id="30215-112">這只是二進位中斷更改;針對 .NET Core 3.0 預覽版或更高版本重新編譯將修復任何運行時問題。</span><span class="sxs-lookup"><span data-stu-id="30215-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="30215-113">類別</span><span class="sxs-lookup"><span data-stu-id="30215-113">Category</span></span>

<span data-ttu-id="30215-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="30215-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30215-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="30215-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
