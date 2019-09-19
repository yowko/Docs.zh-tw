---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117120"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="daf49-101">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="daf49-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="daf49-102">從 .net Core 3.0 Preview 8 開始， <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>方法包含選擇性<xref:System.Text.Encodings.Web.JavaScriptEncoder>的引數。</span><span class="sxs-lookup"><span data-stu-id="daf49-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span> 

#### <a name="details"></a><span data-ttu-id="daf49-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="daf49-103">Details</span></span>

<span data-ttu-id="daf49-104">.NET Core 3.0 包含新的類型 x： JsonEncodedText。編碼% 2A？ displayProperty = Namewithtype> >。</span><span class="sxs-lookup"><span data-stu-id="daf49-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="daf49-105">從 .net Core 3.0 Preview 8 開始，所有<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>方法多載的簽章已變更為包含選擇性<xref:System.Text.Encodings.Web.JavaScriptEncoder>參數。</span><span class="sxs-lookup"><span data-stu-id="daf49-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="daf49-106">已進行這種變更，以允許不同或自訂的編碼器。</span><span class="sxs-lookup"><span data-stu-id="daf49-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="daf49-107">.Net Core 3.0 Preview 7 中的方法簽章為：`Encode`</span><span class="sxs-lookup"><span data-stu-id="daf49-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="daf49-108">.Net Core 3.0 Preview 8 `Encode`和更新版本中相同方法的簽章為：</span><span class="sxs-lookup"><span data-stu-id="daf49-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="daf49-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="daf49-109">Version introduced</span></span>

<span data-ttu-id="daf49-110">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="daf49-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="daf49-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="daf49-111">Recommended action</span></span>

<span data-ttu-id="daf49-112">這只是二進位的重大變更;針對 .NET Core 3.0 Preview 8 或更新版本進行重新編譯將會修正任何執行時間問題。</span><span class="sxs-lookup"><span data-stu-id="daf49-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="daf49-113">分類</span><span class="sxs-lookup"><span data-stu-id="daf49-113">Category</span></span>

<span data-ttu-id="daf49-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="daf49-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="daf49-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="daf49-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->