---
title: 使用 Blazor 構建可重用的 UI 元件
description: 瞭解如何使用 Blazor 構建可重用的 UI 元件，以及它們與 ASP.NET Web 表單控制項的比較方式。
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228618"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="6abda-103">使用 Blazor 構建可重用的 UI 元件</span><span class="sxs-lookup"><span data-stu-id="6abda-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6abda-104">ASP.NET Web 表單中一個美妙的事情是，它如何將可重用的使用者介面 （UI） 代碼封裝到可重用的 UI 控制項中。</span><span class="sxs-lookup"><span data-stu-id="6abda-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="6abda-105">可以使用 *.ascx*檔在標記中定義自訂使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="6abda-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="6abda-106">您還可以在代碼中構建詳細的伺服器控制項，並支援完全設計人員。</span><span class="sxs-lookup"><span data-stu-id="6abda-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="6abda-107">Blazor 還支援通過*元件*進行 UI 封裝。</span><span class="sxs-lookup"><span data-stu-id="6abda-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="6abda-108">元件：</span><span class="sxs-lookup"><span data-stu-id="6abda-108">A component:</span></span>

- <span data-ttu-id="6abda-109">是 UI 的自包含塊。</span><span class="sxs-lookup"><span data-stu-id="6abda-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="6abda-110">維護自己的狀態和呈現邏輯。</span><span class="sxs-lookup"><span data-stu-id="6abda-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="6abda-111">可以定義 UI 事件處理常式、綁定到輸入資料以及管理其自己的生命週期。</span><span class="sxs-lookup"><span data-stu-id="6abda-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="6abda-112">通常在使用 Razor 語法的 *.razor*檔中定義。</span><span class="sxs-lookup"><span data-stu-id="6abda-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="6abda-113">剃刀簡介</span><span class="sxs-lookup"><span data-stu-id="6abda-113">An introduction to Razor</span></span>

<span data-ttu-id="6abda-114">Razor 是基於 HTML 和 C# 的羽量級標記範本化語言。</span><span class="sxs-lookup"><span data-stu-id="6abda-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="6abda-115">使用 Razor，您可以在標記和 C# 代碼之間無縫過渡，以定義元件呈現邏輯。</span><span class="sxs-lookup"><span data-stu-id="6abda-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="6abda-116">編譯 *.razor*檔時，呈現邏輯以結構化方式在 .NET 類中捕獲。</span><span class="sxs-lookup"><span data-stu-id="6abda-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="6abda-117">已編譯類的名稱取自 *.razor*檔案名。</span><span class="sxs-lookup"><span data-stu-id="6abda-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="6abda-118">命名空間取自專案和資料夾路徑的預設命名空間，或者您可以使用`@namespace`指令顯式指定命名空間（下面有關 Razor 指令的更多）。</span><span class="sxs-lookup"><span data-stu-id="6abda-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="6abda-119">元件的呈現邏輯使用使用使用 C# 添加的動態邏輯使用普通 HTML 標籤進行創作。</span><span class="sxs-lookup"><span data-stu-id="6abda-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="6abda-120">該`@`字元用於轉換為 C#。</span><span class="sxs-lookup"><span data-stu-id="6abda-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="6abda-121">剃刀通常很聰明，可以找出您何時切換回 HTML。</span><span class="sxs-lookup"><span data-stu-id="6abda-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="6abda-122">例如，以下元件呈現當前`<p>`時間的標記：</span><span class="sxs-lookup"><span data-stu-id="6abda-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="6abda-123">要顯式指定 C# 運算式的開始和結束，請使用括弧：</span><span class="sxs-lookup"><span data-stu-id="6abda-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="6abda-124">Razor 還便於在渲染邏輯中使用 C# 控制流。</span><span class="sxs-lookup"><span data-stu-id="6abda-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="6abda-125">例如，您可以有條件地呈現一些 HTML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6abda-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="6abda-126">或者，您可以使用正常的 C#`foreach`迴圈生成項清單，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6abda-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="6abda-127">Razor 指令（如ASP.NET Web 表單中的指令）控制 Razor 元件的編譯方式的許多方面。</span><span class="sxs-lookup"><span data-stu-id="6abda-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="6abda-128">示例包括元件：</span><span class="sxs-lookup"><span data-stu-id="6abda-128">Examples include the component's:</span></span>

- <span data-ttu-id="6abda-129">命名空間</span><span class="sxs-lookup"><span data-stu-id="6abda-129">Namespace</span></span>
- <span data-ttu-id="6abda-130">基底類別</span><span class="sxs-lookup"><span data-stu-id="6abda-130">Base class</span></span>
- <span data-ttu-id="6abda-131">實現的介面</span><span class="sxs-lookup"><span data-stu-id="6abda-131">Implemented interfaces</span></span>
- <span data-ttu-id="6abda-132">泛型參數</span><span class="sxs-lookup"><span data-stu-id="6abda-132">Generic parameters</span></span>
- <span data-ttu-id="6abda-133">匯入的命名空間</span><span class="sxs-lookup"><span data-stu-id="6abda-133">Imported namespaces</span></span>
- <span data-ttu-id="6abda-134">路由</span><span class="sxs-lookup"><span data-stu-id="6abda-134">Routes</span></span>

<span data-ttu-id="6abda-135">Razor 指令以`@`字元開頭，通常在檔開頭的新行開始時使用。</span><span class="sxs-lookup"><span data-stu-id="6abda-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="6abda-136">例如，`@namespace`指令定義元件的命名空間：</span><span class="sxs-lookup"><span data-stu-id="6abda-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="6abda-137">下表總結了 Blazor 中使用的各種 Razor 指令及其ASP.NET Web 表單等效項（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="6abda-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="6abda-138">指示詞</span><span class="sxs-lookup"><span data-stu-id="6abda-138">Directive</span></span>    |<span data-ttu-id="6abda-139">描述</span><span class="sxs-lookup"><span data-stu-id="6abda-139">Description</span></span>|<span data-ttu-id="6abda-140">範例</span><span class="sxs-lookup"><span data-stu-id="6abda-140">Example</span></span>|<span data-ttu-id="6abda-141">與 Web 表單等效</span><span class="sxs-lookup"><span data-stu-id="6abda-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="6abda-142">向元件添加類級屬性</span><span class="sxs-lookup"><span data-stu-id="6abda-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="6abda-143">None</span><span class="sxs-lookup"><span data-stu-id="6abda-143">None</span></span>|
|`@code`      |<span data-ttu-id="6abda-144">將類成員添加到元件</span><span class="sxs-lookup"><span data-stu-id="6abda-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="6abda-145">實現指定的介面</span><span class="sxs-lookup"><span data-stu-id="6abda-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="6abda-146">使用程式碼後置</span><span class="sxs-lookup"><span data-stu-id="6abda-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="6abda-147">從指定的基類繼承</span><span class="sxs-lookup"><span data-stu-id="6abda-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="6abda-148">將服務注入元件</span><span class="sxs-lookup"><span data-stu-id="6abda-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="6abda-149">None</span><span class="sxs-lookup"><span data-stu-id="6abda-149">None</span></span>|
|`@layout`    |<span data-ttu-id="6abda-150">指定元件的佈局元件</span><span class="sxs-lookup"><span data-stu-id="6abda-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="6abda-151">設置元件的命名空間</span><span class="sxs-lookup"><span data-stu-id="6abda-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="6abda-152">None</span><span class="sxs-lookup"><span data-stu-id="6abda-152">None</span></span>|
|`@page`      |<span data-ttu-id="6abda-153">指定元件的路由</span><span class="sxs-lookup"><span data-stu-id="6abda-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="6abda-154">為元件指定泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="6abda-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="6abda-155">使用程式碼後置</span><span class="sxs-lookup"><span data-stu-id="6abda-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="6abda-156">指定要引入作用域的命名空間</span><span class="sxs-lookup"><span data-stu-id="6abda-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="6abda-157">在*Web.config 中*添加命名空間</span><span class="sxs-lookup"><span data-stu-id="6abda-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="6abda-158">Razor 元件還廣泛使用元素上的*指令屬性*來控制元件的編譯方式的各個方面（事件處理、資料繫結、元件&元素引用等）。</span><span class="sxs-lookup"><span data-stu-id="6abda-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="6abda-159">指令屬性都遵循一個通用通用語法，其中括弧中的值是可選的：</span><span class="sxs-lookup"><span data-stu-id="6abda-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="6abda-160">下表總結了 Blazor 中使用的 Razor 指令的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="6abda-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="6abda-161">屬性</span><span class="sxs-lookup"><span data-stu-id="6abda-161">Attribute</span></span>    |<span data-ttu-id="6abda-162">描述</span><span class="sxs-lookup"><span data-stu-id="6abda-162">Description</span></span>|<span data-ttu-id="6abda-163">範例</span><span class="sxs-lookup"><span data-stu-id="6abda-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="6abda-164">渲染屬性字典</span><span class="sxs-lookup"><span data-stu-id="6abda-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="6abda-165">創建雙向資料繫結</span><span class="sxs-lookup"><span data-stu-id="6abda-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="6abda-166">為指定事件添加事件處理常式</span><span class="sxs-lookup"><span data-stu-id="6abda-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="6abda-167">指定擴散演算法用於保留集合中元素的鍵</span><span class="sxs-lookup"><span data-stu-id="6abda-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="6abda-168">捕獲對元件或 HTML 元素的引用</span><span class="sxs-lookup"><span data-stu-id="6abda-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="6abda-169">Blazor （、、、`@onclick``@bind``@ref`等） 使用的各種指令屬性在以下各章和後面的章節仲介紹。</span><span class="sxs-lookup"><span data-stu-id="6abda-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="6abda-170">*.aspx*和 *.ascx*檔中使用的許多語法在 Razor 中具有並行語法。</span><span class="sxs-lookup"><span data-stu-id="6abda-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="6abda-171">下面是ASP.NET Web 表單和 Razor 的語法的簡單比較。</span><span class="sxs-lookup"><span data-stu-id="6abda-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="6abda-172">功能</span><span class="sxs-lookup"><span data-stu-id="6abda-172">Feature</span></span>                      |<span data-ttu-id="6abda-173">Web Form</span><span class="sxs-lookup"><span data-stu-id="6abda-173">Web Forms</span></span>           |<span data-ttu-id="6abda-174">語法</span><span class="sxs-lookup"><span data-stu-id="6abda-174">Syntax</span></span>               |<span data-ttu-id="6abda-175">Razor</span><span class="sxs-lookup"><span data-stu-id="6abda-175">Razor</span></span>         |<span data-ttu-id="6abda-176">語法</span><span class="sxs-lookup"><span data-stu-id="6abda-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="6abda-177">指示詞</span><span class="sxs-lookup"><span data-stu-id="6abda-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="6abda-178">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="6abda-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="6abda-179">運算式</span><span class="sxs-lookup"><span data-stu-id="6abda-179">Expressions</span></span><br><span data-ttu-id="6abda-180">（HTML 編碼）</span><span class="sxs-lookup"><span data-stu-id="6abda-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="6abda-181">隱 式：`@`</span><span class="sxs-lookup"><span data-stu-id="6abda-181">Implicit: `@`</span></span><br><span data-ttu-id="6abda-182">明確：`@()`</span><span class="sxs-lookup"><span data-stu-id="6abda-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="6abda-183">註解</span><span class="sxs-lookup"><span data-stu-id="6abda-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="6abda-184">資料繫結</span><span class="sxs-lookup"><span data-stu-id="6abda-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="6abda-185">要將成員添加到 Razor 元件類，請使用`@code`該指令。</span><span class="sxs-lookup"><span data-stu-id="6abda-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="6abda-186">此技術類似于在ASP.NET Web`<script runat="server">...</script>`表單使用者控制項或頁面中使用塊。</span><span class="sxs-lookup"><span data-stu-id="6abda-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="6abda-187">由於 Razor 基於 C#，因此必須從 C# 專案中編譯它 （*.csproj*）。</span><span class="sxs-lookup"><span data-stu-id="6abda-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="6abda-188">無法從視覺化基礎專案 *（.vbproj*） 編譯 *.razor*檔。</span><span class="sxs-lookup"><span data-stu-id="6abda-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="6abda-189">您仍然可以從 Blazor 專案中引用視覺化基本專案。</span><span class="sxs-lookup"><span data-stu-id="6abda-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="6abda-190">事實正好相反。</span><span class="sxs-lookup"><span data-stu-id="6abda-190">The opposite is true too.</span></span>

<span data-ttu-id="6abda-191">有關完整的 Razor 語法引用，請參閱[ASP.NET 酷睿的 Razor 語法引用](/aspnet/core/mvc/views/razor)。</span><span class="sxs-lookup"><span data-stu-id="6abda-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="6abda-192">使用元件</span><span class="sxs-lookup"><span data-stu-id="6abda-192">Use components</span></span>

<span data-ttu-id="6abda-193">除了普通 HTML 之外，元件還可以使用其他元件作為其呈現邏輯的一部分。</span><span class="sxs-lookup"><span data-stu-id="6abda-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="6abda-194">在 Razor 中使用元件的語法類似于在 ASP.NET Web 表單應用中使用使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="6abda-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="6abda-195">使用與元件的類型名稱匹配的元素標記指定元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="6abda-196">例如，您可以添加如下所示的`Counter`元件：</span><span class="sxs-lookup"><span data-stu-id="6abda-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="6abda-197">與ASP.NET Web 表單不同，Blazor 中的元件：</span><span class="sxs-lookup"><span data-stu-id="6abda-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="6abda-198">不要使用元素首碼（例如， `asp:`。</span><span class="sxs-lookup"><span data-stu-id="6abda-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="6abda-199">不需要在頁面或*Web*上註冊。</span><span class="sxs-lookup"><span data-stu-id="6abda-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="6abda-200">像想像一下 Razor 元件，就像您那樣，可以.NET 類型，因為這正是它們。</span><span class="sxs-lookup"><span data-stu-id="6abda-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="6abda-201">如果引用了包含元件的程式集，則該元件可供使用。</span><span class="sxs-lookup"><span data-stu-id="6abda-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="6abda-202">要將元件的命名空間引入範圍，請應用該`@using`指令：</span><span class="sxs-lookup"><span data-stu-id="6abda-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="6abda-203">如預設 Blazor 專案中所示，通常將指令放入`@using` *_Imports.razor*檔中，以便它們導入到同一目錄中的所有 *.razor*檔中以及子目錄中。</span><span class="sxs-lookup"><span data-stu-id="6abda-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="6abda-204">如果元件的命名空間不在作用域中，則可以使用元件的完整類型名稱指定元件，如在 C# 中：</span><span class="sxs-lookup"><span data-stu-id="6abda-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="6abda-205">元件參數</span><span class="sxs-lookup"><span data-stu-id="6abda-205">Component parameters</span></span>

<span data-ttu-id="6abda-206">在ASP.NET Web 表單中，可以使用公共屬性將參數和資料流程向控制項。</span><span class="sxs-lookup"><span data-stu-id="6abda-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="6abda-207">這些屬性可以使用屬性在標記中設置，也可以直接在代碼中設置。</span><span class="sxs-lookup"><span data-stu-id="6abda-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="6abda-208">Blazor 元件的工作方式類似，儘管元件屬性還必須使用要被視為元件參數`[Parameter]`的屬性進行標記。</span><span class="sxs-lookup"><span data-stu-id="6abda-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="6abda-209">以下`Counter`元件定義一個元件參數，該`IncrementAmount`參數可用於指定每次按一下按鈕時`Counter`應遞增的金額。</span><span class="sxs-lookup"><span data-stu-id="6abda-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="6abda-210">要在 Blazor 中指定元件參數，請使用ASP.NET Web 表單中的屬性：</span><span class="sxs-lookup"><span data-stu-id="6abda-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="6abda-211">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="6abda-211">Event handlers</span></span>

<span data-ttu-id="6abda-212">ASP.NET Web 表單和 Blazor 都提供了一個基於事件的程式設計模型來處理 UI 事件。</span><span class="sxs-lookup"><span data-stu-id="6abda-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="6abda-213">此類事件的示例包括按鈕按一下和文本輸入。</span><span class="sxs-lookup"><span data-stu-id="6abda-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="6abda-214">在ASP.NET Web 表單中，您可以使用 HTML 伺服器控制項來處理 DOM 公開的 UI 事件，也可以處理 Web 服務器控制項公開的事件。</span><span class="sxs-lookup"><span data-stu-id="6abda-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="6abda-215">事件通過回後表單請求在伺服器上顯示。</span><span class="sxs-lookup"><span data-stu-id="6abda-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="6abda-216">請考慮以下 Web 表單按鈕按一下示例：</span><span class="sxs-lookup"><span data-stu-id="6abda-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="6abda-217">*計數器.ascx*</span><span class="sxs-lookup"><span data-stu-id="6abda-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="6abda-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="6abda-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="6abda-219">在 Blazor 中，可以直接使用表單`@on{event}`的指令屬性註冊 DOM UI 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="6abda-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="6abda-220">占`{event}`位符表示事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6abda-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="6abda-221">例如，您可以偵聽按鈕按一下，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6abda-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="6abda-222">事件處理常式可以接受可選的特定于事件的參數來提供有關該事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6abda-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="6abda-223">例如，滑鼠事件可以採用`MouseEventArgs`參數，但不是必需的。</span><span class="sxs-lookup"><span data-stu-id="6abda-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="6abda-224">可以使用 lambda 運算式，而不是引用事件處理常式的方法組。</span><span class="sxs-lookup"><span data-stu-id="6abda-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="6abda-225">lambda 運算式允許您關閉其他範圍內值。</span><span class="sxs-lookup"><span data-stu-id="6abda-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="6abda-226">事件處理常式可以同步或非同步執行。</span><span class="sxs-lookup"><span data-stu-id="6abda-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="6abda-227">例如，以下`OnClick`事件處理常式非同步執行：</span><span class="sxs-lookup"><span data-stu-id="6abda-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="6abda-228">處理事件後，元件將呈現為考慮任何元件狀態更改。</span><span class="sxs-lookup"><span data-stu-id="6abda-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="6abda-229">使用非同步事件處理常式，在處理常式執行完成後立即呈現元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="6abda-230">非同步`Task`完成後 *，將再次*呈現元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="6abda-231">此非同步執行模式提供了在非同步`Task`仍在進行時呈現一些適當 UI 的機會。</span><span class="sxs-lookup"><span data-stu-id="6abda-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

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

<span data-ttu-id="6abda-232">元件還可以通過定義類型的`EventCallback<TValue>`元件參數來定義自己的事件。</span><span class="sxs-lookup"><span data-stu-id="6abda-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="6abda-233">事件回檔支援 DOM UI 事件處理常式的所有變體：可選參數、同步或非同步、方法組或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="6abda-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="6abda-234">資料繫結</span><span class="sxs-lookup"><span data-stu-id="6abda-234">Data binding</span></span>

<span data-ttu-id="6abda-235">Blazor 提供了一種將資料從 UI 元件綁定到元件狀態的簡單機制。</span><span class="sxs-lookup"><span data-stu-id="6abda-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="6abda-236">此方法不同于 ASP.NET Web 表單中用於將資料從資料來源綁定到 UI 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="6abda-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="6abda-237">我們將在["處理資料"](data.md)部分仲介紹處理來自不同資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="6abda-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="6abda-238">要創建從 UI 元件到元件狀態的雙向資料繫結，請使用`@bind`指令屬性。</span><span class="sxs-lookup"><span data-stu-id="6abda-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="6abda-239">在下面的示例中，核取方塊的值綁定到該`isChecked`欄位。</span><span class="sxs-lookup"><span data-stu-id="6abda-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="6abda-240">呈現元件時，核取方塊的值將設置為`isChecked`欄位的值。</span><span class="sxs-lookup"><span data-stu-id="6abda-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="6abda-241">當使用者切換核取方塊時，將`onchange`觸發事件並將`isChecked`該欄位設置為新值。</span><span class="sxs-lookup"><span data-stu-id="6abda-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="6abda-242">在這種情況下`@bind`，語法等效于以下標記：</span><span class="sxs-lookup"><span data-stu-id="6abda-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="6abda-243">要更改用於綁定的事件，請使用 屬性`@bind:event`。</span><span class="sxs-lookup"><span data-stu-id="6abda-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="6abda-244">元件還可以支援綁定到其參數的資料。</span><span class="sxs-lookup"><span data-stu-id="6abda-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="6abda-245">要綁定資料，請定義與可綁定參數同名的事件回檔參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="6abda-246">"已更改"尾碼將添加到名稱中。</span><span class="sxs-lookup"><span data-stu-id="6abda-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="6abda-247">*密碼盒.剃鬚刀*</span><span class="sxs-lookup"><span data-stu-id="6abda-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="6abda-248">要將資料繫結連結到基礎 UI 元素，請使用 該值設置值並直接在 UI 元素上處理事件`@bind`，而不是使用 屬性。</span><span class="sxs-lookup"><span data-stu-id="6abda-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="6abda-249">要綁定到元件參數，請使用屬性`@bind-{Parameter}`指定要綁定到的參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="6abda-250">狀態變更</span><span class="sxs-lookup"><span data-stu-id="6abda-250">State changes</span></span>

<span data-ttu-id="6abda-251">如果元件的狀態在正常 UI 事件或事件回檔之外已更改，則元件必須手動發出信號，表示需要再次呈現該元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="6abda-252">要發出元件狀態已更改的信號，請調用元件上`StateHasChanged`的方法。</span><span class="sxs-lookup"><span data-stu-id="6abda-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="6abda-253">在下面的示例中，元件顯示`AppState`來自服務的消息，該消息可以由應用的其他部分更新。</span><span class="sxs-lookup"><span data-stu-id="6abda-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="6abda-254">元件將其`StateHasChanged`方法註冊到事件中`AppState.OnChange`，以便每當消息更新時都會呈現該元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
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

## <a name="component-lifecycle"></a><span data-ttu-id="6abda-255">元件生命週期</span><span class="sxs-lookup"><span data-stu-id="6abda-255">Component lifecycle</span></span>

<span data-ttu-id="6abda-256">ASP.NET Web 表單框架為模組、頁面和控制定義了明確的生命週期方法。</span><span class="sxs-lookup"><span data-stu-id="6abda-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="6abda-257">例如，以下控制項為`Init`和`Load`和`UnLoad`生命週期事件實現事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="6abda-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="6abda-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="6abda-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="6abda-259">Blazor 元件也有定義明確的生命週期。</span><span class="sxs-lookup"><span data-stu-id="6abda-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="6abda-260">元件的生命週期可用於初始化元件狀態並實現高級元件行為。</span><span class="sxs-lookup"><span data-stu-id="6abda-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="6abda-261">Blazor 的所有元件生命週期方法都具有同步和非同步版本。</span><span class="sxs-lookup"><span data-stu-id="6abda-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="6abda-262">元件呈現是同步的。</span><span class="sxs-lookup"><span data-stu-id="6abda-262">Component rendering is synchronous.</span></span> <span data-ttu-id="6abda-263">不能作為元件呈現的一部分運行非同步邏輯。</span><span class="sxs-lookup"><span data-stu-id="6abda-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="6abda-264">所有非同步邏輯都必須作為生命週期方法的一`async`部分執行。</span><span class="sxs-lookup"><span data-stu-id="6abda-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="6abda-265">初始化時</span><span class="sxs-lookup"><span data-stu-id="6abda-265">OnInitialized</span></span>

<span data-ttu-id="6abda-266">和`OnInitialized``OnInitializedAsync`方法用於初始化元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="6abda-267">元件通常在首次呈現後初始化。</span><span class="sxs-lookup"><span data-stu-id="6abda-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="6abda-268">初始化元件後，在最終釋放元件之前，可能會多次呈現該元件。</span><span class="sxs-lookup"><span data-stu-id="6abda-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="6abda-269">該方法`OnInitialized`類似于ASP.NET Web`Page_Load`表單頁和控制項中的事件。</span><span class="sxs-lookup"><span data-stu-id="6abda-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="6abda-270">在參數設置上</span><span class="sxs-lookup"><span data-stu-id="6abda-270">OnParametersSet</span></span>

<span data-ttu-id="6abda-271">當`OnParametersSet`元件`OnParametersSetAsync`從其父元件接收參數並將值分配給屬性時，將調用 和 方法。</span><span class="sxs-lookup"><span data-stu-id="6abda-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="6abda-272">這些方法在元件初始化後以及*每次呈現元件時*執行。</span><span class="sxs-lookup"><span data-stu-id="6abda-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="6abda-273">在渲染後打開</span><span class="sxs-lookup"><span data-stu-id="6abda-273">OnAfterRender</span></span>

<span data-ttu-id="6abda-274">和`OnAfterRender``OnAfterRenderAsync`方法在元件完成呈現後調用。</span><span class="sxs-lookup"><span data-stu-id="6abda-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="6abda-275">此時將填充元素和元件引用（下面將介紹這些概念的更多內容）。</span><span class="sxs-lookup"><span data-stu-id="6abda-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="6abda-276">此時啟用了與瀏覽器的交互性。</span><span class="sxs-lookup"><span data-stu-id="6abda-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="6abda-277">與 DOM 和 JavaScript 執行的交互可以安全地發生。</span><span class="sxs-lookup"><span data-stu-id="6abda-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="6abda-278">`OnAfterRender`並在`OnAfterRenderAsync`*伺服器上預渲染時不調用*。</span><span class="sxs-lookup"><span data-stu-id="6abda-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="6abda-279">參數`firstRender`是`true`首次呈現元件;否則，其值為`false`。</span><span class="sxs-lookup"><span data-stu-id="6abda-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="6abda-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="6abda-280">IDisposable</span></span>

<span data-ttu-id="6abda-281">Blazor 元件可以`IDisposable`實現在從 UI 中刪除元件時釋放資源。</span><span class="sxs-lookup"><span data-stu-id="6abda-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="6abda-282">Razor 元件可以使用`IDispose``@implements`該指令實現：</span><span class="sxs-lookup"><span data-stu-id="6abda-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="6abda-283">捕獲元件引用</span><span class="sxs-lookup"><span data-stu-id="6abda-283">Capture component references</span></span>

<span data-ttu-id="6abda-284">在ASP.NET Web 表單中，通常通過引用控制項實例的 ID 來直接在代碼中操作控制項實例。</span><span class="sxs-lookup"><span data-stu-id="6abda-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="6abda-285">在 Blazor 中，還可以捕獲和操作對元件的引用，儘管它不太常見。</span><span class="sxs-lookup"><span data-stu-id="6abda-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="6abda-286">要在 Blazor 中捕獲元件引用，`@ref`請使用指令屬性。</span><span class="sxs-lookup"><span data-stu-id="6abda-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="6abda-287">屬性的值應與與引用的元件類型相同的可設置欄位的名稱匹配。</span><span class="sxs-lookup"><span data-stu-id="6abda-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="6abda-288">呈現父元件時，該欄位將填充子元件實例。</span><span class="sxs-lookup"><span data-stu-id="6abda-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="6abda-289">然後，您可以調用元件實例上的方法或以其他方式操作元件實例。</span><span class="sxs-lookup"><span data-stu-id="6abda-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="6abda-290">不建議直接使用元件引用操作元件狀態。</span><span class="sxs-lookup"><span data-stu-id="6abda-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="6abda-291">這樣做可防止元件在正確的時間自動呈現。</span><span class="sxs-lookup"><span data-stu-id="6abda-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="6abda-292">捕獲元素引用</span><span class="sxs-lookup"><span data-stu-id="6abda-292">Capture element references</span></span>

<span data-ttu-id="6abda-293">Blazor 元件可以捕獲對元素的引用。</span><span class="sxs-lookup"><span data-stu-id="6abda-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="6abda-294">與ASP.NET Web 表單中的 HTML 伺服器控制項不同，不能直接使用 Blazor 中的元素引用操作 DOM。</span><span class="sxs-lookup"><span data-stu-id="6abda-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="6abda-295">Blazor 使用 DOM 擴散演算法為您處理大多數 DOM 交互。</span><span class="sxs-lookup"><span data-stu-id="6abda-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="6abda-296">Blazor 中捕獲的元素引用不透明。</span><span class="sxs-lookup"><span data-stu-id="6abda-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="6abda-297">但是，它們用於傳遞 JavaScript 交互操作調用中的特定元素引用。</span><span class="sxs-lookup"><span data-stu-id="6abda-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="6abda-298">有關 JavaScript 互通的詳細資訊，請參閱[ASP.NET核心 Blazor JavaScript 互通](/aspnet/core/blazor/javascript-interop)。</span><span class="sxs-lookup"><span data-stu-id="6abda-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="6abda-299">樣板化元件</span><span class="sxs-lookup"><span data-stu-id="6abda-299">Templated components</span></span>

<span data-ttu-id="6abda-300">在ASP.NET Web 表單中，您可以創建*範本化控制項*。</span><span class="sxs-lookup"><span data-stu-id="6abda-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="6abda-301">範本化控制項使開發人員能夠指定用於呈現容器控制項的 HTML 的一部分。</span><span class="sxs-lookup"><span data-stu-id="6abda-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="6abda-302">構建範本化伺服器控制項的機制非常複雜，但它們支援以使用者自訂的方式呈現資料的強大方案。</span><span class="sxs-lookup"><span data-stu-id="6abda-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="6abda-303">範本化控制項的示例包括`Repeater`和`DataList`。</span><span class="sxs-lookup"><span data-stu-id="6abda-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="6abda-304">Blazor 元件也可以通過定義類型`RenderFragment`或`RenderFragment<T>`的元件參數進行範本化。</span><span class="sxs-lookup"><span data-stu-id="6abda-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="6abda-305">表示`RenderFragment`Razor 標記塊，然後由元件呈現。</span><span class="sxs-lookup"><span data-stu-id="6abda-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="6abda-306">A`RenderFragment<T>`是 Razor 標記的塊，它採用在渲染渲染片段時可以指定的參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="6abda-307">子內容</span><span class="sxs-lookup"><span data-stu-id="6abda-307">Child content</span></span>

<span data-ttu-id="6abda-308">Blazor 元件可以捕獲其子內容作為`RenderFragment`，並將該內容呈現為元件呈現的一部分。</span><span class="sxs-lookup"><span data-stu-id="6abda-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="6abda-309">要捕獲子內容，請定義類型的`RenderFragment`元件參數並將其`ChildContent`命名為 。</span><span class="sxs-lookup"><span data-stu-id="6abda-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="6abda-310">*子內容元件.razor*</span><span class="sxs-lookup"><span data-stu-id="6abda-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="6abda-311">然後，父元件可以使用正常的 Razor 語法提供子內容。</span><span class="sxs-lookup"><span data-stu-id="6abda-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="6abda-312">範本參數</span><span class="sxs-lookup"><span data-stu-id="6abda-312">Template parameters</span></span>

<span data-ttu-id="6abda-313">範本化的 Blazor 元件還可以定義類型`RenderFragment`或`RenderFragment<T>`的多個元件參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="6abda-314">調用 時可以`RenderFragment<T>`指定 的 參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="6abda-315">要為元件指定泛型型別參數，請使用`@typeparam`Razor 指令。</span><span class="sxs-lookup"><span data-stu-id="6abda-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="6abda-316">*簡單列表查看.剃鬚刀*</span><span class="sxs-lookup"><span data-stu-id="6abda-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="6abda-317">使用範本化元件時，可以使用與參數名稱匹配的子項目指定範本參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="6abda-318">`RenderFragment<T>`作為元素傳遞的類型元件參數具有名為 的`context`隱式參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="6abda-319">您可以使用子項目上`Context`的屬性更改此實現參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6abda-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="6abda-320">可以使用與類型參數名稱匹配的屬性指定任何泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="6abda-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="6abda-321">如果可能，將推斷類型參數：</span><span class="sxs-lookup"><span data-stu-id="6abda-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="6abda-322">此元件的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="6abda-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="6abda-323">程式碼後置</span><span class="sxs-lookup"><span data-stu-id="6abda-323">Code-behind</span></span>

<span data-ttu-id="6abda-324">Blazor 元件通常創作在單個 *.razor*檔中。</span><span class="sxs-lookup"><span data-stu-id="6abda-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="6abda-325">但是，也可以使用代碼背後的檔分隔代碼和標記。</span><span class="sxs-lookup"><span data-stu-id="6abda-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="6abda-326">要使用元件檔，添加與元件檔的檔案名匹配但添加了 *.cs*副檔名 *（Counter.razor.cs*） 的 C# 檔。</span><span class="sxs-lookup"><span data-stu-id="6abda-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="6abda-327">使用 C# 檔為元件定義基類。</span><span class="sxs-lookup"><span data-stu-id="6abda-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="6abda-328">您可以命名基類的任何內容，但通常將類命名為與元件類相同，但添加了`Base`擴展項 （）。`CounterBase`</span><span class="sxs-lookup"><span data-stu-id="6abda-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="6abda-329">基於元件的類也必須派生自`ComponentBase`。</span><span class="sxs-lookup"><span data-stu-id="6abda-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="6abda-330">然後，在 Razor 元件檔中，添加`@inherits`指令以指定元件的基類 （。`@inherits CounterBase`</span><span class="sxs-lookup"><span data-stu-id="6abda-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="6abda-331">*計數器.剃鬚刀*</span><span class="sxs-lookup"><span data-stu-id="6abda-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="6abda-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="6abda-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="6abda-333">基類中元件成員的可見度必須`protected`為或`public`對元件類可見。</span><span class="sxs-lookup"><span data-stu-id="6abda-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6abda-334">其他資源</span><span class="sxs-lookup"><span data-stu-id="6abda-334">Additional resources</span></span>

<span data-ttu-id="6abda-335">前面不是對Blazor元件所有方面的詳盡處理。</span><span class="sxs-lookup"><span data-stu-id="6abda-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="6abda-336">有關如何[創建和使用核心剃鬚刀元件ASP.NET](/aspnet/core/blazor/components)的詳細資訊，請參閱 Blazor 文檔。</span><span class="sxs-lookup"><span data-stu-id="6abda-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6abda-337">[上一個](app-startup.md)
>[下一個](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="6abda-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
