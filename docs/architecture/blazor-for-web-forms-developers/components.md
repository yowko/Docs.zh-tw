---
title: 使用建立可重複使用的 UI 元件Blazor
description: 瞭解如何使用建立可重複使用的 UI 元件 Blazor ，以及它們與 ASP.NET Web form 控制項之間的比較。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: 9577fc916bb11783b885b2641242820865c0b115
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173335"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="56882-103">使用建立可重複使用的 UI 元件Blazor</span><span class="sxs-lookup"><span data-stu-id="56882-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="56882-104">ASP.NET Web form 的其中一個很棒的東西，就是它可以將可重複使用的使用者介面 (UI) 程式碼片段封裝成可重複使用的 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="56882-105">您可以使用 *.ascx*檔案，在標記中定義自訂使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="56882-106">您也可以使用完整的設計工具支援，在程式碼中建立精緻的伺服器控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-106">You can also build elaborate server controls in code with full designer support.</span></span>

Blazor<span data-ttu-id="56882-107">也支援透過*元件*的 UI 封裝。</span><span class="sxs-lookup"><span data-stu-id="56882-107"> also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="56882-108">元件：</span><span class="sxs-lookup"><span data-stu-id="56882-108">A component:</span></span>

- <span data-ttu-id="56882-109">是獨立的 UI 區塊。</span><span class="sxs-lookup"><span data-stu-id="56882-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="56882-110">會維護自己的狀態和轉譯邏輯。</span><span class="sxs-lookup"><span data-stu-id="56882-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="56882-111">可以定義 UI 事件處理常式、系結至輸入資料，以及管理其本身的生命週期。</span><span class="sxs-lookup"><span data-stu-id="56882-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="56882-112">通常會使用 Razor 語法在*razor*檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="56882-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="56882-113">Razor 簡介</span><span class="sxs-lookup"><span data-stu-id="56882-113">An introduction to Razor</span></span>

<span data-ttu-id="56882-114">Razor 是以 HTML 和 c # 為基礎的輕量標記範本化語言。</span><span class="sxs-lookup"><span data-stu-id="56882-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="56882-115">使用 Razor，您可以在標記和 c # 程式碼之間順暢地轉換，以定義您的元件轉譯邏輯。</span><span class="sxs-lookup"><span data-stu-id="56882-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="56882-116">編譯*razor*檔案時，會在 .net 類別中以結構化的方式來捕獲轉譯邏輯。</span><span class="sxs-lookup"><span data-stu-id="56882-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="56882-117">已編譯類別的名稱取自*razor*檔案名。</span><span class="sxs-lookup"><span data-stu-id="56882-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="56882-118">命名空間是從專案的預設命名空間和資料夾路徑取得，或者您可以使用指示詞明確指定命名空間， `@namespace` () 下的 Razor 指示詞。</span><span class="sxs-lookup"><span data-stu-id="56882-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="56882-119">元件的轉譯邏輯是使用標準的 HTML 標籤撰寫的，並使用 c # 新增動態邏輯。</span><span class="sxs-lookup"><span data-stu-id="56882-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="56882-120">`@`字元是用來轉換成 c #。</span><span class="sxs-lookup"><span data-stu-id="56882-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="56882-121">Razor 通常會在您切換回 HTML 時，聰明地找出。</span><span class="sxs-lookup"><span data-stu-id="56882-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="56882-122">例如，下列元件會呈現 `<p>` 具有目前時間的標記：</span><span class="sxs-lookup"><span data-stu-id="56882-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="56882-123">若要明確指定 c # 運算式的開頭和結尾，請使用括弧：</span><span class="sxs-lookup"><span data-stu-id="56882-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="56882-124">Razor 也可以讓您輕鬆地在呈現邏輯中使用 c # 控制流程。</span><span class="sxs-lookup"><span data-stu-id="56882-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="56882-125">例如，您可以有條件地呈現一些 HTML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="56882-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="56882-126">或者，您可以使用一般 c # 迴圈來產生專案清單， `foreach` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="56882-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="56882-127">Razor 指示詞（例如 ASP.NET Web form 中的指示詞）控制了 Razor 元件編譯方式的許多層面。</span><span class="sxs-lookup"><span data-stu-id="56882-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="56882-128">範例包括元件的：</span><span class="sxs-lookup"><span data-stu-id="56882-128">Examples include the component's:</span></span>

- <span data-ttu-id="56882-129">命名空間</span><span class="sxs-lookup"><span data-stu-id="56882-129">Namespace</span></span>
- <span data-ttu-id="56882-130">基底類別</span><span class="sxs-lookup"><span data-stu-id="56882-130">Base class</span></span>
- <span data-ttu-id="56882-131">實作為介面</span><span class="sxs-lookup"><span data-stu-id="56882-131">Implemented interfaces</span></span>
- <span data-ttu-id="56882-132">泛型參數</span><span class="sxs-lookup"><span data-stu-id="56882-132">Generic parameters</span></span>
- <span data-ttu-id="56882-133">匯入的命名空間</span><span class="sxs-lookup"><span data-stu-id="56882-133">Imported namespaces</span></span>
- <span data-ttu-id="56882-134">路由</span><span class="sxs-lookup"><span data-stu-id="56882-134">Routes</span></span>

<span data-ttu-id="56882-135">Razor 指示詞是以 `@` 字元開頭，而且通常用於檔案開頭的新行開頭。</span><span class="sxs-lookup"><span data-stu-id="56882-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="56882-136">例如，指示詞會 `@namespace` 定義元件的命名空間：</span><span class="sxs-lookup"><span data-stu-id="56882-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="56882-137">下表摘要說明中所使用的各種 Razor 指示詞 Blazor ，以及其 ASP.NET Web form 對應項（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="56882-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="56882-138">指示詞</span><span class="sxs-lookup"><span data-stu-id="56882-138">Directive</span></span>    |<span data-ttu-id="56882-139">描述</span><span class="sxs-lookup"><span data-stu-id="56882-139">Description</span></span>|<span data-ttu-id="56882-140">範例</span><span class="sxs-lookup"><span data-stu-id="56882-140">Example</span></span>|<span data-ttu-id="56882-141">Web Forms 對等</span><span class="sxs-lookup"><span data-stu-id="56882-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="56882-142">將類別層級屬性加入至元件</span><span class="sxs-lookup"><span data-stu-id="56882-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="56882-143">無</span><span class="sxs-lookup"><span data-stu-id="56882-143">None</span></span>|
|`@code`      |<span data-ttu-id="56882-144">將類別成員加入至元件</span><span class="sxs-lookup"><span data-stu-id="56882-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="56882-145">執行指定的介面</span><span class="sxs-lookup"><span data-stu-id="56882-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="56882-146">使用程式碼後置</span><span class="sxs-lookup"><span data-stu-id="56882-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="56882-147">繼承自指定的基類</span><span class="sxs-lookup"><span data-stu-id="56882-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="56882-148">將服務插入元件</span><span class="sxs-lookup"><span data-stu-id="56882-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="56882-149">無</span><span class="sxs-lookup"><span data-stu-id="56882-149">None</span></span>|
|`@layout`    |<span data-ttu-id="56882-150">指定元件的版面配置元件</span><span class="sxs-lookup"><span data-stu-id="56882-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="56882-151">設定元件的命名空間</span><span class="sxs-lookup"><span data-stu-id="56882-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="56882-152">無</span><span class="sxs-lookup"><span data-stu-id="56882-152">None</span></span>|
|`@page`      |<span data-ttu-id="56882-153">指定元件的路由</span><span class="sxs-lookup"><span data-stu-id="56882-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="56882-154">指定元件的泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="56882-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="56882-155">使用程式碼後置</span><span class="sxs-lookup"><span data-stu-id="56882-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="56882-156">指定要帶入範圍的命名空間</span><span class="sxs-lookup"><span data-stu-id="56882-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="56882-157">在*web.config*中新增命名空間</span><span class="sxs-lookup"><span data-stu-id="56882-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="56882-158">Razor 元件也會廣泛使用專案上的指示詞*屬性*，以控制如何編譯元件 (事件處理、資料系結、元件 & 元素) 參考等等的各種層面。</span><span class="sxs-lookup"><span data-stu-id="56882-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="56882-159">指示詞屬性全都遵循通用的泛型語法，其中括弧中的值是選擇性的：</span><span class="sxs-lookup"><span data-stu-id="56882-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="56882-160">下表摘要說明中所使用之 Razor 指示詞的各種屬性 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="56882-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="56882-161">屬性</span><span class="sxs-lookup"><span data-stu-id="56882-161">Attribute</span></span>    |<span data-ttu-id="56882-162">描述</span><span class="sxs-lookup"><span data-stu-id="56882-162">Description</span></span>|<span data-ttu-id="56882-163">範例</span><span class="sxs-lookup"><span data-stu-id="56882-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="56882-164">呈現屬性的字典</span><span class="sxs-lookup"><span data-stu-id="56882-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="56882-165">建立雙向資料系結</span><span class="sxs-lookup"><span data-stu-id="56882-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="56882-166">加入指定事件的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="56882-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="56882-167">指定比較演算法用來保留集合中元素的索引鍵</span><span class="sxs-lookup"><span data-stu-id="56882-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="56882-168">捕捉元件或 HTML 元素的參考</span><span class="sxs-lookup"><span data-stu-id="56882-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="56882-169"> (、、) 等所使用的各種指示詞屬性 Blazor `@onclick` `@bind` `@ref` 會在下列各節和後續章節中說明。</span><span class="sxs-lookup"><span data-stu-id="56882-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="56882-170">*.Aspx*和 *.ascx*檔案中使用的許多語法都具有 Razor 中的平行語法。</span><span class="sxs-lookup"><span data-stu-id="56882-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="56882-171">以下是 ASP.NET Web Forms 和 Razor 語法的簡單比較。</span><span class="sxs-lookup"><span data-stu-id="56882-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="56882-172">功能</span><span class="sxs-lookup"><span data-stu-id="56882-172">Feature</span></span>                      |<span data-ttu-id="56882-173">Web Form</span><span class="sxs-lookup"><span data-stu-id="56882-173">Web Forms</span></span>           |<span data-ttu-id="56882-174">語法</span><span class="sxs-lookup"><span data-stu-id="56882-174">Syntax</span></span>               |<span data-ttu-id="56882-175">Razor</span><span class="sxs-lookup"><span data-stu-id="56882-175">Razor</span></span>         |<span data-ttu-id="56882-176">語法</span><span class="sxs-lookup"><span data-stu-id="56882-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="56882-177">指示詞</span><span class="sxs-lookup"><span data-stu-id="56882-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="56882-178">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="56882-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="56882-179">運算式</span><span class="sxs-lookup"><span data-stu-id="56882-179">Expressions</span></span><br><span data-ttu-id="56882-180"> (HTML 編碼) </span><span class="sxs-lookup"><span data-stu-id="56882-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="56882-181">隱`@`</span><span class="sxs-lookup"><span data-stu-id="56882-181">Implicit: `@`</span></span><br><span data-ttu-id="56882-182">確切`@()`</span><span class="sxs-lookup"><span data-stu-id="56882-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="56882-183">註解</span><span class="sxs-lookup"><span data-stu-id="56882-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="56882-184">資料繫結</span><span class="sxs-lookup"><span data-stu-id="56882-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="56882-185">若要將成員加入至 Razor 元件類別，請使用指示詞 `@code` 。</span><span class="sxs-lookup"><span data-stu-id="56882-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="56882-186">這項技術類似于 `<script runat="server">...</script>` 在 ASP.NET Web Forms 使用者控制項或頁面中使用區塊。</span><span class="sxs-lookup"><span data-stu-id="56882-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="56882-187">因為 Razor 是以 c # 為基礎，所以必須從 c # 專案中編譯， (*.csproj*) 。</span><span class="sxs-lookup"><span data-stu-id="56882-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="56882-188">您無法從 Visual Basic 專案編譯*razor*檔案， (*. vbproj*) 。</span><span class="sxs-lookup"><span data-stu-id="56882-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="56882-189">您仍然可以參考專案中 Visual Basic 專案 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="56882-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="56882-190">相反的情況也是如此。</span><span class="sxs-lookup"><span data-stu-id="56882-190">The opposite is true too.</span></span>

<span data-ttu-id="56882-191">如需完整的 Razor 語法參考，請參閱[ASP.NET Core 的 Razor 語法參考](/aspnet/core/mvc/views/razor)。</span><span class="sxs-lookup"><span data-stu-id="56882-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="56882-192">使用元件</span><span class="sxs-lookup"><span data-stu-id="56882-192">Use components</span></span>

<span data-ttu-id="56882-193">除了一般的 HTML 之外，元件也可以使用其他元件做為其轉譯邏輯的一部分。</span><span class="sxs-lookup"><span data-stu-id="56882-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="56882-194">在 Razor 中使用元件的語法類似于在 ASP.NET Web Forms 應用程式中使用使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="56882-195">元件是使用符合元件型別名稱的元素標記來指定。</span><span class="sxs-lookup"><span data-stu-id="56882-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="56882-196">例如，您可以新增元件， `Counter` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="56882-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="56882-197">不同于 ASP.NET Web form，中的元件 Blazor ：</span><span class="sxs-lookup"><span data-stu-id="56882-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="56882-198">請勿使用元素前置詞 (例如， `asp:`) 。</span><span class="sxs-lookup"><span data-stu-id="56882-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="56882-199">不需要在頁面上或在*web.config*中註冊。</span><span class="sxs-lookup"><span data-stu-id="56882-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="56882-200">您可以將 Razor 元件視為 .NET 類型，因為這正是它們的意義。</span><span class="sxs-lookup"><span data-stu-id="56882-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="56882-201">如果參考包含元件的元件，則元件可供使用。</span><span class="sxs-lookup"><span data-stu-id="56882-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="56882-202">若要將元件的命名空間帶入範圍中，請套用指示詞 `@using` ：</span><span class="sxs-lookup"><span data-stu-id="56882-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="56882-203">如預設專案中所示 Blazor ，通常會將指示詞放入 `@using` _Imports 的*razor*檔案中，使其匯入相同目錄和子目錄中的所有*razor*檔案。</span><span class="sxs-lookup"><span data-stu-id="56882-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="56882-204">如果元件的命名空間不在範圍內，您可以使用其完整類型名稱指定元件，如同您在 c # 中所能執行的動作：</span><span class="sxs-lookup"><span data-stu-id="56882-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="56882-205">元件參數</span><span class="sxs-lookup"><span data-stu-id="56882-205">Component parameters</span></span>

<span data-ttu-id="56882-206">在 ASP.NET Web Forms 中，您可以使用公用屬性將參數和資料傳送至控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="56882-207">這些屬性可以使用屬性在標記中設定，或直接在程式碼中設定。</span><span class="sxs-lookup"><span data-stu-id="56882-207">These properties can be set in markup using attributes or set directly in code.</span></span> Blazor<span data-ttu-id="56882-208">元件的工作方式類似，雖然元件屬性也必須以屬性標記， `[Parameter]` 才能視為元件參數。</span><span class="sxs-lookup"><span data-stu-id="56882-208"> components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="56882-209">下列 `Counter` 元件會定義名為的元件參數 `IncrementAmount` ，可以用來指定 `Counter` 每次按下按鈕時應該遞增的數量。</span><span class="sxs-lookup"><span data-stu-id="56882-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="56882-210">若要在中指定元件參數 Blazor ，請使用屬性，就像您在 ASP.NET Web form 中所做的一樣：</span><span class="sxs-lookup"><span data-stu-id="56882-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="56882-211">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="56882-211">Event handlers</span></span>

<span data-ttu-id="56882-212">兩者都 ASP.NET Web form，並 Blazor 提供以事件為基礎的程式設計模型來處理 UI 事件。</span><span class="sxs-lookup"><span data-stu-id="56882-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="56882-213">這類事件的範例包括按鈕點擊和文字輸入。</span><span class="sxs-lookup"><span data-stu-id="56882-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="56882-214">在 ASP.NET Web Forms 中，您可以使用 HTML 伺服器控制項來處理 DOM 所公開的 UI 事件，也可以處理 Web 服務器控制項所公開的事件。</span><span class="sxs-lookup"><span data-stu-id="56882-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="56882-215">事件會透過表單回傳要求呈現在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="56882-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="56882-216">請考慮下列 Web Forms 按鈕的 click 範例：</span><span class="sxs-lookup"><span data-stu-id="56882-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="56882-217">*計數器 .ascx*</span><span class="sxs-lookup"><span data-stu-id="56882-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="56882-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="56882-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="56882-219">在中 Blazor ，您可以直接使用表單的指示詞屬性來註冊 DOM UI 事件的處理常式 `@on{event}` 。</span><span class="sxs-lookup"><span data-stu-id="56882-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="56882-220">`{event}`預留位置代表事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="56882-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="56882-221">例如，您可以聆聽按鈕的點擊方式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="56882-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="56882-222">事件處理常式可以接受選擇性的事件特定引數，以提供有關事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56882-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="56882-223">例如，滑鼠事件可以接受 `MouseEventArgs` 引數，但不是必要的。</span><span class="sxs-lookup"><span data-stu-id="56882-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="56882-224">您可以使用 lambda 運算式，而不是參考事件處理常式的方法群組。</span><span class="sxs-lookup"><span data-stu-id="56882-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="56882-225">Lambda 運算式可讓您關閉其他範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="56882-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="56882-226">事件處理常式可以同步或非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="56882-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="56882-227">例如，下列 `OnClick` 事件處理常式會以非同步方式執行：</span><span class="sxs-lookup"><span data-stu-id="56882-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="56882-228">處理事件之後，會呈現元件以考慮任何元件狀態變更。</span><span class="sxs-lookup"><span data-stu-id="56882-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="56882-229">使用非同步事件處理常式時，元件會在處理常式執行完成之後立即轉譯。</span><span class="sxs-lookup"><span data-stu-id="56882-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="56882-230">此元件會在非同步完成後*再次*轉譯 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="56882-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="56882-231">這個非同步執行模式可讓您在非同步仍在進行時，呈現一些適當的 UI `Task` 。</span><span class="sxs-lookup"><span data-stu-id="56882-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="56882-232">元件也可以定義類型的元件參數，以定義自己的事件 `EventCallback<TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="56882-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="56882-233">事件回呼支援 DOM UI 事件處理常式的所有變化：選擇性引數、同步或非同步、方法群組或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="56882-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="56882-234">資料繫結</span><span class="sxs-lookup"><span data-stu-id="56882-234">Data binding</span></span>

Blazor<span data-ttu-id="56882-235">提供簡單的機制，可將 UI 元件的資料系結至元件的狀態。</span><span class="sxs-lookup"><span data-stu-id="56882-235"> provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="56882-236">此方法不同于 ASP.NET Web form 中的功能，可將資料從資料來源系結至 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="56882-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="56882-237">在[處理資料](data.md)一節中，我們將討論如何處理來自不同資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="56882-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="56882-238">若要從 UI 元件建立雙向資料系結至元件的狀態，請使用指示詞 `@bind` 屬性。</span><span class="sxs-lookup"><span data-stu-id="56882-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="56882-239">在下列範例中，核取方塊的值會系結至 `isChecked` 欄位。</span><span class="sxs-lookup"><span data-stu-id="56882-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="56882-240">當元件呈現時，核取方塊的值會設定為欄位的值 `isChecked` 。</span><span class="sxs-lookup"><span data-stu-id="56882-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="56882-241">當使用者切換核取方塊時， `onchange` 就會引發事件，並將 `isChecked` 欄位設定為新的值。</span><span class="sxs-lookup"><span data-stu-id="56882-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="56882-242">`@bind`此案例中的語法相當於下列標記：</span><span class="sxs-lookup"><span data-stu-id="56882-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="56882-243">若要變更用於系結的事件，請使用 `@bind:event` 屬性。</span><span class="sxs-lookup"><span data-stu-id="56882-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="56882-244">元件也可以支援資料系結至其參數。</span><span class="sxs-lookup"><span data-stu-id="56882-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="56882-245">若要進行資料系結，請使用與可系結參數相同的名稱來定義事件回呼參數。</span><span class="sxs-lookup"><span data-stu-id="56882-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="56882-246">「已變更」尾碼會新增至名稱。</span><span class="sxs-lookup"><span data-stu-id="56882-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="56882-247">*PasswordBox razor*</span><span class="sxs-lookup"><span data-stu-id="56882-247">*PasswordBox.razor*</span></span>

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="56882-248">若要將資料系結連結至基礎 UI 專案，請設定值，並直接在 UI 元素上處理事件，而不使用 `@bind` 屬性。</span><span class="sxs-lookup"><span data-stu-id="56882-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="56882-249">若要系結至元件參數，請使用 `@bind-{Parameter}` 屬性來指定您要系結的參數。</span><span class="sxs-lookup"><span data-stu-id="56882-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="56882-250">狀態變更</span><span class="sxs-lookup"><span data-stu-id="56882-250">State changes</span></span>

<span data-ttu-id="56882-251">如果元件的狀態在一般 UI 事件或事件回呼之外已變更，則元件必須手動指示需要再次轉譯。</span><span class="sxs-lookup"><span data-stu-id="56882-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="56882-252">若要通知元件的狀態已變更，請 `StateHasChanged` 在元件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="56882-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="56882-253">在下面的範例中，元件會顯示來自 `AppState` 服務的訊息，而應用程式的其他部分可加以更新。</span><span class="sxs-lookup"><span data-stu-id="56882-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="56882-254">元件 `StateHasChanged` 會向事件註冊其方法， `AppState.OnChange` 以便在每次更新訊息時呈現該元件。</span><span class="sxs-lookup"><span data-stu-id="56882-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="56882-255">元件生命週期</span><span class="sxs-lookup"><span data-stu-id="56882-255">Component lifecycle</span></span>

<span data-ttu-id="56882-256">ASP.NET Web form 架構具有定義完善的模組、頁面和控制項生命週期方法。</span><span class="sxs-lookup"><span data-stu-id="56882-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="56882-257">例如，下列控制項會 `Init` `Load` 執行、和週期事件的事件處理常式 `UnLoad` ：</span><span class="sxs-lookup"><span data-stu-id="56882-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="56882-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="56882-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor<span data-ttu-id="56882-259">元件也具有妥善定義的生命週期。</span><span class="sxs-lookup"><span data-stu-id="56882-259"> components also have a well-defined lifecycle.</span></span> <span data-ttu-id="56882-260">元件的生命週期可用來初始化元件狀態和執行 advanced 元件行為。</span><span class="sxs-lookup"><span data-stu-id="56882-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="56882-261">所有的 Blazor 元件生命週期方法都有同步和非同步版本。</span><span class="sxs-lookup"><span data-stu-id="56882-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="56882-262">元件呈現是同步的。</span><span class="sxs-lookup"><span data-stu-id="56882-262">Component rendering is synchronous.</span></span> <span data-ttu-id="56882-263">您無法在元件轉譯過程中執行非同步邏輯。</span><span class="sxs-lookup"><span data-stu-id="56882-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="56882-264">所有非同步邏輯都必須當做生命週期方法的一部分來執行 `async` 。</span><span class="sxs-lookup"><span data-stu-id="56882-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="56882-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="56882-265">OnInitialized</span></span>

<span data-ttu-id="56882-266">`OnInitialized`和 `OnInitializedAsync` 方法是用來初始化元件。</span><span class="sxs-lookup"><span data-stu-id="56882-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="56882-267">元件通常會在第一次呈現之後初始化。</span><span class="sxs-lookup"><span data-stu-id="56882-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="56882-268">元件初始化之後，它可能會轉譯多次，最後才會被處置。</span><span class="sxs-lookup"><span data-stu-id="56882-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="56882-269">`OnInitialized`方法類似于 `Page_Load` ASP.NET Web Forms 頁面和控制項中的事件。</span><span class="sxs-lookup"><span data-stu-id="56882-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="56882-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="56882-270">OnParametersSet</span></span>

<span data-ttu-id="56882-271">`OnParametersSet` `OnParametersSetAsync` 當元件已從其父系接收參數，且已將值指派給屬性時，會呼叫和方法。</span><span class="sxs-lookup"><span data-stu-id="56882-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="56882-272">這些方法會在元件初始化之後和*每次呈現元件時*執行。</span><span class="sxs-lookup"><span data-stu-id="56882-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="56882-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="56882-273">OnAfterRender</span></span>

<span data-ttu-id="56882-274">在 `OnAfterRender` `OnAfterRenderAsync` 元件完成呈現之後，會呼叫和方法。</span><span class="sxs-lookup"><span data-stu-id="56882-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="56882-275">此時會填入元素和元件參考 () 下的這些概念的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="56882-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="56882-276">此時會啟用與瀏覽器的互動。</span><span class="sxs-lookup"><span data-stu-id="56882-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="56882-277">可以安全地進行與 DOM 的互動和 JavaScript 的執行。</span><span class="sxs-lookup"><span data-stu-id="56882-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="56882-278">`OnAfterRender`在 `OnAfterRenderAsync` *伺服器上進行預呈現時，不會呼叫*和。</span><span class="sxs-lookup"><span data-stu-id="56882-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="56882-279">`firstRender`參數是 `true` 第一次轉譯元件時，否則其值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="56882-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="56882-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="56882-280">IDisposable</span></span>

Blazor<span data-ttu-id="56882-281">元件可以在 `IDisposable` 元件從 UI 中移除時，執行以處置資源。</span><span class="sxs-lookup"><span data-stu-id="56882-281"> components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="56882-282">Razor 元件可以使用指示詞來執行 `IDispose` `@implements` ：</span><span class="sxs-lookup"><span data-stu-id="56882-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="56882-283">捕捉元件參考</span><span class="sxs-lookup"><span data-stu-id="56882-283">Capture component references</span></span>

<span data-ttu-id="56882-284">在 ASP.NET Web form 中，通常會藉由參考其識別碼，直接在程式碼中操作控制項實例。</span><span class="sxs-lookup"><span data-stu-id="56882-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="56882-285">在中 Blazor ，您也可以捕捉和操作元件的參考，雖然較不常見。</span><span class="sxs-lookup"><span data-stu-id="56882-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="56882-286">若要在中捕捉元件參考 Blazor ，請使用指示詞 `@ref` 屬性。</span><span class="sxs-lookup"><span data-stu-id="56882-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="56882-287">屬性的值應該符合可設定欄位的名稱，其類型與參考的元件相同。</span><span class="sxs-lookup"><span data-stu-id="56882-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="56882-288">當父代元件呈現時，欄位會填入子元件實例。</span><span class="sxs-lookup"><span data-stu-id="56882-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="56882-289">接著，您可以呼叫或操作元件實例上的方法。</span><span class="sxs-lookup"><span data-stu-id="56882-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="56882-290">不建議直接使用元件參考來操作元件狀態。</span><span class="sxs-lookup"><span data-stu-id="56882-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="56882-291">這麼做可防止元件在正確的時間自動轉譯。</span><span class="sxs-lookup"><span data-stu-id="56882-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="56882-292">Capture 元素參考</span><span class="sxs-lookup"><span data-stu-id="56882-292">Capture element references</span></span>

Blazor<span data-ttu-id="56882-293">元件可以捕獲元素的參考。</span><span class="sxs-lookup"><span data-stu-id="56882-293"> components can capture references to an element.</span></span> <span data-ttu-id="56882-294">不同于 ASP.NET Web Forms 中的 HTML 伺服器控制項，您無法直接使用中的專案參考來操作 DOM Blazor 。</span><span class="sxs-lookup"><span data-stu-id="56882-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> Blazor<span data-ttu-id="56882-295">使用其 DOM 比較演算法，為您處理大部分的 DOM 互動。</span><span class="sxs-lookup"><span data-stu-id="56882-295"> handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="56882-296">中的已捕捉專案參考 Blazor 是不透明的。</span><span class="sxs-lookup"><span data-stu-id="56882-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="56882-297">不過，它們是用來傳遞 JavaScript interop 呼叫中的特定元素參考。</span><span class="sxs-lookup"><span data-stu-id="56882-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="56882-298">如需 JavaScript interop 的詳細資訊，請參閱[ASP.NET Core Blazor javascript interop](/aspnet/core/blazor/javascript-interop)。</span><span class="sxs-lookup"><span data-stu-id="56882-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="56882-299">樣板化元件</span><span class="sxs-lookup"><span data-stu-id="56882-299">Templated components</span></span>

<span data-ttu-id="56882-300">在 ASP.NET Web Forms 中，您可以建立樣板*化控制項*。</span><span class="sxs-lookup"><span data-stu-id="56882-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="56882-301">樣板化控制項可讓開發人員指定用來呈現容器控制項的 HTML 部分。</span><span class="sxs-lookup"><span data-stu-id="56882-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="56882-302">建立樣板化伺服器控制項的機制很複雜，但它們可以讓您以可自訂的方式呈現資料的強大案例。</span><span class="sxs-lookup"><span data-stu-id="56882-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="56882-303">樣板化控制項的範例包括 `Repeater` 和 `DataList` 。</span><span class="sxs-lookup"><span data-stu-id="56882-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

Blazor<span data-ttu-id="56882-304">元件也可以藉由定義或類型的元件參數來進行樣板化 `RenderFragment` `RenderFragment<T>` 。</span><span class="sxs-lookup"><span data-stu-id="56882-304"> components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="56882-305">`RenderFragment`代表 Razor 標記的區塊，可由元件呈現。</span><span class="sxs-lookup"><span data-stu-id="56882-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="56882-306">`RenderFragment<T>`是 Razor 標記的區塊，它會接受呈現轉譯片段時可指定的參數。</span><span class="sxs-lookup"><span data-stu-id="56882-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="56882-307">子內容</span><span class="sxs-lookup"><span data-stu-id="56882-307">Child content</span></span>

Blazor<span data-ttu-id="56882-308">元件可以將其子內容捕捉為 `RenderFragment` ，並將該內容轉譯為元件轉譯的一部分。</span><span class="sxs-lookup"><span data-stu-id="56882-308"> components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="56882-309">若要捕獲子內容，請定義類型的元件參數 `RenderFragment` ，並將它命名為 `ChildContent` 。</span><span class="sxs-lookup"><span data-stu-id="56882-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="56882-310">*ChildContentComponent razor*</span><span class="sxs-lookup"><span data-stu-id="56882-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="56882-311">然後，父系元件可以使用一般 Razor 語法來提供子內容。</span><span class="sxs-lookup"><span data-stu-id="56882-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="56882-312">範本參數</span><span class="sxs-lookup"><span data-stu-id="56882-312">Template parameters</span></span>

<span data-ttu-id="56882-313">樣板化 Blazor 元件也可以定義多個類型的元件參數 `RenderFragment` 或 `RenderFragment<T>` 。</span><span class="sxs-lookup"><span data-stu-id="56882-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="56882-314">當叫用 `RenderFragment<T>` 時，可以指定的參數。</span><span class="sxs-lookup"><span data-stu-id="56882-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="56882-315">若要指定元件的泛型型別參數，請使用 Razor 指示詞 `@typeparam` 。</span><span class="sxs-lookup"><span data-stu-id="56882-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="56882-316">*SimpleListView razor*</span><span class="sxs-lookup"><span data-stu-id="56882-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="56882-317">使用樣板化元件時，可以使用符合參數名稱的子項目來指定範本參數。</span><span class="sxs-lookup"><span data-stu-id="56882-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="56882-318">當做元素傳遞之類型的元件引數 `RenderFragment<T>` 具有名為的隱含參數 `context` 。</span><span class="sxs-lookup"><span data-stu-id="56882-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="56882-319">您可以使用子項目上的屬性來變更這個實參數的名稱 `Context` 。</span><span class="sxs-lookup"><span data-stu-id="56882-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="56882-320">您可以使用符合型別參數名稱的屬性來指定任何泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="56882-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="56882-321">可能的話，會推斷型別參數：</span><span class="sxs-lookup"><span data-stu-id="56882-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="56882-322">此元件的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="56882-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="56882-323">程式碼後置</span><span class="sxs-lookup"><span data-stu-id="56882-323">Code-behind</span></span>

<span data-ttu-id="56882-324">Blazor元件通常是在單一的*razor*檔案中撰寫。</span><span class="sxs-lookup"><span data-stu-id="56882-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="56882-325">不過，也可以使用程式碼後置檔案來分隔程式碼和標記。</span><span class="sxs-lookup"><span data-stu-id="56882-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="56882-326">若要使用元件檔案，請新增符合元件檔檔案名的 c # 檔案，但已新增 (*Counter.razor.cs*) 的 *.cs 副檔名。*</span><span class="sxs-lookup"><span data-stu-id="56882-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="56882-327">使用 c # 檔案來定義元件的基類。</span><span class="sxs-lookup"><span data-stu-id="56882-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="56882-328">您可以將基類命名為任何您想要的名稱，但通常會將類別命名為與 component 類別相同，但 `Base` () 加入延伸模組 `CounterBase` 。</span><span class="sxs-lookup"><span data-stu-id="56882-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="56882-329">以元件為基礎的類別也必須衍生自 `ComponentBase` 。</span><span class="sxs-lookup"><span data-stu-id="56882-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="56882-330">然後，在 Razor 元件檔案中加入指示詞， `@inherits` 以指定元件 () 的基類 `@inherits CounterBase` 。</span><span class="sxs-lookup"><span data-stu-id="56882-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="56882-331">*Counter. razor*</span><span class="sxs-lookup"><span data-stu-id="56882-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="56882-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="56882-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="56882-333">元件的成員在基類中的可見度必須是 `protected` 或，才能 `public` 顯示在元件類別中。</span><span class="sxs-lookup"><span data-stu-id="56882-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="56882-334">其他資源</span><span class="sxs-lookup"><span data-stu-id="56882-334">Additional resources</span></span>

<span data-ttu-id="56882-335">上述並不是元件所有層面的完整處理 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="56882-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="56882-336">如需如何[建立和使用 Razor 元件 ASP.NET Core](/aspnet/core/blazor/components)的詳細資訊，請參閱 Blazor 檔集。</span><span class="sxs-lookup"><span data-stu-id="56882-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56882-337">[上一個](app-startup.md) 
>[下一步](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="56882-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
