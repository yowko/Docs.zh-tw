---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595674"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="d2adc-101">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="d2adc-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="d2adc-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType>不會再前面加`#`上前置<xref:System.UriBuilder.Query?displayProperty=nameWithType>字元，而且當其中`?`一個字元已存在時，不會再前面加上前置字元。</span><span class="sxs-lookup"><span data-stu-id="d2adc-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d2adc-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d2adc-103">Change description</span></span>

<span data-ttu-id="d2adc-104">在 .NET Framework 中， <xref:System.UriBuilder.Fragment?displayProperty=nameWithType>和<xref:System.UriBuilder.Query?displayProperty=nameWithType>屬性一律會分別`#`在`?`所要儲存的值前面加上或字元。</span><span class="sxs-lookup"><span data-stu-id="d2adc-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="d2adc-105">如果字串已包含這些前置`#`字元`?`的其中一個，則此行為可能會在儲存的值中產生多個或字元。</span><span class="sxs-lookup"><span data-stu-id="d2adc-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="d2adc-106">例如，的值<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>可能會變成。 `##main`</span><span class="sxs-lookup"><span data-stu-id="d2adc-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="d2adc-107">從 .NET Core 1.0 開始，如果字串開頭已有一個`#`或`?`多個字元，這些屬性就不會再于預存值前面加上。</span><span class="sxs-lookup"><span data-stu-id="d2adc-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2adc-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d2adc-108">Version introduced</span></span>

<span data-ttu-id="d2adc-109">1.0</span><span class="sxs-lookup"><span data-stu-id="d2adc-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2adc-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d2adc-110">Recommended action</span></span>

<span data-ttu-id="d2adc-111">在設定屬性值時，您不再需要明確地移除這些前置字元的任何一個。</span><span class="sxs-lookup"><span data-stu-id="d2adc-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="d2adc-112">當您要附加值時，這個方法特別有用，因為您不再需要移除前置`#`或`?`每次附加的。</span><span class="sxs-lookup"><span data-stu-id="d2adc-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="d2adc-113">例如，下列程式碼片段顯示 .NET Framework 和 .NET Core 之間的行為差異。</span><span class="sxs-lookup"><span data-stu-id="d2adc-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="d2adc-114">在 .NET Framework 中，輸出為`????one=1&two=2&three=3&four=4`。</span><span class="sxs-lookup"><span data-stu-id="d2adc-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="d2adc-115">在 .NET Core 中，輸出是`?one=1&two=2&three=3&four=4`。</span><span class="sxs-lookup"><span data-stu-id="d2adc-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="d2adc-116">類別</span><span class="sxs-lookup"><span data-stu-id="d2adc-116">Category</span></span>

<span data-ttu-id="d2adc-117">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="d2adc-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2adc-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d2adc-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
