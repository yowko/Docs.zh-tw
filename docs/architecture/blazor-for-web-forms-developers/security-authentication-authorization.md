---
title: 安全性： ASP.NET Web Forms 和中的驗證和授權 Blazor
description: 瞭解如何在 ASP.NET Web Forms 和中處理驗證和授權 Blazor 。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267822"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a>安全性： ASP.NET Web Forms 和中的驗證和授權 Blazor

Blazor假設應用程式已設定驗證，則從 ASP.NET Web Forms 應用程式遷移到幾乎都需要更新驗證和授權的執行方式。 本章將說明如何) 成員資格、角色和使用者設定檔的 ASP.NET Web Forms 通用提供者模型 (遷移，以及如何從應用程式使用 ASP.NET Core 身分識別 Blazor 。 雖然本章將涵蓋高階步驟和考慮，但您可以在參考的檔中找到詳細的步驟和腳本。

## <a name="aspnet-universal-providers"></a>ASP.NET 通用提供者

自 ASP.NET 2.0 起，ASP.NET Web Forms 平臺支援各種功能的提供者模型，包括成員資格。 通用成員資格提供者以及選用的角色提供者，通常會與 ASP.NET Web Forms 的應用程式一起部署。 它提供一種健全且安全的方式來管理驗證和授權，以持續正常運作。 這些通用提供者的最新供應專案是以 NuGet[套件的形式提供。](https://www.nuget.org/packages/Microsoft.AspNet.Providers)

Universal Providers 使用包含 `aspnet_Applications` 、、和等資料表的 SQL database 架構 `aspnet_Membership` `aspnet_Roles` `aspnet_Users` 。 藉由執行 [aspnet_regsql.exe 命令](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140))來設定時，提供者會安裝資料表和預存程式，以提供使用基礎資料所需的所有必要查詢和命令。 資料庫架構與這些預存程式與較新的 ASP.NET Identity 和 ASP.NET Core 的身分識別系統不相容，因此必須將現有的資料移轉到新系統中。 [圖 1] 顯示針對通用提供者設定的範例資料表架構。

![通用提供者架構](./media/security/membership-tables.png)

通用提供者會處理使用者、成員資格、角色和設定檔。 系統會將全域唯一識別碼和非常基本的資訊指派給使用者， (userId、userName) 儲存在 `aspnet_Users` 資料表中。 系統會將驗證資訊（例如密碼、密碼格式、密碼 salt、鎖定計數器和詳細資料等）儲存在 `aspnet_Membership` 資料表中。 角色只包含名稱和唯一識別碼，可透過關聯資料表指派給使用者 `aspnet_UsersInRoles` ，並提供多對多關聯性。

如果您現有的系統除了成員資格之外還在使用角色，您必須將使用者帳戶、相關聯的密碼、角色和角色成員資格遷移至 ASP.NET Core 身分識別。 您也可能需要使用 if 語句來更新您目前正在執行角色檢查的程式碼，以改用宣告式篩選、屬性和/或標記協助程式。 我們將在這一章的結尾更詳細地探討遷移考慮。

### <a name="authorization-configuration-in-web-forms"></a>Web Form 中的授權設定

若要在 ASP.NET Web Forms 應用程式中設定特定頁面的授權存取，您通常會指定匿名使用者無法存取特定頁面或資料夾。 這是在 web.config 檔案中完成：

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

`authentication`設定區段會設定應用程式的表單驗證。 `authorization`區段是用來禁止整個應用程式的匿名使用者。 不過，您可以針對每個位置提供更細微的授權規則，以及套用以角色為基礎的授權檢查。

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

上述設定與第一個設定合併時，會允許匿名使用者存取登入頁面，以覆寫非驗證使用者的全網站限制。

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

上述設定與其他設定合併時， `/admin` 會將資料夾和其內所有資源的存取限制為「系統管理員」角色的成員。 也可以藉由將個別檔案放 `web.config` 在資料夾根目錄中來套用 `/admin` 。

### <a name="authorization-code-in-web-forms"></a>Web Form 中的授權碼

除了使用設定存取之外 `web.config` ，您也可以在 Web Form 應用程式中，以程式設計方式設定存取和行為。 例如，您可以限制執行特定作業或根據使用者角色來查看特定資料的能力。

這段程式碼可用於程式碼後置邏輯和頁面本身：

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

除了檢查使用者角色成員資格，您也可以判斷這些成員資格是否經過驗證 (但使用上述) 所涵蓋的位置型設定，通常是較好的做法。 以下是此方法的範例。

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

在上述程式碼中， (RBAC) 的角色型存取控制會用來判斷是否 `SecretPanel` 會根據目前使用者的角色來顯示頁面的某些專案，例如。

一般來說，ASP.NET Web Forms 的應用程式會在檔案中設定安全性 `web.config` ，然後再于 `.aspx` 頁面及其相關的程式碼後置檔案中新增其他檢查 `.aspx.cs` 。 大部分的應用程式會利用通用的成員資格提供者，通常會有額外的角色提供者。

## <a name="aspnet-core-identity"></a>ASP.NET Core 身分識別

雖然仍然負責驗證和授權，但在與通用提供者相較之下，ASP.NET Core 身分識別會使用一組不同的抽象概念和假設。 例如，新的身分識別模型支援協力廠商驗證，可讓使用者使用社交媒體帳戶或其他受信任的驗證提供者進行驗證。 ASP.NET Core 身分識別支援使用者介面，可用於通常需要的頁面，例如登入、登出及註冊。 它會利用 EF Core 來存取資料，並使用 EF Core 的遷移來產生支援其資料模型所需的架構。 本 [ASP.NET Core 的身分識別簡介](https://docs.microsoft.com/aspnet/core/security/authentication/identity) 提供了 ASP.NET Core 身分識別所包含的內容，以及如何開始使用它的良好總覽。 如果您尚未在您的應用程式及其資料庫中設定 ASP.NET Core 身分識別，它會協助您開始使用。

### <a name="roles-claims-and-policies"></a>角色、宣告和原則

通用提供者和 ASP.NET Core 身分識別都支援角色的概念。 您可以為使用者建立角色，並將使用者指派給角色。 使用者可以屬於任意數量的角色，而且您可以驗證角色成員資格作為授權實施的一部分。

除了角色之外，ASP.NET Core 身分識別也支援宣告和原則的概念。 角色應特別對應到一組資源，而該角色的使用者應該能夠存取，而宣告只是使用者身分識別的一部分。 宣告是一組名稱值組，代表主體是什麼，而不是主體可做的動作。

您可以直接檢查使用者的宣告，並根據這些使用者是否應該獲得資源的存取權來決定。 不過，這類檢查通常會在整個系統中重複和散佈。 更好的方法是定義 *原則*。

授權原則包含一個或多個需求。 原則會在的方法中註冊為授權服務設定的一部分 `ConfigureServices` `Startup.cs` 。 例如，下列程式碼片段會設定名為 "CanadiansOnly" 的原則，其要求使用者的國家/地區宣告值為 "加拿大"。

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

您可以 [在檔中深入瞭解如何建立自訂原則](https://docs.microsoft.com/aspnet/core/security/authorization/policies)。

無論您使用的是原則或角色，都可以指定應用程式中的特定頁面， Blazor 要求該角色或具有 `[Authorize]` 屬性（attribute）的原則套用於指示詞 `@attribute` 。

需要角色：

```csharp
@attribute [Authorize(Roles ="administrators")]
```

需要滿足原則：

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

如果您需要存取使用者的驗證狀態、角色或程式碼中的宣告，有兩種主要方式可以達成此目的。 第一個是以串聯參數形式接收驗證狀態。 第二個是使用插入的來存取狀態 `AuthenticationStateProvider` 。 這些方法的詳細資料將在[ Blazor 安全性檔案](https://docs.microsoft.com/aspnet/core/blazor/security/)中說明。

下列程式碼示範如何以串聯 `AuthenticationState` 參數的形式接收：

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

使用這個參數時，您可以使用下列程式碼來取得使用者：

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

下列程式碼顯示如何插入 `AuthenticationStateProvider` ：

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

有了提供者之後，您就可以使用下列程式碼來取得使用者的存取權：

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**注意：**`AuthorizeView`本章節稍後所涵蓋的元件提供了一種宣告方式，可控制使用者在頁面或元件上看到的內容。

若要在伺服器應用程式中使用使用者和宣告 (Blazor) 您可能也需要插入 `UserManager<T>` 預設) 的 (用法， `IdentityUser` 您可以用來列舉和修改使用者的宣告。 先插入類型，並將它指派給屬性：

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

然後使用它來處理使用者的宣告。 下列範例顯示如何在使用者上新增和保存宣告：

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

如果您需要使用角色，請遵循相同的方法。 您可能需要插入 (用於 `RoleManager<T>` `IdentityRole` 預設類型) ，以列出和管理角色本身。

**注意：** 在 Blazor WebAssembly 專案中，您將需要提供伺服器 api 來執行這些作業 (而不是使用 `UserManager<T>` 或 `RoleManager<T>` 直接) 。 BlazorWebAssembly 用戶端應用程式會藉由安全地呼叫針對此目的公開的 API 端點來管理宣告和/或角色。

### <a name="migration-guide"></a>移轉指南

從 ASP.NET Web Forms 和通用提供者遷移到 ASP.NET Core 身分識別需要幾個步驟：

1. 在目的地資料庫中建立 ASP.NET Core 身分識別資料庫架構
2. 將資料從通用提供者架構遷移至 ASP.NET Core 的身分識別架構
3. 將 configuration 從 web.config 遷移至中介軟體和服務，通常位於 `Startup.cs`
4. 使用控制項和條件更新個別頁面，以使用標記協助程式和新的身分識別 Api。

下列各節將詳細討論這其中每個步驟。

### <a name="creating-the-aspnet-core-identity-schema"></a>建立 ASP.NET Core 身分識別架構

有幾種方式可以建立用於 ASP.NET Core 身分識別的必要資料表結構。 最簡單的方式是建立新的 ASP.NET Core Web 應用程式。 選擇 [Web 應用程式]，然後將驗證變更為使用個別的使用者帳戶。

![具有個別使用者帳戶的新專案](./media/security/individual-user-accounts.png)

您可以從命令列執行相同的動作 `dotnet new webapp -au Individual` 。 建立應用程式之後，請在該網站上執行並註冊。 您應該會觸發如下所示的頁面：

![套用遷移頁面](./media/security/apply-migrations-page.png)

按一下 [套用遷移] 按鈕，就應該為您建立必要的資料庫資料表。 此外，遷移檔應該會出現在您的專案中，如下所示：

![遷移檔](./media/security/migration-files.png)

您可以使用下列命令列工具，自行執行遷移，而不需要執行 web 應用程式：

```powershell
dotnet ef database update
```

如果您想要執行腳本，以將新的架構套用至現有的資料庫，您可以從命令列編寫這些遷移的腳本。 執行此命令以產生腳本：

```powershell
dotnet ef migrations script -o auth.sql
```

這將會在輸出檔案中產生 SQL 腳本， `auth.sql` 然後針對您想要的任何資料庫來執行。 如果您在執行命令時遇到任何問題 `dotnet ef` ， [請確定您已在系統上安裝 EF Core 工具](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet)。

如果您的來源資料表有額外的資料行，您必須在新的架構中找出這些資料行的最佳位置。 一般而言，資料表上的資料行 `aspnet_Membership` 應該對應至 `AspNetUsers` 資料表。 上的資料行 `aspnet_Roles` 應該對應至 `AspNetRoles` 。 資料表上的任何其他資料行 `aspnet_UsersInRoles` 都會加入至 `AspNetUserRoles` 資料表。

也值得考慮將任何額外的資料行放在不同的資料表上，以便未來的遷移不需要考慮預設身分識別架構的自訂。

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>將資料從通用提供者遷移至 ASP.NET Core 身分識別

當您備妥目的地資料表架構後，下一個步驟是將您的使用者和角色記錄遷移至新的架構。 您可以在 [這裡](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)找到架構差異的完整清單，包括哪些資料行對應到哪些新資料行。

若要將使用者的成員資格遷移至新的身分識別資料表，您應 [遵循檔中所述的步驟](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)。 遵循這些步驟和提供的腳本之後，您的使用者將需要在下次登入時變更其密碼。

您可以遷移使用者密碼，但程式更牽涉到更多。 要求使用者在遷移過程中更新其密碼，並鼓勵他們使用新的唯一密碼，可能會增強應用程式的整體安全性。

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>將安全性設定從 web.config 遷移至 Startup.cs

如先前所述，ASP.NET 成員資格和角色提供者會在應用程式的 web.config 檔中設定。 由於 ASP.NET Core 的應用程式不會系結至 IIS，並且使用個別的系統進行設定，因此必須在其他地方設定這些設定。 在大部分的情況下，會在檔案中設定 ASP.NET Core 身分識別 `Startup.cs` 。 開啟稍早建立的 Web 專案 (，以產生識別資料表架構) 並檢查其檔案 `Startup.cs` 。

預設的 ConfigureServices 方法會新增 EF Core 和身分識別的支援：

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

`AddDefaultIdentity`擴充方法是用來設定身分識別，以使用預設值 `ApplicationDbContext` 和架構的 `IdentityUser` 類型。 如果您是使用自訂 `IdentityUser` ，請務必在此指定它的類型。 如果這些擴充方法無法在您的應用程式中運作，請檢查您是否有適當的 using 語句，以及您是否有必要的 NuGet 套件參考。 例如，您的專案應該已參考某些版本的 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 和 `Microsoft.AspNetCore.Identity.UI` 套件。

此外 `Startup.cs` ，您應該會看到為網站設定的必要中介軟體。 具體來說 `UseAuthentication` ， `UseAuthorization` 應該在適當的位置進行設定。

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity 不會將匿名或以角色為基礎的存取設定至的位置 `Startup.cs` 。 您必須將任何位置特定的授權設定資料移轉至 ASP.NET Core 中的篩選準則。 請記下哪些資料夾和頁面需要這類更新。 您將在下一節中進行這些變更。

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>更新個別頁面以使用 ASP.NET Core 身分識別抽象

在您的 ASP.NET Web Forms 應用程式中，如果您有 web.config 設定來拒絕匿名使用者的特定頁面或資料夾的存取權，您只要將此 `[Authorize]` 屬性新增至這類頁面，即可進行遷移：

```razor
@attribute [Authorize]
```

如果您對屬於某個角色的使用者進一步拒絕存取，您也可以藉由新增指定角色的屬性來進行遷移：

```razor
@attribute [Authorize(Roles ="administrators")]
```

請注意，此 `[Authorize]` 屬性只適用于透過 `@page` 路由器達成的元件 Blazor 。 屬性無法與子元件搭配使用，而應該改用 `AuthorizeView` 。

如果您在頁面標記內有邏輯來判斷是否要對特定使用者顯示某些程式碼，您可以將此取代為 `AuthorizeView` 元件。 [AuthorizeView 元件](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component)會選擇性地顯示 UI，取決於使用者是否已獲授權查看。 它也會公開 `context` 可以用來存取使用者資訊的變數。

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

您可以使用屬性設定的，存取程式邏輯內的驗證狀態 `Task<AuthenticationState` `[CascadingParameter]` 。 這可讓您存取使用者，這可讓您判斷它們是否經過驗證，以及是否屬於特定的角色。 如果您需要評估原則 cti，您可以插入的實例， `IAuthorizationService` 並 `AuthorizeAsync` 在其上呼叫方法。 下列範例程式碼示範如何取得使用者資訊，並允許授權的使用者執行原則所限制的工作 `content-editor` 。

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

`AuthenticationState`首先需要將設定為串聯值，才能系結至像這樣的串聯參數。 這通常是使用元件來完成 `CascadingAuthenticationState` 。 這通常是在中完成 `App.razor` ：

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>摘要

Blazor 使用與 ASP.NET Core 相同的安全性模型，這是 ASP.NET Core 身分識別。 從通用提供者遷移到 ASP.NET Core 身分識別相當簡單，但前提是不太太多自訂套用至原始資料架構。 一旦資料移轉之後，在應用程式中使用驗證和授權的 Blazor 記錄就會有完整的記錄，並可進行設定，以及針對大部分的安全性需求進行程式設計支援。

## <a name="references"></a>參考

- [ASP.NET Core 上的身分識別簡介](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [從 ASP.NET 成員資格驗證遷移至 ASP.NET Core 2.0 身分識別](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [將驗證和身分識別遷移至 ASP.NET Core](https://docs.microsoft.com/aspnet/core/migration/identity)
- [ASP.NET Core Blazor 驗證與授權](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[上一個](config.md) 
>[下一步](migration.md)
