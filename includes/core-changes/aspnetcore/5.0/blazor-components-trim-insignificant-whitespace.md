---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174255"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="d177e-101">Blazor：在編譯時期從元件修剪的空白空白字元</span><span class="sxs-lookup"><span data-stu-id="d177e-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="d177e-102">從 ASP.NET Core 5.0 Preview 7 開始，Razor 編譯器會在編譯時期 (*razor*檔案) 中省略 Blazor 元件中的空白空白字元。</span><span class="sxs-lookup"><span data-stu-id="d177e-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="d177e-103">如需討論，請參閱 issue [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568)。</span><span class="sxs-lookup"><span data-stu-id="d177e-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d177e-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d177e-104">Version introduced</span></span>

<span data-ttu-id="d177e-105">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="d177e-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d177e-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d177e-106">Old behavior</span></span>

<span data-ttu-id="d177e-107">在3.x 版的 Blazor 伺服器和 Blazor WebAssembly 中，在元件的原始程式碼中會接受空白字元。</span><span class="sxs-lookup"><span data-stu-id="d177e-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="d177e-108">只有空白字元的文位元組點會在瀏覽器的檔物件模型 (DOM) 中呈現，即使沒有視覺效果也一樣。</span><span class="sxs-lookup"><span data-stu-id="d177e-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="d177e-109">請考慮下列 Blazor 元件程式碼：</span><span class="sxs-lookup"><span data-stu-id="d177e-109">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="d177e-110">上述範例會呈現兩個空白字元節點：</span><span class="sxs-lookup"><span data-stu-id="d177e-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="d177e-111">在程式 `@foreach` 代碼區塊之外。</span><span class="sxs-lookup"><span data-stu-id="d177e-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="d177e-112">圍繞 `<li>` 元素。</span><span class="sxs-lookup"><span data-stu-id="d177e-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="d177e-113">在 `@item.Text` 輸出周圍。</span><span class="sxs-lookup"><span data-stu-id="d177e-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="d177e-114">包含100專案的清單會產生402個空白節點。</span><span class="sxs-lookup"><span data-stu-id="d177e-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="d177e-115">這不是所有呈現的節點一半，即使空白節點都不會影響轉譯的輸出。</span><span class="sxs-lookup"><span data-stu-id="d177e-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="d177e-116">為元件轉譯靜態 HTML 時，不會保留標記內的空白字元。</span><span class="sxs-lookup"><span data-stu-id="d177e-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="d177e-117">例如，請參閱下列元件的來源：</span><span class="sxs-lookup"><span data-stu-id="d177e-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="d177e-118">不會保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="d177e-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="d177e-119">預先呈現的輸出為：</span><span class="sxs-lookup"><span data-stu-id="d177e-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="d177e-120">新的行為</span><span class="sxs-lookup"><span data-stu-id="d177e-120">New behavior</span></span>

<span data-ttu-id="d177e-121">除非 `@preservewhitespace` 指示詞與值搭配使用 `true` ，否則會移除空白字元節點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d177e-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="d177e-122">是元素內的前置或尾端。</span><span class="sxs-lookup"><span data-stu-id="d177e-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="d177e-123">是參數內的開頭或結尾 `RenderFragment` 。</span><span class="sxs-lookup"><span data-stu-id="d177e-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="d177e-124">例如，將子內容傳遞至另一個元件。</span><span class="sxs-lookup"><span data-stu-id="d177e-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="d177e-125">在 c # 程式碼區塊之前或後面 `@if` ，例如和 `@foreach` 。</span><span class="sxs-lookup"><span data-stu-id="d177e-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d177e-126">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d177e-126">Reason for change</span></span>

<span data-ttu-id="d177e-127">ASP.NET Core 5.0 中的 Blazor 目標是要改善轉譯和比較的效能。</span><span class="sxs-lookup"><span data-stu-id="d177e-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="d177e-128">無意義的空白字元樹狀節點在基準測試中耗用最多40% 的轉譯時間。</span><span class="sxs-lookup"><span data-stu-id="d177e-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d177e-129">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d177e-129">Recommended action</span></span>

<span data-ttu-id="d177e-130">在大部分情況下，轉譯之元件的視覺化配置不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="d177e-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="d177e-131">不過，使用類似的 CSS 規則時，移除空白字元可能會影響轉譯的輸出 `white-space: pre` 。</span><span class="sxs-lookup"><span data-stu-id="d177e-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="d177e-132">若要停用此效能優化並保留空白字元，請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="d177e-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="d177e-133">在 razor 檔案頂端新增指示詞 `@preservewhitespace true` ， *.razor*以將喜好設定套用至特定元件。</span><span class="sxs-lookup"><span data-stu-id="d177e-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="d177e-134">在 `@preservewhitespace true` *_Imports razor*檔案內加入指示詞，以將喜好設定套用到整個子目錄或整個專案。</span><span class="sxs-lookup"><span data-stu-id="d177e-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="d177e-135">在大部分情況下，不需要採取任何動作，因為應用程式通常會繼續正常運作 (但) 更快。</span><span class="sxs-lookup"><span data-stu-id="d177e-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="d177e-136">如果空白字元的移除會導致特定元件發生任何問題，請 `@preservewhitespace true` 在該元件中使用來停用此優化。</span><span class="sxs-lookup"><span data-stu-id="d177e-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="d177e-137">類別</span><span class="sxs-lookup"><span data-stu-id="d177e-137">Category</span></span>

<span data-ttu-id="d177e-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d177e-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d177e-139">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d177e-139">Affected APIs</span></span>

<span data-ttu-id="d177e-140">無</span><span class="sxs-lookup"><span data-stu-id="d177e-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
