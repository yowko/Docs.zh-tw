---
title: 使用 Blazor 建立可重複使用的 UI 元件
description: 瞭解如何使用 Blazor 建立可重複使用的 UI 元件，以及它們與 ASP.NET Web form 控制項之間的比較。
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: b461cf1b572de389c746b894d79d157bf2791e48
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183949"
---
# <a name="build-reusable-ui-components-with-blazor"></a>使用 Blazor 建立可重複使用的 UI 元件

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web form 的其中一項很棒的東西，就是它可以將可重複使用的使用者介面（UI）程式碼片段封裝成可重複使用的 UI 控制項。 您可以使用 *.ascx*檔案，在標記中定義自訂使用者控制項。 您也可以使用完整的設計工具支援，在程式碼中建立精緻的伺服器控制項。

Blazor 也支援透過*元件*的 UI 封裝。 元件：

* 是獨立的 UI 區塊。
* 會維護自己的狀態和轉譯邏輯。
* 可以定義 UI 事件處理常式、系結至輸入資料，以及管理其本身的生命週期。
* 通常會使用 Razor 語法在*razor*檔案中定義。

## <a name="an-introduction-to-razor"></a>Razor 簡介

Razor 是以 HTML 和C#為基礎的輕量標記範本化語言。 使用 Razor，您可以在標記和C#程式碼之間順暢地轉換，以定義您的元件轉譯邏輯。 編譯*razor*檔案時，會在 .net 類別中以結構化的方式來捕獲轉譯邏輯。 已編譯類別的名稱取自*razor*檔案名。 命名空間是從專案的預設命名空間和資料夾路徑取得，或者您可以使用`@namespace`指示詞明確指定命名空間（以下是 Razor 指示詞的詳細資訊）。

元件的轉譯邏輯是使用標準的 HTML 標籤撰寫的，並使用新增C#的動態邏輯。 字元是用來轉換到C# `@` Razor 通常會在您切換回 HTML 時，聰明地找出。 例如，下列元件會呈現`<p>`具有目前時間的標記：

```razor
<p>@DateTime.Now</p>
```

若要明確指定C#運算式的開頭和結尾，請使用括弧：

```razor
<p>@(DateTime.Now)</p>
```

Razor 也可以讓您輕鬆地C#在呈現邏輯中使用控制流程。 例如，您可以有條件地呈現一些 HTML，如下所示：

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

或者，您可以使用一般C# `foreach`迴圈產生專案清單，如下所示：

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

Razor 指示詞（例如 ASP.NET Web form 中的指示詞）控制了 Razor 元件編譯方式的許多層面。 範例包括元件的：

* 命名空間
* 基底類別
* 實作為介面
* 泛型參數
* 匯入的命名空間
* 路由

Razor 指示詞是以`@`字元開頭，而且通常用於檔案開頭的新行開頭。 例如， `@namespace`指示詞會定義元件的命名空間：

```razor
@namespace MyComponentNamespace
```

下表摘要說明 Blazor 中使用的各種 Razor 指示詞，以及其 ASP.NET Web form 對應項（如果有的話）。

|指示詞    |描述|範例|Web Forms 對等|
|-------------|-----------|-------|--------------------|
|`@attribute` |將類別層級屬性加入至元件|`@attribute [Authorize]`|None|
|`@code`      |將類別成員加入至元件|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|執行指定的介面|`@implements IDisposable`|使用程式碼後置|
|`@inherits`  |繼承自指定的基類|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |將服務插入元件|`@inject IJSRuntime JS`|None|
|`@layout`    |指定元件的版面配置元件|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |設定元件的命名空間|`@namespace MyNamespace`|None|
|`@page`      |指定元件的路由|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |指定元件的泛型型別參數|`@typeparam TItem`|使用程式碼後置|
|`@using`     |指定要帶入範圍的命名空間|`@using MyComponentNamespace`|*在 web.config*中新增命名空間|

Razor 元件也會廣泛使用專案上的指示詞*屬性*，以控制元件的編譯方式（事件處理、資料系結、元件 & 專案參考等等）。 指示詞屬性全都遵循通用的泛型語法，其中括弧中的值是選擇性的：

```razor
@directive(-suffix(:name))(="value")
```

下表摘要說明 Blazor 中使用的 Razor 指示詞的各種屬性。

|屬性    |描述|範例|
|-------------|-----------|-------|
|`@attributes`|呈現屬性的字典|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |建立雙向資料系結    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |加入指定事件的事件處理常式|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |指定比較演算法用來保留集合中元素的索引鍵|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |捕捉元件或 HTML 元素的參考|`<MyDialog @ref="myDialog" />`|

Blazor （`@onclick`、 `@bind`、 `@ref`等）所使用的各種指示詞屬性會涵蓋在下列各節和之後的章節中。

*.Aspx*和 *.ascx*檔案中使用的許多語法都具有 Razor 中的平行語法。 以下是 ASP.NET Web Forms 和 Razor 語法的簡單比較。

|功能                      |Web Form           |語法               |Razor         |語法 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|指示詞                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|程式碼區塊                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|運算式<br>（HTML 編碼）|`<%: %>`            |`<%:DateTime.Now %>` |隱`@`<br>確切`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|註解                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|資料繫結                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

若要將成員加入至 Razor 元件類別，請`@code`使用指示詞。 這項技術類似于在 ASP.NET `<script runat="server">...</script>` Web Forms 使用者控制項或頁面中使用區塊。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

因為 Razor 是以C# C#為基礎，所以必須從專案（ *.csproj*）中進行編譯。 您無法從 VB 專案（ *. vbproj*）編譯*razor*檔案。 您仍然可以從 Blazor 專案參考 VB 專案。 相反的情況也是如此。

如需完整的 Razor 語法參考，請參閱[ASP.NET Core 的 Razor 語法參考](/aspnet/core/mvc/views/razor)。

## <a name="use-components"></a>使用元件

除了一般的 HTML 之外，元件也可以使用其他元件做為其轉譯邏輯的一部分。 在 Razor 中使用元件的語法類似于在 ASP.NET Web Forms 應用程式中使用使用者控制項。 元件是使用符合元件型別名稱的元素標記來指定。 例如，您可以新增`Counter`元件，如下所示：

```razor
<Counter />
```

不同于 ASP.NET Web Forms，Blazor 中的元件：

* 請勿使用元素前置詞（ `asp:`例如）。
* 不需要在頁面*或 web.config 中註冊。*

您可以將 Razor 元件視為 .NET 類型，因為這正是它們的意義。 如果參考包含元件的元件，則元件可供使用。 若要將元件的命名空間帶入範圍中， `@using`請套用指示詞：

```razor
@using MyComponentLib

<Counter />
```

如預設 Blazor 專案中所示，通常會將指示詞`@using`放入 *_Imports razor*檔案，使其匯入相同目錄和子目錄中的所有*razor*檔案。

如果元件的命名空間不在範圍內，您可以使用其完整類型名稱來指定元件，如同您在中C#的一樣：

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>元件參數

在 ASP.NET Web Forms 中，您可以使用公用屬性將參數和資料傳送至控制項。 這些屬性可以使用屬性在標記中設定，或直接在程式碼中設定。 Blazor 元件的工作方式類似，雖然元件屬性也必須標記`[Parameter]`為屬性，才能視為元件參數。

下列`Counter`元件會定義名`IncrementAmount`為的元件參數，可以用來`Counter`指定每次按下按鈕時應該遞增的數量。

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

若要在 Blazor 中指定元件參數，請使用屬性，就像您在 ASP.NET Web Forms 中所做的一樣：

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>事件處理常式

ASP.NET Web Forms 和 Blazor 都提供以事件為基礎的程式設計模型來處理 UI 事件。 這類事件的範例包括按鈕點擊和文字輸入。 在 ASP.NET Web Forms 中，您可以使用 HTML 伺服器控制項來處理 DOM 所公開的 UI 事件，也可以處理 Web 服務器控制項所公開的事件。 事件會透過表單回傳要求呈現在伺服器上。 請考慮下列 Web Forms 按鈕的 click 範例：

*計數器 .ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

在 Blazor 中，您可以直接使用表單`@on{event}`的指示詞屬性來註冊 DOM UI 事件的處理常式。 `{event}`預留位置代表事件的名稱。 例如，您可以聆聽按鈕的點擊方式，如下所示：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

事件處理常式可以接受選擇性的事件特定引數，以提供有關事件的詳細資訊。 例如，滑鼠事件可以接受`MouseEventArgs`引數，但不是必要的。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e) 
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

您可以使用 lambda 運算式，而不是參考事件處理常式的方法群組。 Lambda 運算式可讓您關閉其他範圍內的值。

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

事件處理常式可以同步或非同步方式執行。 例如，下列`OnClick`事件處理常式會以非同步方式執行：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick() 
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

處理事件之後，會呈現元件以考慮任何元件狀態變更。 使用非同步事件處理常式時，元件會在處理常式執行完成之後立即轉譯。 此元件會在非同步`Task`完成後再次轉譯。 這個非同步執行模式可讓您在非同步`Task`仍在進行時，呈現一些適當的 UI。

```razor
<button @onclick="Get message">Get message</button>

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

元件也可以定義類型`EventCallback<TValue>`的元件參數，以定義自己的事件。 事件回呼支援 DOM UI 事件處理常式的所有變化：選擇性引數、同步或非同步、方法群組或 lambda 運算式。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>資料繫結

Blazor 提供簡單的機制，可將 UI 元件的資料系結至元件的狀態。 此方法不同于 ASP.NET Web form 中的功能，可將資料從資料來源系結至 UI 控制項。 在[處理資料](data.md)一節中，我們將討論如何處理來自不同資料來源的資料。

若要從 UI 元件建立雙向資料系結至元件的狀態，請使用`@bind`指示詞屬性。 在下列範例中，核取方塊的值會系結至`isChecked`欄位。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

當元件呈現時，核取方塊的值會設定為`isChecked`欄位的值。 當使用者切換核取方塊時， `onchange`就會引發事件， `isChecked`並將欄位設定為新的值。 此`@bind`案例中的語法相當於下列標記：

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

若要變更用於系結的事件，請使用`@bind:event`屬性。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

元件也可以支援資料系結至其參數。 若要進行資料系結，請使用與可系結參數相同的名稱來定義事件回呼參數。 「已變更」尾碼會新增至名稱。

*PasswordBox razor*

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

若要將資料系結連結至基礎 UI 專案，請設定值，並直接在 UI 元素上處理事件，而不`@bind`使用屬性。

若要系結至元件參數，請`@bind-{Parameter}`使用屬性來指定您要系結的參數。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>狀態變更

如果元件的狀態在一般 UI 事件或事件回呼之外已變更，則元件必須手動指示需要再次轉譯。 若要通知元件的狀態已變更，請在元件`StateHasChanged`上呼叫方法。

在下面的範例中，元件會顯示來自`AppState`服務的訊息，而應用程式的其他部分可加以更新。 元件會`StateHasChanged` `AppState.OnChange`向事件註冊其方法，以便在每次更新訊息時呈現該元件。

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

## <a name="component-lifecycle"></a>元件生命週期

ASP.NET Web form 架構具有定義完善的模組、頁面和控制項生命週期方法。 例如，下列控制項會執行`Init`、 `Load`和`UnLoad`週期事件的事件處理常式：

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor 元件也有定義完善的生命週期。 元件的生命週期可用來初始化元件狀態和執行 advanced 元件行為。 

所有 Blazor 的元件生命週期方法都有同步和非同步版本。 元件呈現是同步的。 您無法在元件轉譯過程中執行非同步邏輯。 所有非同步邏輯都必須當做`async`生命週期方法的一部分來執行。

### <a name="oninitialized"></a>OnInitialized

`OnInitialized` 和`OnInitializedAsync`方法是用來初始化元件。 元件通常會在第一次呈現之後初始化。 元件初始化之後，它可能會轉譯多次，最後才會被處置。 方法類似于 ASP.NET Web Forms `Page_Load`頁面和控制項中的事件。 `OnInitialized`

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

當元件`OnParametersSetAsync`已從其父系接收參數，且已將值指派給屬性時，會呼叫和方法。`OnParametersSet` 這些方法會在元件初始化之後和*每次呈現元件時*執行。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

在元件`OnAfterRenderAsync`完成呈現之後，會呼叫和方法。`OnAfterRender` 此時會填入元素和元件參考（以下是這些概念的詳細資訊）。 此時會啟用與瀏覽器的互動。 可以安全地進行與 DOM 的互動和 JavaScript 的執行。 

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

`OnAfterRender`在`OnAfterRenderAsync` *伺服器上進行預呈現時，不會呼叫*和。

參數是`true`第一次轉譯元件時，否則其值為`false`。 `firstRender`

### <a name="idisposable"></a>IDisposable

當元件從 UI `IDisposable`中移除時，Blazor 元件可以執行來處置資源。 Razor 元件可以`@implements`使用指示`IDispose`詞來執行：

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

## <a name="capture-component-references"></a>捕捉元件參考

在 ASP.NET Web form 中，通常會藉由參考其識別碼，直接在程式碼中操作控制項實例。 在 Blazor 中，您也可以捕捉和操作元件的參考，不過這種情況較不常見。

若要在 Blazor 中捕捉元件參考，請`@ref`使用指示詞屬性。 屬性的值應該符合可設定欄位的名稱，其類型與參考的元件相同。

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

當父代元件呈現時，欄位會填入子元件實例。 接著，您可以呼叫或操作元件實例上的方法。

不建議直接使用元件參考來操作元件狀態。 這麼做可防止元件在正確的時間自動轉譯。

## <a name="capture-element-references"></a>Capture 元素參考

Blazor 元件可以捕捉元素的參考。 不同于 ASP.NET Web Forms 中的 HTML 伺服器控制項，您無法直接使用 Blazor 中的專案參考來操作 DOM。 Blazor 會使用其 DOM 比較演算法，為您處理大部分的 DOM 互動。 Blazor 中的已捕捉元素參考是不透明的。 不過，它們是用來傳遞 JavaScript interop 呼叫中的特定元素參考。 如需 JavaScript interop 的詳細資訊，請參閱[ASP.NET Core Blazor javascript interop](/aspnet/core/blazor/javascript-interop)。

## <a name="templated-components"></a>樣板化元件

在 ASP.NET Web Forms 中，您可以建立樣板*化控制項*。 樣板化控制項可讓開發人員指定用來呈現容器控制項的 HTML 部分。 建立樣板化伺服器控制項的機制很複雜，但它們可以讓您以可自訂的方式呈現資料的強大案例。 樣板化控制項的範例`Repeater`包括`DataList`和。 

您也可以藉由定義或`RenderFragment` `RenderFragment<T>`類型的元件參數，將 Blazor 元件樣板化。 `RenderFragment`代表 Razor 標記的區塊，可由元件呈現。 `RenderFragment<T>`是 Razor 標記的區塊，它會接受呈現轉譯片段時可指定的參數。

### <a name="child-content"></a>子內容

Blazor 元件可以將`RenderFragment`其子內容捕捉為，並將該內容轉譯為元件轉譯的一部分。 若要捕獲子內容，請定義類型`RenderFragment`的元件參數，並將它`ChildContent`命名為。

*ChildContentComponent razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

然後，父系元件可以使用一般 Razor 語法來提供子內容。

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>範本參數

樣板化 Blazor 元件也可以定義多個類型`RenderFragment`的元件參數或。 `RenderFragment<T>` 當叫用`RenderFragment<T>`時，可以指定的參數。 若要指定元件的泛型型別參數，請使用`@typeparam` Razor 指示詞。

*SimpleListView razor*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in items)
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

使用樣板化元件時，可以使用符合參數名稱的子項目來指定範本參數。 當做元素傳遞之`RenderFragment<T>`類型的元件引數具有名為`context`的隱含參數。 您可以使用子項目上的`Context`屬性來變更這個實參數的名稱。 您可以使用符合型別參數名稱的屬性來指定任何泛型型別參數。 可能的話，會推斷型別參數：

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

此元件的輸出看起來像這樣：

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>程式碼後置

Blazor 元件通常是在單一的*razor*檔案中撰寫。 不過，也可以使用程式碼後置檔案來分隔程式碼和標記。 若要使用元件檔案，請新增C#符合元件檔檔案名的檔案，但已加入 *.cs*副檔名（*Counter.razor.cs*）。 C#使用檔案來定義元件的基類。 您可以將基類命名為任何您想要的名稱，但通常會將類別命名為與 component 類別相同，但`Base`已加入延伸模組（`CounterBase`）。 以元件為基礎的類別也必須衍生`ComponentBase`自。 然後，在 Razor 元件檔案中，加入`@inherits`指示詞以指定元件的基類（`@inherits CounterBase`）。

*Counter. razor*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

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

元件的成員在基類中的可見度必須是`protected`或`public` ，才能顯示在元件類別中。

## <a name="additional-resources"></a>其他資源

上述並不是 Blazor 元件所有層面的完整處理。 如需如何[建立和使用 Razor 元件 ASP.NET Core](/aspnet/core/blazor/components)的詳細資訊，請參閱 Blazor 檔。

>[!div class="step-by-step"]
>[上一頁](app-startup.md)
>[下一頁](pages-routing-layouts.md)
