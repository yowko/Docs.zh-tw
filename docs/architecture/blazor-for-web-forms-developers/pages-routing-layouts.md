---
title: 頁面、路由和版面配置
description: 瞭解如何在 Blazor 中建立頁面、使用用戶端路由，以及管理頁面佈局。
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c31544156250a9e97ff8c0b17338f418817b21d2
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275826"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="9fb86-103">頁面、路由和版面配置</span><span class="sxs-lookup"><span data-stu-id="9fb86-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9fb86-104">ASP.NET Web Forms 應用程式是由 *.aspx*檔案中定義的頁面所組成。</span><span class="sxs-lookup"><span data-stu-id="9fb86-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="9fb86-105">每個頁面的位址都是以專案中的實體檔案路徑為基礎。</span><span class="sxs-lookup"><span data-stu-id="9fb86-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="9fb86-106">當瀏覽器對頁面提出要求時，頁面的內容會在伺服器上以動態方式呈現。</span><span class="sxs-lookup"><span data-stu-id="9fb86-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="9fb86-107">頁面的 HTML 標籤和其伺服器控制項的轉譯帳戶。</span><span class="sxs-lookup"><span data-stu-id="9fb86-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="9fb86-108">在 Blazor 中，應用程式中的每個頁面都是一個元件，通常是在*razor*檔案中定義，其中包含一或多個指定的路由。</span><span class="sxs-lookup"><span data-stu-id="9fb86-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="9fb86-109">路由大部分會發生在用戶端，而不涉及特定的伺服器要求。</span><span class="sxs-lookup"><span data-stu-id="9fb86-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="9fb86-110">瀏覽器會先對應用程式的根位址提出要求。</span><span class="sxs-lookup"><span data-stu-id="9fb86-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="9fb86-111">Blazor 應用程式中的根 @no__t 0 元件會接著處理攔截導覽要求，並將它們傳送至正確的元件。</span><span class="sxs-lookup"><span data-stu-id="9fb86-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="9fb86-112">Blazor 也支援*深層連結*。</span><span class="sxs-lookup"><span data-stu-id="9fb86-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="9fb86-113">當瀏覽器對應用程式根目錄以外的特定路由提出要求時，就會發生深層連結。</span><span class="sxs-lookup"><span data-stu-id="9fb86-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="9fb86-114">傳送到伺服器之深層連結的要求會路由傳送至 Blazor 應用程式，然後將要求用戶端路由傳送至正確的元件。</span><span class="sxs-lookup"><span data-stu-id="9fb86-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="9fb86-115">ASP.NET Web Forms 中的簡單頁面可能會包含下列標記：</span><span class="sxs-lookup"><span data-stu-id="9fb86-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="9fb86-116">*名稱 .aspx*</span><span class="sxs-lookup"><span data-stu-id="9fb86-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="9fb86-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="9fb86-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="9fb86-118">Blazor 應用程式中的對等頁面看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9fb86-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="9fb86-119">*名稱. razor*</span><span class="sxs-lookup"><span data-stu-id="9fb86-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="9fb86-120">建立頁面</span><span class="sxs-lookup"><span data-stu-id="9fb86-120">Create pages</span></span>

<span data-ttu-id="9fb86-121">若要在 Blazor 中建立頁面，請建立元件，並新增 `@page` Razor 指示詞來指定元件的路由。</span><span class="sxs-lookup"><span data-stu-id="9fb86-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="9fb86-122">@No__t-0 指示詞接受單一參數，也就是要新增至該元件的路由範本。</span><span class="sxs-lookup"><span data-stu-id="9fb86-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="9fb86-123">需要路由範本參數。</span><span class="sxs-lookup"><span data-stu-id="9fb86-123">The route template parameter is required.</span></span> <span data-ttu-id="9fb86-124">不同于 ASP.NET Web form，Blazor 元件的路由*不*會從其檔案位置推斷（雖然這可能是未來新增的功能）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="9fb86-125">路由範本語法與 ASP.NET Web Forms 中的路由所使用的基本語法相同。</span><span class="sxs-lookup"><span data-stu-id="9fb86-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="9fb86-126">使用大括弧在範本中指定路由參數。</span><span class="sxs-lookup"><span data-stu-id="9fb86-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="9fb86-127">Blazor 會將路由值系結至具有相同名稱的元件參數（不區分大小寫）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="9fb86-128">您也可以在 route 參數的值上指定條件約束。</span><span class="sxs-lookup"><span data-stu-id="9fb86-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="9fb86-129">例如，若要將產品識別碼限制為 `int`：</span><span class="sxs-lookup"><span data-stu-id="9fb86-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="9fb86-130">如需 Blazor 所支援之路由條件約束的完整清單，請參閱[路由條件約束](/aspnet/core/blazor/routing#route-constraints)。</span><span class="sxs-lookup"><span data-stu-id="9fb86-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="9fb86-131">路由器元件</span><span class="sxs-lookup"><span data-stu-id="9fb86-131">Router component</span></span>

<span data-ttu-id="9fb86-132">Blazor 中的路由是由 `Router` 元件所處理。</span><span class="sxs-lookup"><span data-stu-id="9fb86-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="9fb86-133">@No__t-0 元件通常用於應用程式的根元件（*razor*）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="9fb86-134">@No__t-0 元件會探索指定的 `AppAssembly` 中的可路由元件，以及選擇性地指定 `AdditionalAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="9fb86-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="9fb86-135">當瀏覽器導覽時，`Router` 會攔截導覽，並以解壓縮的 `RouteData` 來呈現其 @no__t 1 參數的內容（如果路由符合位址），否則 `Router` 會轉譯其 `NotFound` 參數。</span><span class="sxs-lookup"><span data-stu-id="9fb86-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="9fb86-136">@No__t 0 元件會處理呈現 `RouteData` 所指定的相符元件及其配置（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="9fb86-137">如果相符的元件沒有版面配置，則會使用選擇性指定的 `DefaultLayout`。</span><span class="sxs-lookup"><span data-stu-id="9fb86-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="9fb86-138">@No__t-0 元件會在指定的版面配置內呈現其子內容。</span><span class="sxs-lookup"><span data-stu-id="9fb86-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="9fb86-139">我們將在本章稍後詳細探討版面配置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="9fb86-140">巡覽</span><span class="sxs-lookup"><span data-stu-id="9fb86-140">Navigation</span></span>

<span data-ttu-id="9fb86-141">在 ASP.NET Web form 中，您可以藉由將重新導向回應傳回至瀏覽器，來觸發導覽至不同頁面。</span><span class="sxs-lookup"><span data-stu-id="9fb86-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="9fb86-142">例如:</span><span class="sxs-lookup"><span data-stu-id="9fb86-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="9fb86-143">在 Blazor 中，通常不可能傳回重新導向回應。</span><span class="sxs-lookup"><span data-stu-id="9fb86-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="9fb86-144">Blazor 不會使用要求-回復模型。</span><span class="sxs-lookup"><span data-stu-id="9fb86-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="9fb86-145">不過，您可以直接觸發瀏覽器導覽，就像使用 JavaScript 一樣。</span><span class="sxs-lookup"><span data-stu-id="9fb86-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="9fb86-146">Blazor 提供的 `NavigationManager` 服務可用於：</span><span class="sxs-lookup"><span data-stu-id="9fb86-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

* <span data-ttu-id="9fb86-147">取得目前的瀏覽器位址</span><span class="sxs-lookup"><span data-stu-id="9fb86-147">Get the current browser address</span></span>
* <span data-ttu-id="9fb86-148">取得基底位址</span><span class="sxs-lookup"><span data-stu-id="9fb86-148">Get the base address</span></span>
* <span data-ttu-id="9fb86-149">觸發程式導覽</span><span class="sxs-lookup"><span data-stu-id="9fb86-149">Trigger navigations</span></span>
* <span data-ttu-id="9fb86-150">在位址變更時收到通知</span><span class="sxs-lookup"><span data-stu-id="9fb86-150">Get notified when the address changes</span></span>

<span data-ttu-id="9fb86-151">若要流覽至不同的位址，請使用 `NavigateTo` 方法：</span><span class="sxs-lookup"><span data-stu-id="9fb86-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="9fb86-152">如需所有 @no__t 0 成員的說明，請參閱[URI 和流覽狀態](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers)協助程式。</span><span class="sxs-lookup"><span data-stu-id="9fb86-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="9fb86-153">基底 Url</span><span class="sxs-lookup"><span data-stu-id="9fb86-153">Base URLs</span></span>

<span data-ttu-id="9fb86-154">如果您的 Blazor 應用程式是部署在基底路徑下，則您需要在頁面中繼資料中指定基底 URL，並使用 `<base>` 標記來路由傳送至工作屬性。</span><span class="sxs-lookup"><span data-stu-id="9fb86-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="9fb86-155">如果應用程式的 [主控制項] 頁面是使用 Razor 進行伺服器轉譯，則您可以使用 `~/` 語法來指定應用程式的基底位址。</span><span class="sxs-lookup"><span data-stu-id="9fb86-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="9fb86-156">如果 [主機] 頁面是靜態 HTML，則您需要明確指定基底 URL。</span><span class="sxs-lookup"><span data-stu-id="9fb86-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="9fb86-157">頁面配置</span><span class="sxs-lookup"><span data-stu-id="9fb86-157">Page layout</span></span>

<span data-ttu-id="9fb86-158">ASP.NET Web Forms 中的頁面配置是由主版頁面處理。</span><span class="sxs-lookup"><span data-stu-id="9fb86-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="9fb86-159">主版頁面會定義範本，其中包含一或多個可由個別頁面提供的內容預留位置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="9fb86-160">主版頁面定義于*master*檔案中，並從 `<%@ Master %>` 指示詞開始。</span><span class="sxs-lookup"><span data-stu-id="9fb86-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="9fb86-161">*主要*檔案內容的編碼方式就像是 *.aspx*頁面，但新增了 `<asp:ContentPlaceHolder>` 控制項，以標記頁面可以提供內容的位置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="9fb86-162">*網站. master*</span><span class="sxs-lookup"><span data-stu-id="9fb86-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="9fb86-163">在 Blazor 中，您可以使用版面配置元件來處理頁面配置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="9fb86-164">版面配置元件會繼承自 `LayoutComponentBase`，這會定義類型為 `RenderFragment` 的單一 @no__t 1 屬性，可用來呈現頁面的內容。</span><span class="sxs-lookup"><span data-stu-id="9fb86-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="9fb86-165">*MainLayout razor*</span><span class="sxs-lookup"><span data-stu-id="9fb86-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="9fb86-166">轉譯具有版面配置的頁面時，會在配置呈現其 `Body` 屬性的位置，于指定配置的內容中轉譯頁面。</span><span class="sxs-lookup"><span data-stu-id="9fb86-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="9fb86-167">若要將版面配置套用至頁面，請使用 `@layout` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="9fb86-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="9fb86-168">您可以使用 *_Imports*檔案，為資料夾和子資料夾中的所有元件指定版面配置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="9fb86-169">您也可以使用[路由器元件](#router-component)來指定所有頁面的預設版面配置。</span><span class="sxs-lookup"><span data-stu-id="9fb86-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="9fb86-170">主版頁面可以定義多個內容預留位置，但 Blazor 中的版面配置只有單一的 `Body` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9fb86-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="9fb86-171">Blazor 版面配置元件的這項限制會在未來的版本中解決。</span><span class="sxs-lookup"><span data-stu-id="9fb86-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="9fb86-172">ASP.NET Web Forms 中的主版頁面可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="9fb86-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="9fb86-173">也就是，主版頁面也可以使用主版頁面。</span><span class="sxs-lookup"><span data-stu-id="9fb86-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="9fb86-174">Blazor 中的版面配置元件可能也會進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="9fb86-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="9fb86-175">您可以將版面配置元件套用至版面配置元件。</span><span class="sxs-lookup"><span data-stu-id="9fb86-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="9fb86-176">內部配置的內容將會在外部版面配置中呈現。</span><span class="sxs-lookup"><span data-stu-id="9fb86-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="9fb86-177">*ChildLayout razor*</span><span class="sxs-lookup"><span data-stu-id="9fb86-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="9fb86-178">*Index. razor*</span><span class="sxs-lookup"><span data-stu-id="9fb86-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="9fb86-179">頁面的呈現輸出將會是：</span><span class="sxs-lookup"><span data-stu-id="9fb86-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="9fb86-180">Blazor 中的版面配置通常不會定義頁面的根 HTML 元素（`<html>`、`<body>`、`<head>` 等等）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="9fb86-181">根 HTML 專案會改為定義于 Blazor 應用程式的 [主機] 頁面，用來呈現應用程式的初始 HTML 內容（請參閱[啟動 Blazor](project-structure.md#bootstrap-blazor)）。</span><span class="sxs-lookup"><span data-stu-id="9fb86-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="9fb86-182">[主機] 頁面可以使用周圍標記來呈現應用程式的多個根元件。</span><span class="sxs-lookup"><span data-stu-id="9fb86-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="9fb86-183">Blazor 中的元件（包括頁面）無法轉譯 `<script>` 標記。</span><span class="sxs-lookup"><span data-stu-id="9fb86-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="9fb86-184">這種轉譯限制存在，因為 `<script>` 標記會載入一次，因此無法變更。</span><span class="sxs-lookup"><span data-stu-id="9fb86-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="9fb86-185">如果您嘗試使用 Razor 語法動態呈現標記，可能會發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="9fb86-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="9fb86-186">相反地，所有 @no__t 0 標記都應該新增到應用程式的 [主機] 頁面。</span><span class="sxs-lookup"><span data-stu-id="9fb86-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9fb86-187">[上一頁](components.md)
>[下一頁](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="9fb86-187">[Previous](components.md)
[Next](state-management.md)</span></span>
