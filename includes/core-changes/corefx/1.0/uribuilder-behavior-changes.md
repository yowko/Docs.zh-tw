---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031997"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="0fc08-101">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="0fc08-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="0fc08-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 不會再加上前置 `#` 字元，而且 <xref:System.UriBuilder.Query?displayProperty=nameWithType> `?` 如果其中一個字元已存在，就不會再加上前置字元。</span><span class="sxs-lookup"><span data-stu-id="0fc08-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0fc08-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0fc08-103">Change description</span></span>

<span data-ttu-id="0fc08-104">在 .NET Framework 中， <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 和 <xref:System.UriBuilder.Query?displayProperty=nameWithType> 屬性一律會 `#` 分別在 `?` 所儲存的值前面加上 or 字元。</span><span class="sxs-lookup"><span data-stu-id="0fc08-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="0fc08-105">`#` `?` 如果字串已經包含這些前導字元的其中一個，則此行為可能會在儲存的值中產生多個字元或多個字元。</span><span class="sxs-lookup"><span data-stu-id="0fc08-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="0fc08-106">例如，的值可能會 <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> 變成 `##main` 。</span><span class="sxs-lookup"><span data-stu-id="0fc08-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="0fc08-107">從 .NET Core 1.0 開始，這些屬性不 `#` `?` 會再于預存值的前面加上字元（如果字串開頭已經有的話）。</span><span class="sxs-lookup"><span data-stu-id="0fc08-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0fc08-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0fc08-108">Version introduced</span></span>

<span data-ttu-id="0fc08-109">1.0</span><span class="sxs-lookup"><span data-stu-id="0fc08-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0fc08-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0fc08-110">Recommended action</span></span>

<span data-ttu-id="0fc08-111">在設定屬性值時，您不再需要明確移除這些開頭的任何字元。</span><span class="sxs-lookup"><span data-stu-id="0fc08-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="0fc08-112">這在您附加值時特別有用，因為您不再需要移除附加的前置 `#` 或 `?` 每次。</span><span class="sxs-lookup"><span data-stu-id="0fc08-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="0fc08-113">例如，下列程式碼片段顯示 .NET Framework 和 .NET Core 之間的行為差異。</span><span class="sxs-lookup"><span data-stu-id="0fc08-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="0fc08-114">在 .NET Framework 中，輸出為 `????one=1&two=2&three=3&four=4` 。</span><span class="sxs-lookup"><span data-stu-id="0fc08-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="0fc08-115">在 .NET Core 中，輸出為 `?one=1&two=2&three=3&four=4` 。</span><span class="sxs-lookup"><span data-stu-id="0fc08-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="0fc08-116">類別</span><span class="sxs-lookup"><span data-stu-id="0fc08-116">Category</span></span>

<span data-ttu-id="0fc08-117">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="0fc08-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0fc08-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0fc08-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
