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
# <a name="build-reusable-ui-components-with-blazor"></a>使用 Blazor 構建可重用的 UI 元件

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web 表單中一個美妙的事情是，它如何將可重用的使用者介面 （UI） 代碼封裝到可重用的 UI 控制項中。 可以使用 *.ascx*檔在標記中定義自訂使用者控制項。 您還可以在代碼中構建詳細的伺服器控制項，並支援完全設計人員。

Blazor 還支援通過*元件*進行 UI 封裝。 元件：

- 是 UI 的自包含塊。
- 維護自己的狀態和呈現邏輯。
- 可以定義 UI 事件處理常式、綁定到輸入資料以及管理其自己的生命週期。
- 通常在使用 Razor 語法的 *.razor*檔中定義。

## <a name="an-introduction-to-razor"></a>剃刀簡介

Razor 是基於 HTML 和 C# 的羽量級標記範本化語言。 使用 Razor，您可以在標記和 C# 代碼之間無縫過渡，以定義元件呈現邏輯。 編譯 *.razor*檔時，呈現邏輯以結構化方式在 .NET 類中捕獲。 已編譯類的名稱取自 *.razor*檔案名。 命名空間取自專案和資料夾路徑的預設命名空間，或者您可以使用`@namespace`指令顯式指定命名空間（下面有關 Razor 指令的更多）。

元件的呈現邏輯使用使用使用 C# 添加的動態邏輯使用普通 HTML 標籤進行創作。 該`@`字元用於轉換為 C#。 剃刀通常很聰明，可以找出您何時切換回 HTML。 例如，以下元件呈現當前`<p>`時間的標記：

```razor
<p>@DateTime.Now</p>
```

要顯式指定 C# 運算式的開始和結束，請使用括弧：

```razor
<p>@(DateTime.Now)</p>
```

Razor 還便於在渲染邏輯中使用 C# 控制流。 例如，您可以有條件地呈現一些 HTML，如下所示：

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

或者，您可以使用正常的 C#`foreach`迴圈生成項清單，如下所示：

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor 指令（如ASP.NET Web 表單中的指令）控制 Razor 元件的編譯方式的許多方面。 示例包括元件：

- 命名空間
- 基底類別
- 實現的介面
- 泛型參數
- 匯入的命名空間
- 路由

Razor 指令以`@`字元開頭，通常在檔開頭的新行開始時使用。 例如，`@namespace`指令定義元件的命名空間：

```razor
@namespace MyComponentNamespace
```

下表總結了 Blazor 中使用的各種 Razor 指令及其ASP.NET Web 表單等效項（如果存在）。

|指示詞    |描述|範例|與 Web 表單等效|
|-------------|-----------|-------|--------------------|
|`@attribute` |向元件添加類級屬性|`@attribute [Authorize]`|None|
|`@code`      |將類成員添加到元件|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|實現指定的介面|`@implements IDisposable`|使用程式碼後置|
|`@inherits`  |從指定的基類繼承|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |將服務注入元件|`@inject IJSRuntime JS`|None|
|`@layout`    |指定元件的佈局元件|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |設置元件的命名空間|`@namespace MyNamespace`|None|
|`@page`      |指定元件的路由|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |為元件指定泛型型別參數|`@typeparam TItem`|使用程式碼後置|
|`@using`     |指定要引入作用域的命名空間|`@using MyComponentNamespace`|在*Web.config 中*添加命名空間|

Razor 元件還廣泛使用元素上的*指令屬性*來控制元件的編譯方式的各個方面（事件處理、資料繫結、元件&元素引用等）。 指令屬性都遵循一個通用通用語法，其中括弧中的值是可選的：

```razor
@directive(-suffix(:name))(="value")
```

下表總結了 Blazor 中使用的 Razor 指令的各種屬性。

|屬性    |描述|範例|
|-------------|-----------|-------|
|`@attributes`|渲染屬性字典|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |創建雙向資料繫結    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |為指定事件添加事件處理常式|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |指定擴散演算法用於保留集合中元素的鍵|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |捕獲對元件或 HTML 元素的引用|`<MyDialog @ref="myDialog" />`|

Blazor （、、、`@onclick``@bind``@ref`等） 使用的各種指令屬性在以下各章和後面的章節仲介紹。

*.aspx*和 *.ascx*檔中使用的許多語法在 Razor 中具有並行語法。 下面是ASP.NET Web 表單和 Razor 的語法的簡單比較。

|功能                      |Web Form           |語法               |Razor         |語法 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|指示詞                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|程式碼區塊                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|運算式<br>（HTML 編碼）|`<%: %>`            |`<%:DateTime.Now %>` |隱 式：`@`<br>明確：`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|註解                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|資料繫結                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

要將成員添加到 Razor 元件類，請使用`@code`該指令。 此技術類似于在ASP.NET Web`<script runat="server">...</script>`表單使用者控制項或頁面中使用塊。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

由於 Razor 基於 C#，因此必須從 C# 專案中編譯它 （*.csproj*）。 無法從視覺化基礎專案 *（.vbproj*） 編譯 *.razor*檔。 您仍然可以從 Blazor 專案中引用視覺化基本專案。 事實正好相反。

有關完整的 Razor 語法引用，請參閱[ASP.NET 酷睿的 Razor 語法引用](/aspnet/core/mvc/views/razor)。

## <a name="use-components"></a>使用元件

除了普通 HTML 之外，元件還可以使用其他元件作為其呈現邏輯的一部分。 在 Razor 中使用元件的語法類似于在 ASP.NET Web 表單應用中使用使用者控制項。 使用與元件的類型名稱匹配的元素標記指定元件。 例如，您可以添加如下所示的`Counter`元件：

```razor
<Counter />
```

與ASP.NET Web 表單不同，Blazor 中的元件：

- 不要使用元素首碼（例如， `asp:`。
- 不需要在頁面或*Web*上註冊。

像想像一下 Razor 元件，就像您那樣，可以.NET 類型，因為這正是它們。 如果引用了包含元件的程式集，則該元件可供使用。 要將元件的命名空間引入範圍，請應用該`@using`指令：

```razor
@using MyComponentLib

<Counter />
```

如預設 Blazor 專案中所示，通常將指令放入`@using` *_Imports.razor*檔中，以便它們導入到同一目錄中的所有 *.razor*檔中以及子目錄中。

如果元件的命名空間不在作用域中，則可以使用元件的完整類型名稱指定元件，如在 C# 中：

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>元件參數

在ASP.NET Web 表單中，可以使用公共屬性將參數和資料流程向控制項。 這些屬性可以使用屬性在標記中設置，也可以直接在代碼中設置。 Blazor 元件的工作方式類似，儘管元件屬性還必須使用要被視為元件參數`[Parameter]`的屬性進行標記。

以下`Counter`元件定義一個元件參數，該`IncrementAmount`參數可用於指定每次按一下按鈕時`Counter`應遞增的金額。

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

要在 Blazor 中指定元件參數，請使用ASP.NET Web 表單中的屬性：

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>事件處理常式

ASP.NET Web 表單和 Blazor 都提供了一個基於事件的程式設計模型來處理 UI 事件。 此類事件的示例包括按鈕按一下和文本輸入。 在ASP.NET Web 表單中，您可以使用 HTML 伺服器控制項來處理 DOM 公開的 UI 事件，也可以處理 Web 服務器控制項公開的事件。 事件通過回後表單請求在伺服器上顯示。 請考慮以下 Web 表單按鈕按一下示例：

*計數器.ascx*

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

在 Blazor 中，可以直接使用表單`@on{event}`的指令屬性註冊 DOM UI 事件的處理常式。 占`{event}`位符表示事件的名稱。 例如，您可以偵聽按鈕按一下，如下所示：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

事件處理常式可以接受可選的特定于事件的參數來提供有關該事件的詳細資訊。 例如，滑鼠事件可以採用`MouseEventArgs`參數，但不是必需的。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

可以使用 lambda 運算式，而不是引用事件處理常式的方法組。 lambda 運算式允許您關閉其他範圍內值。

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

事件處理常式可以同步或非同步執行。 例如，以下`OnClick`事件處理常式非同步執行：

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

處理事件後，元件將呈現為考慮任何元件狀態更改。 使用非同步事件處理常式，在處理常式執行完成後立即呈現元件。 非同步`Task`完成後 *，將再次*呈現元件。 此非同步執行模式提供了在非同步`Task`仍在進行時呈現一些適當 UI 的機會。

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

元件還可以通過定義類型的`EventCallback<TValue>`元件參數來定義自己的事件。 事件回檔支援 DOM UI 事件處理常式的所有變體：可選參數、同步或非同步、方法組或 lambda 運算式。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>資料繫結

Blazor 提供了一種將資料從 UI 元件綁定到元件狀態的簡單機制。 此方法不同于 ASP.NET Web 表單中用於將資料從資料來源綁定到 UI 控制項的功能。 我們將在["處理資料"](data.md)部分仲介紹處理來自不同資料來源的資料。

要創建從 UI 元件到元件狀態的雙向資料繫結，請使用`@bind`指令屬性。 在下面的示例中，核取方塊的值綁定到該`isChecked`欄位。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

呈現元件時，核取方塊的值將設置為`isChecked`欄位的值。 當使用者切換核取方塊時，將`onchange`觸發事件並將`isChecked`該欄位設置為新值。 在這種情況下`@bind`，語法等效于以下標記：

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

要更改用於綁定的事件，請使用 屬性`@bind:event`。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

元件還可以支援綁定到其參數的資料。 要綁定資料，請定義與可綁定參數同名的事件回檔參數。 "已更改"尾碼將添加到名稱中。

*密碼盒.剃鬚刀*

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

要將資料繫結連結到基礎 UI 元素，請使用 該值設置值並直接在 UI 元素上處理事件`@bind`，而不是使用 屬性。

要綁定到元件參數，請使用屬性`@bind-{Parameter}`指定要綁定到的參數。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>狀態變更

如果元件的狀態在正常 UI 事件或事件回檔之外已更改，則元件必須手動發出信號，表示需要再次呈現該元件。 要發出元件狀態已更改的信號，請調用元件上`StateHasChanged`的方法。

在下面的示例中，元件顯示`AppState`來自服務的消息，該消息可以由應用的其他部分更新。 元件將其`StateHasChanged`方法註冊到事件中`AppState.OnChange`，以便每當消息更新時都會呈現該元件。

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

ASP.NET Web 表單框架為模組、頁面和控制定義了明確的生命週期方法。 例如，以下控制項為`Init`和`Load`和`UnLoad`生命週期事件實現事件處理常式：

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor 元件也有定義明確的生命週期。 元件的生命週期可用於初始化元件狀態並實現高級元件行為。

Blazor 的所有元件生命週期方法都具有同步和非同步版本。 元件呈現是同步的。 不能作為元件呈現的一部分運行非同步邏輯。 所有非同步邏輯都必須作為生命週期方法的一`async`部分執行。

### <a name="oninitialized"></a>初始化時

和`OnInitialized``OnInitializedAsync`方法用於初始化元件。 元件通常在首次呈現後初始化。 初始化元件後，在最終釋放元件之前，可能會多次呈現該元件。 該方法`OnInitialized`類似于ASP.NET Web`Page_Load`表單頁和控制項中的事件。

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>在參數設置上

當`OnParametersSet`元件`OnParametersSetAsync`從其父元件接收參數並將值分配給屬性時，將調用 和 方法。 這些方法在元件初始化後以及*每次呈現元件時*執行。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>在渲染後打開

和`OnAfterRender``OnAfterRenderAsync`方法在元件完成呈現後調用。 此時將填充元素和元件引用（下面將介紹這些概念的更多內容）。 此時啟用了與瀏覽器的交互性。 與 DOM 和 JavaScript 執行的交互可以安全地發生。

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

`OnAfterRender`並在`OnAfterRenderAsync`*伺服器上預渲染時不調用*。

參數`firstRender`是`true`首次呈現元件;否則，其值為`false`。

### <a name="idisposable"></a>IDisposable

Blazor 元件可以`IDisposable`實現在從 UI 中刪除元件時釋放資源。 Razor 元件可以使用`IDispose``@implements`該指令實現：

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

## <a name="capture-component-references"></a>捕獲元件引用

在ASP.NET Web 表單中，通常通過引用控制項實例的 ID 來直接在代碼中操作控制項實例。 在 Blazor 中，還可以捕獲和操作對元件的引用，儘管它不太常見。

要在 Blazor 中捕獲元件引用，`@ref`請使用指令屬性。 屬性的值應與與引用的元件類型相同的可設置欄位的名稱匹配。

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

呈現父元件時，該欄位將填充子元件實例。 然後，您可以調用元件實例上的方法或以其他方式操作元件實例。

不建議直接使用元件引用操作元件狀態。 這樣做可防止元件在正確的時間自動呈現。

## <a name="capture-element-references"></a>捕獲元素引用

Blazor 元件可以捕獲對元素的引用。 與ASP.NET Web 表單中的 HTML 伺服器控制項不同，不能直接使用 Blazor 中的元素引用操作 DOM。 Blazor 使用 DOM 擴散演算法為您處理大多數 DOM 交互。 Blazor 中捕獲的元素引用不透明。 但是，它們用於傳遞 JavaScript 交互操作調用中的特定元素引用。 有關 JavaScript 互通的詳細資訊，請參閱[ASP.NET核心 Blazor JavaScript 互通](/aspnet/core/blazor/javascript-interop)。

## <a name="templated-components"></a>樣板化元件

在ASP.NET Web 表單中，您可以創建*範本化控制項*。 範本化控制項使開發人員能夠指定用於呈現容器控制項的 HTML 的一部分。 構建範本化伺服器控制項的機制非常複雜，但它們支援以使用者自訂的方式呈現資料的強大方案。 範本化控制項的示例包括`Repeater`和`DataList`。

Blazor 元件也可以通過定義類型`RenderFragment`或`RenderFragment<T>`的元件參數進行範本化。 表示`RenderFragment`Razor 標記塊，然後由元件呈現。 A`RenderFragment<T>`是 Razor 標記的塊，它採用在渲染渲染片段時可以指定的參數。

### <a name="child-content"></a>子內容

Blazor 元件可以捕獲其子內容作為`RenderFragment`，並將該內容呈現為元件呈現的一部分。 要捕獲子內容，請定義類型的`RenderFragment`元件參數並將其`ChildContent`命名為 。

*子內容元件.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

然後，父元件可以使用正常的 Razor 語法提供子內容。

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>範本參數

範本化的 Blazor 元件還可以定義類型`RenderFragment`或`RenderFragment<T>`的多個元件參數。 調用 時可以`RenderFragment<T>`指定 的 參數。 要為元件指定泛型型別參數，請使用`@typeparam`Razor 指令。

*簡單列表查看.剃鬚刀*

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

使用範本化元件時，可以使用與參數名稱匹配的子項目指定範本參數。 `RenderFragment<T>`作為元素傳遞的類型元件參數具有名為 的`context`隱式參數。 您可以使用子項目上`Context`的屬性更改此實現參數的名稱。 可以使用與類型參數名稱匹配的屬性指定任何泛型型別參數。 如果可能，將推斷類型參數：

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

此元件的輸出如下所示：

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>程式碼後置

Blazor 元件通常創作在單個 *.razor*檔中。 但是，也可以使用代碼背後的檔分隔代碼和標記。 要使用元件檔，添加與元件檔的檔案名匹配但添加了 *.cs*副檔名 *（Counter.razor.cs*） 的 C# 檔。 使用 C# 檔為元件定義基類。 您可以命名基類的任何內容，但通常將類命名為與元件類相同，但添加了`Base`擴展項 （）。`CounterBase` 基於元件的類也必須派生自`ComponentBase`。 然後，在 Razor 元件檔中，添加`@inherits`指令以指定元件的基類 （。`@inherits CounterBase`

*計數器.剃鬚刀*

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

基類中元件成員的可見度必須`protected`為或`public`對元件類可見。

## <a name="additional-resources"></a>其他資源

前面不是對Blazor元件所有方面的詳盡處理。 有關如何[創建和使用核心剃鬚刀元件ASP.NET](/aspnet/core/blazor/components)的詳細資訊，請參閱 Blazor 文檔。

>[!div class="step-by-step"]
>[上一個](app-startup.md)
>[下一個](pages-routing-layouts.md)
