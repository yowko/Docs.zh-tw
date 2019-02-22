---
title: 保護 .NET 微服務和 Web 應用程式
description: .NET 微服務和 Web 應用程式中的安全性 - 了解 ASP.NET Core Web 應用程式中的驗證選項。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a>製作安全的 .NET 微服務和 Web 應用程式

微服務和 Web 應用程式有許多層面，使得主題可能參考到如圖本書的多本書籍，因此我們在本節會將重點放在驗證、授權和應用程式祕密。

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>在 .NET 微服務和 Web 應用程式中實作驗證

您通常必須將服務發佈的資源和 API 限制給某些信任的使用者或用戶端。 制定這類 API 層級信任決策的第一個步驟是驗證。 驗證是可靠地驗證使用者身分識別的程序。

在微服務案例中，通常會集中處理驗證。 如果您使用 API 閘道，則閘道會是適合驗證的位置，如圖 9-1 所示。 如果您使用此方法，請確定若沒有 API 閘道，就無法直接到達個別微服務，除非有其他安全性機制可驗證訊息，而不論其是否來自閘道。

![當 API 閘道將驗證集中時，會在將要求轉送給微服務時新增使用者資訊。](./media/image1.png)

**圖 9-1**. 使用 API 閘道的集中式驗證

如果服務可供直接存取，則可以使用 Azure Active Directory 等驗證服務或作為 Security Token Service (STS) 的專用驗證微服務來驗證使用者。 信任決策會透過安全性權杖或 Cookie 在服務之間共用 (如果有需要，可以透過實作 [Cookie 共用](/aspnet/core/security/cookie-sharing)以在 ASP.NET Core 應用程式之間共用這些權杖。)圖 9-2 說明的就是這種模式。

![有人直接存取微服務時，包含驗證和授權的信任將由專用微服務發行的安全性權杖處理，於微服務間共用。](./media/image2.png)

**圖 9-2**： 由識別微服務驗證並透過授權權杖共用信任

### <a name="authenticate-with-aspnet-core-identity"></a>使用 ASP.NET Core Identity 進行驗證

ASP.NET Core 中用來識別應用程式使用者的主要機制是 [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) 成員資格系統。 ASP.NET Core Identity 會將使用者資訊 (包括登入資訊、角色和宣告) 儲存在開發人員所設定的資料存放區中。 一般而言，ASP.NET Core Identity 資料存放區是 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 套件中所提供的 Entity Framework 存放區。 不過，您可以使用自訂存放區或其他協力廠商套件，將身分識別資訊儲存在 Azure 表格儲存體、CosmosDB 或其他位置。

下列程式碼擷取自 ASP.NET Core Web 應用程式專案範本，並已選取個別使用者帳戶驗證。 其示範如何使用 Startup.ConfigureServices 方法中的 EntityFramework.Core 來設定 ASP.NET Core Identity。

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

設定 ASP.NET Core Identity 之後，您可以在服務的 `Startup.Configure` 方法中呼叫 app.UseIdentity 加以啟用。

您可以在下列幾個情況下使用 ASP.NET Code Identity：

- 使用 UserManager 類型 (userManager.CreateAsync) 建立新的使用者資訊。

- 使用 SignInManager 類型驗證使用者。 您可以使用 `signInManager.SignInAsync` 直接登入，或是用 `signInManager.PasswordSignInAsync` 確認使用者的密碼是否正確，然後將使用者登入。

- 根據儲存在 Cookie 中的資訊 (由 ASP.NET Core Identity 中介軟體讀取) 識別使用者；如此一來，來自瀏覽器的後續要求就會包含已登入使用者的身分識別和宣告。

ASP.NET Core Identity 也支援[雙因素驗證](/aspnet/core/security/authentication/2fa)。

針對使用本機使用者資料存放區，以及使用 Cookie 在要求之間保存身分識別 (通常適用於 MVC Web 應用程式) 的驗證案例，ASP.NET Core Identity 是建議的解決方案。

### <a name="authenticate-with-external-providers"></a>使用外部提供者進行驗證

ASP.NET Core 也支援使用[外部驗證提供者](/aspnet/core/security/authentication/social/)，讓使用者透過 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流程登入。 這表示使用者可以使用來自 Microsoft、Google、Facebook 或 Twitter 等提供者的現有驗證程序進行登入，並將這些身分識別與您應用程式中的 ASP.NET Core Identity 建立關聯。

若要使用外部驗證，您可以在應用程式的 HTTP 要求處理管線中包含適當的驗證中介軟體。 此中介軟體會負責處理從驗證提供者傳回 URI 路由的要求、擷取身分識別資訊，並透過 SignInManager.GetExternalLoginInfo 方法來提供此資訊。

下表顯示熱門的外部驗證提供者及其關聯的 NuGet 套件：

| **提供者**  | **套件**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

不論是何種情況，都會透過呼叫類似 `Startup.Configure`中 `app.Use{ExternalProvider}Authentication` 的註冊方法來註冊中介軟體。 視提供者需要，這些註冊方法會接受選項物件，其中包含應用程式識別碼和秘密資訊 (例如密碼)。 外部驗證提供者需要註冊應用程式 (如 [ASP.NET Core 文件](/aspnet/core/security/authentication/social/)中所述)，才能通知使用者哪個應用程式要求存取其身分識別。

在 `Startup.Configure` 中註冊中介軟體之後，您可以提示使用者透過任何控制器動作登入。 若要這樣做，您可以建立 `AuthenticationProperties` 物件，其中包含驗證提供者的名稱和重新導向 URL。 然後，您需要傳回傳遞 `AuthenticationProperties` 物件的挑戰回應。 下列程式碼將示範這項作業。

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

redirectUrl 參數包含驗證使用者之後，外部提供者應該重新導向的目標 URL。 此 URL 應該代表根據外部身分識別資訊將使用者登入的動作，如下列簡化範例所示：

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

如果當您在 Visual Studio 中建立 ASP.NET Code Web 應用程式專案時，選擇 [Individual User Account] \(個別使用者帳戶\) 驗證選項，專案中已有使用外部提供者登入所需的所有程式碼，如圖 9-3 所示。

![新 ASP.NET Core Web 應用程式的對話方塊，反白顯示了變更驗證的按鈕。](./media/image3.png)

**圖 9-3**。 建立 Web 應用程式專案時選取使用外部驗證的選項

除了先前所列的外部驗證提供者，還有協力廠商套件提供中介軟體以使用其他更多外部驗證提供者。 如需清單，請參閱 GitHub 上的 [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) 存放庫。

您也可以建立自己的外部驗證中介軟體來解決某些特殊需求。

### <a name="authenticate-with-bearer-tokens"></a>使用持有人權杖進行驗證

使用 ASP.NET Core Identity (或 Identity 加上外部驗證提供者) 進行驗證適用於許多 Web 應用程式案例，在這類案例中，適合將使用者資訊儲存在 Cookie 中。 不過在其他案例中，Cookie 不是保存及傳輸資料的自然方式。

例如，在公開 RESTful 端點的 ASP.NET Core Web API 中，由於這些端點可能是由單一頁面應用程式 (SPA)、原生用戶端或甚至是其他 Web API 存取，因此您通常會想要改用持有人權杖驗證。 這些類型的應用程式不適用於 Cookie，但可輕鬆地擷取持有人權杖，並將它包含在後續要求的授權標頭中。 若要啟用權杖驗證，ASP.NET Core 支援使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](https://openid.net/connect/) 的數個選項。

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>使用 OpenID Connect 或 OAuth 2.0 識別提供者進行驗證

如果使用者資訊儲存在 Azure Active Directory 或是支援 OpenID Connect 或 OAuth 2.0 的其他身分識別解決方案中，您可以使用 **Microsoft.AspNetCore.Authentication.OpenIdConnect** 套件透過 OpenID Connect 工作流程進行驗證。 例如，若要對 eShopOnContainers 中的 Identity.Api 微服務進行驗證，ASP.NET Core Web 應用程式可以使用該套件中的中介軟體，如以下 `Startup.cs` 中的簡例所示：

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
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

1. 您在 Startup.Configure 方法中呼叫 app.UseIdentityServer，以將 IdentityServer4 新增至應用程式的 HTTP 要求處理管線。 這可讓程式庫服務 OpenID Connect 和 OAuth2 端點的要求，例如 /connect/token。

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
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>取用安全性權杖

對 OpenID Connect 端點進行驗證或發行您自己的安全性權杖涵蓋一些案例。 但如果服務只需要將存取權限制給具有其他服務所提供之有效安全性權杖的使用者，又如何？

針對該案例，**Microsoft.AspNetCore.Authentication.JwtBearer** 套件會提供用於處理 JWT 權杖的驗證中介軟體。 JWT 代表 "[JSON Web Token](https://tools.ietf.org/html/rfc7519)"，這是用於傳達安全性宣告的常見安全性權杖格式 (由 RFC 7519 定義)。 使用中介軟體來取用該等權杖的簡例看起來就像此程式碼片段，取自 eShopOnContainers 的 Ordering.Api 微服務。

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

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

- **在應用程式之間共用 Cookie** \
  [*https://docs.microsoft.com/aspnet/core/security/cookie-sharing*](/aspnet/core/security/cookie-sharing)

- **身分識別簡介** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](/aspnet/core/security/authentication/identity)

- **Rick Anderson，使用 SMS 的雙因素驗證** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](/aspnet/core/security/authentication/2fa)

- **使用 Facebook、Google 和其他外部提供者啟用驗證** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](/aspnet/core/security/authentication/social/)

- **Michell Anicas，OAuth 2 簡介** \
  [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- **AspNet.Security.OAuth.Providers** (ASP.NET OAuth 提供者的 GitHub 存放庫) \
  [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- **Danny Strockis，將 Azure AD 整合到 ASP.NET Core Web 應用程式** \
  [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- **IdentityServer4，正式文件** \
  *<https://identityserver4.readthedocs.io/en/latest/>*

>[!div class="step-by-step"]
>[上一頁](../implement-resilient-applications/monitor-app-health.md)
>[下一頁](authorization-net-microservices-web-applications.md)
