---
title: 保護 .NET 微服務和 Web 應用程式
description: .NET 微服務和 Web 應用程式中的安全性 - 了解 ASP.NET Core Web 應用程式中的驗證選項。
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 2b503b326d1869ae095f9b177c04389bda9fe46c
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100778"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>製作安全的 .NET 微服務和 Web 應用程式

微服務和 Web 應用程式有許多層面，使得主題可能參考到如圖本書的多本書籍，因此我們在本節會將重點放在驗證、授權和應用程式祕密。

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>在 .NET 微服務和 Web 應用程式中實作驗證

您通常必須將服務發佈的資源和 API 限制給某些信任的使用者或用戶端。 制定這類 API 層級信任決策的第一個步驟是驗證。 驗證是可靠地驗證使用者身分識別的程式。

在微服務案例中，驗證通常會集中處理。 如果您使用 API 閘道，則閘道會是適合驗證的位置，如圖 9-1 所示。 如果您使用此方法，請確定若沒有 API 閘道，就無法直接到達個別微服務，除非有其他安全性機制可驗證訊息，而不論其是否來自閘道。

![此圖顯示用戶端行動應用程式如何與後端互動。](./media/index/api-gateway-centralized-authentication.png)

**圖 9-1**. 使用 API 閘道的集中式驗證

當 API 閘道將驗證集中時，會在將要求轉送給微服務時新增使用者資訊。 如果可以直接存取服務，則驗證服務 (例如 Azure Active Directory 或專用驗證微服務) 會作為安全性權杖服務 (STS)，可用來驗證使用者。 信任決策會在服務與安全性權杖或 Cookie 之間共用。 （如有需要，可以在 ASP.NET Core 應用程式之間共用這些權杖，方法是執行[cookie 共用](/aspnet/core/security/cookie-sharing)）。此模式如圖9-2 所示。

![此圖顯示透過後端微服務的驗證。](./media/index/identity-microservice-authentication.png)

**圖 9-2**： 由識別微服務驗證並透過授權權杖共用信任

有人直接存取微服務時，包含驗證和授權的信任將由專用微服務發行的安全性權杖處理，於微服務間共用。

### <a name="authenticate-with-aspnet-core-identity"></a>使用 ASP.NET Core Identity 進行驗證

ASP.NET Core 識別應用程式使用者的主要機制是[ASP.NET Core 身分識別](/aspnet/core/security/authentication/identity)成員資格系統。 ASP.NET Core 身分識別會將使用者資訊 (包括登入資訊、角色及宣告) 儲存在由開發人員設定的資料存放區中。 一般而言，ASP.NET Core Identity 資料存放區是 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 套件中所提供的 Entity Framework 存放區。 不過，您可以使用自訂存放區或其他協力廠商套件，將身分識別資訊儲存在 Azure 表格儲存體、CosmosDB 或其他位置。

> [!TIP]
> ASP.NET Core 2.1 和更新版本提供作為[Razor 類別庫](/aspnet/core/razor-pages/ui-class)的[ASP.NET Core 身分識別](/aspnet/core/security/authentication/identity)，因此，您不會在專案中看到大部分必要的程式碼，就像先前版本的情況一樣。 如需如何自訂身分識別程式碼以符合您的需求的詳細資訊，請參閱[ASP.NET Core 專案中的 Scaffold 身分識別](/aspnet/core/security/authentication/scaffold-identity)。

下列程式碼是從 ASP.NET Core Web 應用程式 MVC 3.1 專案範本取得，並選取個別的使用者帳戶驗證。 它會示範如何在方法中使用 Entity Framework Core 來設定 ASP.NET Core 身分識別 `Startup.ConfigureServices` 。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

設定 ASP.NET Core 身分識別之後，您可以藉由新增和來啟用它， `app.UseAuthentication()` `endpoints.MapRazorPages()` 如服務的方法中的下列程式碼所示 `Startup.Configure` ：

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> 前面程式碼中的行**必須依照顯示的順序**，身分識別才能正常運作。

您可以在下列幾個情況下使用 ASP.NET Code Identity：

- 使用 UserManager 類型 (userManager.CreateAsync) 建立新的使用者資訊。

- 使用 SignInManager 類型驗證使用者。 您可以使用 `signInManager.SignInAsync` 直接登入，或 `signInManager.PasswordSignInAsync` 確認使用者的密碼正確，然後登入。

- 根據儲存在 cookie 中的資訊（由 ASP.NET Core 身分識別中介軟體讀取）來識別使用者，讓來自瀏覽器的後續要求會包含登入使用者的身分識別和宣告。

ASP.NET Core Identity 也支援[雙因素驗證](/aspnet/core/security/authentication/2fa)。

針對使用本機使用者資料存放區，以及使用 Cookie 在要求之間保存身分識別 (通常適用於 MVC Web 應用程式) 的驗證案例，ASP.NET Core Identity 是建議的解決方案。

### <a name="authenticate-with-external-providers"></a>使用外部提供者進行驗證

ASP.NET Core 也支援使用[外部驗證提供者](/aspnet/core/security/authentication/social/)，讓使用者透過 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流程登入。 這表示使用者可以使用來自 Microsoft、Google、Facebook 或 Twitter 等提供者的現有驗證程序進行登入，並將這些身分識別與您應用程式中的 ASP.NET Core Identity 建立關聯。

若要使用外部驗證（除了前面所述的驗證中介軟體以外）， `app.UseAuthentication()` 您也必須在中註冊外部提供者， `Startup` 如下列範例所示：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

下表顯示熱門的外部驗證提供者及其關聯的 NuGet 套件：

| **提供者**  | **套件** \(英文\)                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

在所有情況下，您都必須完成與廠商相依的應用程式註冊程式，而且通常包含：

1. 取得用戶端應用程式識別碼。
2. 取得用戶端應用程式密碼。
3. 設定重新導向 URL，由授權中介軟體和已註冊的提供者處理
4. （選擇性）設定 [登出 URL]，以在單一登入（SSO）案例中正確地處理登出。

如需為外部提供者設定應用程式的詳細資訊，請參閱[ASP.NET Core 檔中的外部提供者驗證](/aspnet/core/security/authentication/social/)。

>[!TIP]
>所有詳細資料都是由先前所述的授權中介軟體和服務所處理。 因此，當您在 Visual Studio 建立 ASP.NET 程式碼 web 應用程式專案時，只需要選擇 [**個別使用者帳戶**] 驗證選項，如圖9-3 所示，除了註冊先前所述的驗證提供者之外。

![[新增 ASP.NET Core Web 應用程式] 對話方塊的螢幕擷取畫面。](./media/index/select-individual-user-account-authentication-option.png)

**圖 9-3**。 在 Visual Studio 2019 中建立 web 應用程式專案時，選取 [個別使用者帳戶] 選項（用於使用外部驗證）。

除了先前所列的外部驗證提供者，還有協力廠商套件提供中介軟體以使用其他更多外部驗證提供者。 如需清單，請參閱 GitHub 上的[AspNet. Security. OAuth. provider](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)存放庫。

您也可以建立自己的外部驗證中介軟體來解決某些特殊需求。

### <a name="authenticate-with-bearer-tokens"></a>使用持有人權杖進行驗證

使用 ASP.NET Core Identity (或 Identity 加上外部驗證提供者) 進行驗證適用於許多 Web 應用程式案例，在這類案例中，適合將使用者資訊儲存在 Cookie 中。 不過在其他案例中，Cookie 不是保存及傳輸資料的自然方式。

例如，在公開 RESTful 端點的 ASP.NET Core Web API 中，由於這些端點可能是由單一頁面應用程式 (SPA)、原生用戶端或甚至是其他 Web API 存取，因此您通常會想要改用持有人權杖驗證。 這些類型的應用程式不適用於 Cookie，但可輕鬆地擷取持有人權杖，並將它包含在後續要求的授權標頭中。 若要啟用權杖驗證，ASP.NET Core 支援使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](https://openid.net/connect/) 的數個選項。

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>使用 OpenID Connect 或 OAuth 2.0 識別提供者進行驗證

如果使用者資訊儲存在 Azure Active Directory 或另一個支援 OpenID Connect 或 OAuth 2.0 的身分識別解決方案中，您可以使用**AspNetCore OpenIdConnect**套件來使用 OpenID connect 工作流程進行驗證。 例如，若要對 eShopOnContainers 中的 Identity.Api 微服務進行驗證，ASP.NET Core Web 應用程式可以使用該套件中的中介軟體，如以下 `Startup.cs` 中的簡例所示：

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

請注意，當您使用此工作流程時，不需要 ASP.NET Core Identity 中介軟體，因為識別服務會處理所有使用者資訊的儲存與驗證。

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>從 ASP.NET Core 服務發行安全性權杖

如果您想要對本機 ASP.NET Core Identity 使用者發行安全性權杖，而不是使用外部識別提供者，您可以利用一些不錯的協力廠商程式庫。

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) 和 [OpenIddict](https://github.com/openiddict/openiddict-core) 是 OpenID Connect 提供者，可輕鬆地與 ASP.NET Core Identity 整合，讓您從 ASP.NET Core 服務發行安全性權杖。 [IdentityServer4 文件](https://identityserver4.readthedocs.io/en/latest/)深入說明如何使用程式庫。 不過，使用 IdentityServer4 發行權杖的基本步驟如下。

1. 您呼叫應用程式。在 Startup.Configu 方法中 UseIdentityServer，以將 IdentityServer4 新增至應用程式的 HTTP 要求處理管線。 這可讓程式庫服務 OpenID Connect 和 OAuth2 端點的要求，例如 /connect/token。

2. 您呼叫 services.AddIdentityServer，以設定 IdentityServer4 in Startup.ConfigureServices。

3. 若要設定識別伺服器，請設定下列資料：

   - 用於簽署的[認證](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)。

   - 使用者可能要求存取的[身分識別和 API 資源](https://identityserver4.readthedocs.io/en/latest/topics/resources.html)：

      - 代表使用者可透過存取權杖存取之受保護資料或功能的 API 資源。 API 資源的一個範例是需要授權的 Web API (或一組 API)。

      - 代表資訊 (宣告) 的資源，這些資訊 (宣告) 已提供給用戶端來識別使用者。 宣告可能包含使用者名稱、電子郵件地址等等。

   - 將連線以要求權杖的[用戶端](https://identityserver4.readthedocs.io/en/latest/topics/clients.html)。

   - 使用者資訊的儲存機制，例如 [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) 或替代方案。

當您指定要讓 IdentityServer4 使用的用戶端和資源時，您可以將適當類型的 <xref:System.Collections.Generic.IEnumerable%601> 集合傳遞至接受記憶體內部用戶端或資源存放區的方法。 在更複雜的情況下，您可能會透過相依性插入提供用戶端或資源提供者類型。

讓 IdentityServer4 使用自訂 IClientStore 類型所提供之記憶體內部資源和用戶端的範例設定可能如下列範例所示：

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a>取用安全性權杖

對 OpenID Connect 端點進行驗證或發行您自己的安全性權杖涵蓋一些案例。 但如果服務只需要將存取權限制給具有其他服務所提供之有效安全性權杖的使用者，又如何？

針對該案例，處理 JWT 權杖的驗證中介軟體可在**AspNetCore. microsoft.aspnetcore.authentication.jwtbearer**套件中取得。 JWT 代表 "[JSON Web Token](https://tools.ietf.org/html/rfc7519)"，這是用於傳達安全性宣告的常見安全性權杖格式 (由 RFC 7519 定義)。 使用中介軟體來取用該等權杖的簡例看起來就像此程式碼片段，取自 eShopOnContainers 的 Ordering.Api 微服務。

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

此用法的參數如下：

- `Audience` 代表權杖授與存取權之傳入權杖或資源的接收者。 如果此參數中指定的值不符合權杖中的參數，則會拒絕此權杖。

- `Authority` 是發行權杖之驗證伺服器的位址。 JWT 持有人驗證中介軟體使用此 URI 來取得公開金鑰，以用來驗證權杖的簽章。 中介軟體也會確認權杖中的 `iss` 參數符合此 URI。

另一個參數 `RequireHttpsMetadata`；您可以將此參數設定為 false，以便在沒有憑證的環境中進行測試。 在真實世界部署中，JWT 持有人權杖一律只能透過 HTTPS 傳遞。

準備好此中介軟體之後，就會從授權標頭自動擷取 JWT 權杖。 這些權杖會接著還原序列化、驗證 (使用 `Audience` 和 `Authority` 參數中的值) 並儲存為使用者資訊，以供 MVC 動作或授權篩選稍後參考。

JWT 持有人驗證中介軟體也可以支援更進階的案例；例如，在沒有授權單位的情況下，使用本機憑證來驗證權杖。 在此案例中，您可以在 `JwtBearerOptions`物件中指定 `TokenValidationParameters` 物件。

## <a name="additional-resources"></a>其他資源

- **在應用程式之間共用 cookie** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **身分識別簡介** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson。使用 SMS 的雙因素驗證** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **使用 Facebook、Google 和其他外部提供者啟用驗證** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas,。OAuth 2 簡介** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (ASP.NET OAuth 提供者的 GitHub 存放庫) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4.官方檔** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[上一個](../implement-resilient-applications/monitor-app-health.md) 
>[下一步](authorization-net-microservices-web-applications.md)
