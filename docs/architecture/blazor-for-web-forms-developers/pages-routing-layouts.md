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
# <a name="pages-routing-and-layouts"></a>頁面、路由和版面配置

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms 應用程式是由 *.aspx*檔案中定義的頁面所組成。 每個頁面的位址都是以專案中的實體檔案路徑為基礎。 當瀏覽器對頁面提出要求時，頁面的內容會在伺服器上以動態方式呈現。 頁面的 HTML 標籤和其伺服器控制項的轉譯帳戶。

在 Blazor 中，應用程式中的每個頁面都是一個元件，通常是在*razor*檔案中定義，其中包含一或多個指定的路由。 路由大部分會發生在用戶端，而不涉及特定的伺服器要求。 瀏覽器會先對應用程式的根位址提出要求。 Blazor 應用程式中的根 @no__t 0 元件會接著處理攔截導覽要求，並將它們傳送至正確的元件。

Blazor 也支援*深層連結*。 當瀏覽器對應用程式根目錄以外的特定路由提出要求時，就會發生深層連結。 傳送到伺服器之深層連結的要求會路由傳送至 Blazor 應用程式，然後將要求用戶端路由傳送至正確的元件。

ASP.NET Web Forms 中的簡單頁面可能會包含下列標記：

*名稱 .aspx*

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

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

Blazor 應用程式中的對等頁面看起來會像這樣：

*名稱. razor*

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

## <a name="create-pages"></a>建立頁面

若要在 Blazor 中建立頁面，請建立元件，並新增 `@page` Razor 指示詞來指定元件的路由。 @No__t-0 指示詞接受單一參數，也就是要新增至該元件的路由範本。

```razor
@page "/counter"
```

需要路由範本參數。 不同于 ASP.NET Web form，Blazor 元件的路由*不*會從其檔案位置推斷（雖然這可能是未來新增的功能）。

路由範本語法與 ASP.NET Web Forms 中的路由所使用的基本語法相同。 使用大括弧在範本中指定路由參數。 Blazor 會將路由值系結至具有相同名稱的元件參數（不區分大小寫）。

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

您也可以在 route 參數的值上指定條件約束。 例如，若要將產品識別碼限制為 `int`：

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

如需 Blazor 所支援之路由條件約束的完整清單，請參閱[路由條件約束](/aspnet/core/blazor/routing#route-constraints)。

## <a name="router-component"></a>路由器元件

Blazor 中的路由是由 `Router` 元件所處理。 @No__t-0 元件通常用於應用程式的根元件（*razor*）。

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

@No__t-0 元件會探索指定的 `AppAssembly` 中的可路由元件，以及選擇性地指定 `AdditionalAssemblies`。 當瀏覽器導覽時，`Router` 會攔截導覽，並以解壓縮的 `RouteData` 來呈現其 @no__t 1 參數的內容（如果路由符合位址），否則 `Router` 會轉譯其 `NotFound` 參數。

@No__t 0 元件會處理呈現 `RouteData` 所指定的相符元件及其配置（如果有的話）。 如果相符的元件沒有版面配置，則會使用選擇性指定的 `DefaultLayout`。

@No__t-0 元件會在指定的版面配置內呈現其子內容。 我們將在本章稍後詳細探討版面配置。

## <a name="navigation"></a>巡覽

在 ASP.NET Web form 中，您可以藉由將重新導向回應傳回至瀏覽器，來觸發導覽至不同頁面。 例如:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

在 Blazor 中，通常不可能傳回重新導向回應。 Blazor 不會使用要求-回復模型。 不過，您可以直接觸發瀏覽器導覽，就像使用 JavaScript 一樣。

Blazor 提供的 `NavigationManager` 服務可用於：

* 取得目前的瀏覽器位址
* 取得基底位址
* 觸發程式導覽
* 在位址變更時收到通知

若要流覽至不同的位址，請使用 `NavigateTo` 方法：

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

如需所有 @no__t 0 成員的說明，請參閱[URI 和流覽狀態](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers)協助程式。

## <a name="base-urls"></a>基底 Url

如果您的 Blazor 應用程式是部署在基底路徑下，則您需要在頁面中繼資料中指定基底 URL，並使用 `<base>` 標記來路由傳送至工作屬性。 如果應用程式的 [主控制項] 頁面是使用 Razor 進行伺服器轉譯，則您可以使用 `~/` 語法來指定應用程式的基底位址。 如果 [主機] 頁面是靜態 HTML，則您需要明確指定基底 URL。

```html
<base href="~/" />
```

## <a name="page-layout"></a>頁面配置

ASP.NET Web Forms 中的頁面配置是由主版頁面處理。 主版頁面會定義範本，其中包含一或多個可由個別頁面提供的內容預留位置。 主版頁面定義于*master*檔案中，並從 `<%@ Master %>` 指示詞開始。 *主要*檔案內容的編碼方式就像是 *.aspx*頁面，但新增了 `<asp:ContentPlaceHolder>` 控制項，以標記頁面可以提供內容的位置。

*網站. master*

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

在 Blazor 中，您可以使用版面配置元件來處理頁面配置。 版面配置元件會繼承自 `LayoutComponentBase`，這會定義類型為 `RenderFragment` 的單一 @no__t 1 屬性，可用來呈現頁面的內容。

*MainLayout razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

轉譯具有版面配置的頁面時，會在配置呈現其 `Body` 屬性的位置，于指定配置的內容中轉譯頁面。

若要將版面配置套用至頁面，請使用 `@layout` 指示詞：

```razor
@layout MainLayout
```

您可以使用 *_Imports*檔案，為資料夾和子資料夾中的所有元件指定版面配置。 您也可以使用[路由器元件](#router-component)來指定所有頁面的預設版面配置。

主版頁面可以定義多個內容預留位置，但 Blazor 中的版面配置只有單一的 `Body` 屬性。 Blazor 版面配置元件的這項限制會在未來的版本中解決。

ASP.NET Web Forms 中的主版頁面可以嵌套。 也就是，主版頁面也可以使用主版頁面。 Blazor 中的版面配置元件可能也會進行嵌套。 您可以將版面配置元件套用至版面配置元件。 內部配置的內容將會在外部版面配置中呈現。

*ChildLayout razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index. razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

頁面的呈現輸出將會是：

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Blazor 中的版面配置通常不會定義頁面的根 HTML 元素（`<html>`、`<body>`、`<head>` 等等）。 根 HTML 專案會改為定義于 Blazor 應用程式的 [主機] 頁面，用來呈現應用程式的初始 HTML 內容（請參閱[啟動 Blazor](project-structure.md#bootstrap-blazor)）。 [主機] 頁面可以使用周圍標記來呈現應用程式的多個根元件。

Blazor 中的元件（包括頁面）無法轉譯 `<script>` 標記。 這種轉譯限制存在，因為 `<script>` 標記會載入一次，因此無法變更。 如果您嘗試使用 Razor 語法動態呈現標記，可能會發生非預期的行為。 相反地，所有 @no__t 0 標記都應該新增到應用程式的 [主機] 頁面。

>[!div class="step-by-step"]
>[上一頁](components.md)
>[下一頁](state-management.md)
