---
title: 使用建立可重複使用的 UI 元件 Blazor
description: 瞭解如何建立可重複使用的 UI 元件 Blazor ，以及它們與 ASP.NET Web Forms 控制項的比較方式。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: 4fdf062fb719e62b53e47f79db1e93d0bf079350
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267681"
---
# <a name="build-reusable-ui-components-with-no-locblazor"></a>使用建立可重複使用的 UI 元件 Blazor

ASP.NET Web Forms 的其中一項很美觀的事，就是它如何能夠將可重複使用的使用者介面 (UI) 程式碼封裝成可重複使用的 UI 控制項。 自訂使用者控制項可以使用 *.ascx* 檔在標記中定義。 您也可以使用完整的設計工具支援，在程式碼中建立詳盡的伺服器控制項。

Blazor 也支援透過 *元件*的 UI 封裝。 元件：

- 是獨立的 UI 區塊。
- 維護其本身的狀態和轉譯邏輯。
- 可以定義 UI 事件處理常式、系結至輸入資料，以及管理它自己的生命週期。
- 通常是使用 Razor 語法在 *razor* 檔案中定義。

## <a name="an-introduction-to-razor"></a>Razor 簡介

Razor 是以 HTML 和 c # 為基礎的輕量標記範本化語言。 使用 Razor，您可以在標記和 c # 程式碼之間順暢地轉換，以定義您的元件轉譯邏輯。 編譯 *razor* 檔案時，會以結構化方式在 .net 類別中捕捉轉譯邏輯。 已編譯類別的名稱取自 *razor* 檔案名。 命名空間取自專案的預設命名空間和資料夾路徑，或者您也可以使用指示詞明確指定命名空間， `@namespace` (更多有關) 的 Razor 指示詞。

元件的轉譯邏輯是使用一般 HTML 標籤來撰寫，並使用 c # 新增動態邏輯。 `@`字元用來轉換至 c #。 Razor 通常會在您切換回 HTML 時，很聰明地搞清楚。 例如，下列元件會 `<p>` 以目前的時間呈現標記：

```razor
<p>@DateTime.Now</p>
```

若要明確指定 c # 運算式的開頭和結尾，請使用括弧：

```razor
<p>@(DateTime.Now)</p>
```

Razor 也可讓您輕鬆地在轉譯邏輯中使用 c # 控制流程。 例如，您可以有條件地轉譯一些 HTML，如下所示：

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

或者，您可以使用一般 c # 迴圈來產生專案清單， `foreach` 如下所示：

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor 指示詞（例如 ASP.NET Web Forms 中的指示詞）會控制 Razor 元件編譯方式的許多層面。 範例包括元件的：

- 命名空間
- 基底類別
- 實作為介面
- 泛型參數
- 匯入的命名空間
- 路由

Razor 指示詞以 `@` 字元開頭，通常是在檔案開頭的新行開頭使用。 例如，指示詞會 `@namespace` 定義元件的命名空間：

```razor
@namespace MyComponentNamespace
```

下表摘要說明中使用的各種 Razor 指示詞 Blazor ，以及它們的 ASP.NET Web Forms 對等專案（如果有的話）。

|指示詞    |描述|範例|Web Form 相等|
|-------------|-----------|-------|--------------------|
|`@attribute` |將類別層級屬性加入至元件|`@attribute [Authorize]`|None|
|`@code`      |將類別成員新增至元件|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|實行指定的介面|`@implements IDisposable`|使用程式碼後置|
|`@inherits`  |繼承自指定的基類|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |將服務插入元件|`@inject IJSRuntime JS`|None|
|`@layout`    |指定元件的版面配置元件|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |設定元件的命名空間|`@namespace MyNamespace`|None|
|`@page`      |指定元件的路由|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |指定元件的泛型型別參數|`@typeparam TItem`|使用程式碼後置|
|`@using`     |指定要帶入範圍內的命名空間|`@using MyComponentNamespace`|在*web.config*中新增命名空間|

Razor 元件也廣泛使用元素上的指示詞 *屬性* ，來控制如何編譯元件 (事件處理、資料系結、元件 & 專案參考等等，以及) 。 指示詞屬性全都遵循一般一般語法，其中括弧中的值是選擇性的：

```razor
@directive(-suffix(:name))(="value")
```

下表摘要說明中所使用之 Razor 指示詞的各種屬性 Blazor 。

|屬性    |描述|範例|
|-------------|-----------|-------|
|`@attributes`|呈現屬性的字典|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |建立雙向資料系結    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |加入指定之事件的事件處理常式。|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |指定要由比較演算法用來保留集合中元素的索引鍵|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |捕捉元件或 HTML 元素的參考|`<MyDialog @ref="myDialog" />`|

 (、、等) 所使用的各種指示詞屬性， Blazor `@onclick` `@bind` `@ref` 將在下列各節和後續章節中討論。

*.Aspx*和 *.ascx*檔案中使用的許多語法在 Razor 中都有平行語法。 以下是 ASP.NET Web Forms 和 Razor 語法的簡單比較。

|功能                      |Web Form           |語法               |Razor         |語法 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|指示詞                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|程式碼區塊                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|運算式<br> (HTML 編碼的) |`<%: %>`            |`<%:DateTime.Now %>` |隱 式： `@`<br>明確： `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|註解                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|資料繫結                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

若要將成員加入 Razor 元件類別，請使用指示詞 `@code` 。 這項技術類似于 `<script runat="server">...</script>` 在 ASP.NET Web Forms 使用者控制項或頁面中使用區塊。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

因為 Razor 是以 c # 為基礎，所以必須在 c # 專案中編譯， (*.csproj*) 。 您無法從 Visual Basic 專案編譯 *razor* 檔案， (*. vbproj*) 。 您仍然可以參考專案中的 Visual Basic 專案 Blazor 。 相反的也是如此。

如需完整 Razor 語法參考，請參閱 [ASP.NET Core 的 Razor 語法參考](/aspnet/core/mvc/views/razor)。

## <a name="use-components"></a>使用元件

除了一般的 HTML，元件也可以使用其他元件作為轉譯邏輯的一部分。 在 Razor 中使用元件的語法類似于在 ASP.NET Web Forms 應用程式中使用使用者控制項。 元件是使用符合元件型別名稱的元素標記來指定。 例如，您可以新增如下的 `Counter` 元件：

```razor
<Counter />
```

不同于 ASP.NET Web Forms，中的元件 Blazor ：

- 請勿使用元素首碼 (例如 `asp:`) 。
- 不需要在頁面或 *web.config*中註冊。

您可以把 Razor 元件想像成像是 .NET 型別，因為這正是它們的意思。 如果參考包含元件的元件，則元件可供使用。 若要將元件的命名空間帶入範圍中，請套用指示詞 `@using` ：

```razor
@using MyComponentLib

<Counter />
```

如同在預設專案中所見 Blazor ，通常會將指示詞放入 `@using` _Imports 的 *razor* 檔案中，以便將它們匯入至相同目錄和子目錄中的所有 *razor* 檔案。

如果元件的命名空間不在範圍內，您可以使用其完整類型名稱來指定元件，如同您在 c # 中所能使用的一樣：

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>元件參數

在 ASP.NET Web Forms 中，您可以使用公用屬性將參數和資料傳送給控制項。 您可以使用屬性在標記中設定這些屬性，或直接在程式碼中設定這些屬性。 Blazor 元件的運作方式類似，雖然元件屬性也必須以屬性標記，才能被 `[Parameter]` 視為元件參數。

下列 `Counter` 元件會定義一個名為的元件參數 `IncrementAmount` ，可用來指定 `Counter` 每次按下按鈕時，應該遞增的數量。

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

若要在中指定元件參數 Blazor ，請使用屬性，就像您在 ASP.NET Web Forms 中所做的一樣：

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>事件處理常式

兩者都 ASP.NET Web Forms，並 Blazor 提供以事件為基礎的程式設計模型來處理 UI 事件。 這類事件的範例包括按鈕點擊和文字輸入。 在 ASP.NET Web Forms 中，您可以使用 HTML 伺服器控制項來處理 DOM 所公開的 UI 事件，也可以處理 Web 服務器控制項所公開的事件。 系統會透過表單回傳要求，在伺服器上呈現事件。 請考慮下列 Web Form 按鈕點擊範例：

*Counter*

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

在中 Blazor ，您可以使用表單的指示詞屬性，直接註冊 DOM UI 事件的處理常式 `@on{event}` 。 `{event}`預留位置代表事件的名稱。 例如，您可以聆聽按鈕的點擊方式，如下所示：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

事件處理常式可以接受選擇性的事件特定引數，以提供有關事件的詳細資訊。 例如，滑鼠事件可以採用 `MouseEventArgs` 引數，但不是必要的。

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

事件處理常式可以同步或非同步方式執行。 例如，下列 `OnClick` 事件處理常式會以非同步方式執行：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

處理事件之後，會轉譯元件以考慮任何元件狀態變更。 使用非同步事件處理常式時，元件會在處理常式執行完成後立即轉譯。 此元件會在非同步完成後 *再次* 轉譯 `Task` 。 這種非同步執行模式可在非同步仍在進行時，提供轉譯一些適當 UI 的機會 `Task` 。

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

元件也可以定義型別的元件參數，以定義自己的事件 `EventCallback<TValue>` 。 事件回呼支援 DOM UI 事件處理常式的所有變化：選擇性引數、同步或非同步、方法群組或 lambda 運算式。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>資料繫結

Blazor 提供簡單的機制，可將 UI 元件的資料系結至元件的狀態。 這種方法不同于 ASP.NET Web Forms 中的功能，可將資料從資料來源系結至 UI 控制項。 我們將在處理 [資料](data.md) 一節中討論如何處理來自不同資料來源的資料。

若要從 UI 元件建立雙向資料系結至元件的狀態，請使用指示詞 `@bind` 屬性。 在下列範例中，核取方塊的值會系結至 `isChecked` 欄位。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

轉譯元件時，核取方塊的值會設定為欄位的值 `isChecked` 。 當使用者切換核取方塊時， `onchange` 就會引發事件，並將 `isChecked` 欄位設定為新的值。 `@bind`此案例中的語法相當於下列標記：

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

若要變更系結所使用的事件，請使用 `@bind:event` 屬性。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

元件也可以支援其參數的資料系結。 若為數據系結，請使用與可系結參數相同的名稱來定義事件回呼參數。 名稱中會新增「已變更」尾碼。

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

若要將資料系結至基礎 UI 元素，請設定值，並直接在 UI 元素上處理事件，而不是使用 `@bind` 屬性。

若要系結至元件參數，請使用 `@bind-{Parameter}` 屬性來指定您要系結的參數。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>狀態變更

如果元件的狀態在正常的 UI 事件或事件回呼之外變更，則元件必須手動表示它需要再次轉譯。 若要指示元件的狀態已變更，請 `StateHasChanged` 在元件上呼叫方法。

在下列範例中，元件 `AppState` 會顯示服務的訊息，該訊息可由應用程式的其他部分進行更新。 元件 `StateHasChanged` 會向事件註冊其方法， `AppState.OnChange` 以便在每次更新訊息時轉譯元件。

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

## <a name="component-lifecycle"></a>元件生命週期

ASP.NET Web Forms 架構具有定義完善的模組、頁面和控制項生命週期方法。 例如，下列控制項會 `Init` `Load` 執行、和 `UnLoad` 生命週期事件的事件處理常式：

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor 元件也有妥善定義的生命週期。 元件的生命週期可以用來初始化元件狀態並執行 advanced 元件行為。

所有 Blazor 的元件生命週期方法都有同步和非同步版本。 元件呈現是同步的。 您無法在元件呈現過程中執行非同步邏輯。 所有非同步邏輯都必須作為生命週期方法的一部分來執行 `async` 。

### <a name="oninitialized"></a>OnInitialized

`OnInitialized`和 `OnInitializedAsync` 方法是用來初始化元件。 元件通常會在第一次呈現之後初始化。 元件在初始化之後，可能會在最後處置之前多次轉譯。 `OnInitialized`方法類似于 `Page_Load` ASP.NET Web Forms 頁面和控制項中的事件。

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

`OnParametersSet` `OnParametersSetAsync` 當元件從其父系收到參數，且將值指派給屬性時，會呼叫和方法。 這些方法會在元件初始化之後，以及 *每次轉譯元件*之後執行。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

在 `OnAfterRender` `OnAfterRenderAsync` 元件完成轉譯之後，會呼叫和方法。 此時會填入元素和元件參考， () 以下概念的詳細資訊。 目前已啟用與瀏覽器的互動。 您可以安全地進行與 DOM 的互動和 JavaScript 執行。

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

`OnAfterRender` 在 `OnAfterRenderAsync` *伺服器上進行預呈現時，不會呼叫*。

`firstRender`參數是 `true` 第一次轉譯元件，否則它的值為 `false` 。

### <a name="idisposable"></a>IDisposable

Blazor 元件可以在 `IDisposable` 元件從 UI 中移除時，執行以處置資源。 Razor 元件可以使用指示詞來執行 `IDispose` `@implements` ：

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

## <a name="capture-component-references"></a>捕獲元件參考

在 ASP.NET Web Forms 中，通常會藉由參考其識別碼，直接在程式碼中操作控制項實例。 在中 Blazor ，您也可以捕獲和操作元件的參考，不過這種情況較不常見。

若要在中捕捉元件參考 Blazor ，請使用指示詞 `@ref` 屬性。 屬性的值應該符合可設定欄位的名稱，該欄位與參考的元件具有相同的類型。

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

當轉譯父元件時，此欄位會填入子元件實例。 然後，您可以在元件實例上呼叫方法，或以其他方式操作。

不建議使用元件參考直接操作元件狀態。 這樣做可防止元件在正確的時間自動轉譯。

## <a name="capture-element-references"></a>Capture 元素參考

Blazor 元件可以捕獲元素的參考。 不同于 ASP.NET Web Forms 中的 HTML 伺服器控制項，您無法直接使用中的專案參考來操作 DOM Blazor 。 Blazor 使用其 DOM 比較演算法，為您處理大部分的 DOM 互動。 中的已捕捉元素參考 Blazor 不是透明的。 不過，它們是用來在 JavaScript interop 呼叫中傳遞特定的元素參考。 如需 JavaScript interop 的詳細資訊，請參閱 [ASP.NET Core Blazor javascript interop](/aspnet/core/blazor/javascript-interop)。

## <a name="templated-components"></a>樣板化元件

在 ASP.NET Web Forms 中，您可以建立樣板 *化控制項*。 樣板化控制項可讓開發人員指定用來呈現容器控制項的 HTML 部分。 建立樣板化伺服器控制項的機制很複雜，但是可讓您以使用者自訂的方式來呈現資料的強大案例。 樣板化控制項的範例包括 `Repeater` 和 `DataList` 。

Blazor 元件也可以藉由定義類型或的元件參數來樣板化 `RenderFragment` `RenderFragment<T>` 。 `RenderFragment`代表 Razor 標記的區塊，該區塊可接著由元件呈現。 `RenderFragment<T>`是 Razor 標記的區塊，會採用轉譯片段轉譯時可指定的參數。

### <a name="child-content"></a>子內容

Blazor 元件可以將其子內容視為的 `RenderFragment` 一部分，並在呈現元件時轉譯該內容。 若要捕捉子內容，請定義類型的元件參數， `RenderFragment` 並為其命名 `ChildContent` 。

*ChildContentComponent razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

父元件接著可以使用一般 Razor 語法來提供子內容。

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>範本參數

樣板化 Blazor 元件也可以定義多個或類型的元件參數 `RenderFragment` `RenderFragment<T>` 。 當叫用 `RenderFragment<T>` 時，可以指定的參數。 若要指定元件的泛型型別參數，請使用 `@typeparam` Razor 指示詞。

*SimpleListView razor*

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

使用樣板化元件時，可以使用符合參數名稱的子專案來指定範本參數。 以元素形式傳遞之類型的元件引數 `RenderFragment<T>` 具有名為的隱含參數 `context` 。 您可以使用子項目上的屬性來變更這個實參數的名稱 `Context` 。 您可以使用符合型別參數名稱的屬性來指定任何泛型型別參數。 如果可能的話，將會推斷類型參數：

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

此元件的輸出如下所示：

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a>程式碼後置

Blazor元件通常會在單一的*razor*檔案中撰寫。 不過，您也可以使用程式碼後端檔案來分隔程式碼和標記。 若要使用元件檔，請新增符合元件檔檔案名的 c # 檔案，但副檔名為 *.cs* 的 (*Counter.razor.cs*) 。 使用 c # 檔案來定義元件的基類。 您可以將基類命名為任何您想要的名稱，但通常會將該類別命名為與 component 類別相同，但是擴充功能會 `Base` 新增 (`CounterBase`) 。 以元件為基礎的類別也必須衍生自 `ComponentBase` 。 然後，在 Razor 元件檔中加入指示詞， `@inherits` 以指定元件 () 的基類 `@inherits CounterBase` 。

*計數器 razor*

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

元件類別的元件成員在基類中的可見度必須是 `protected` 或 `public` 可見。

## <a name="additional-resources"></a>其他資源

上述不是元件的所有層面的完整處理方式 Blazor 。 如需有關如何 [建立和使用 ASP.NET Core Razor 元件](/aspnet/core/blazor/components)的詳細資訊，請參閱 Blazor 檔。

>[!div class="step-by-step"]
>[上一個](app-startup.md) 
>[下一步](pages-routing-layouts.md)
