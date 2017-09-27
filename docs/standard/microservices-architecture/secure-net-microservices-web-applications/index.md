---
title: "保護 .NET 微服務和 Web 應用程式"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 保護 .NET 微服務和 Web 應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 0bc9fe2975dc1c72f6dbe551c4ec74d7d51e69af
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="securing-net-microservices-and-web-applications"></a>保護 .NET 微服務和 Web 應用程式

您通常必須將服務所公開的資源和 API 限制給某些信任的使用者或用戶端。 制定這類 API 層級信任決策的第一個步驟是驗證。 驗證是可靠地確認使用者身分識別的程序。

在微服務案例中，通常會集中處理驗證。 如果您使用 API 閘道，閘道是適合驗證的位置，如圖 11-1 所示。 如果您使用此方法，請確定若沒有 API 閘道，就無法直接到達個別微服務，除非有其他安全性機制可驗證訊息，而不論其是否來自閘道。

![](./media/image1.png)

**圖 11-1**. 使用 API 閘道的集中式驗證

如果服務可供直接存取，則可以使用 Azure Active Directory 等驗證服務或作為 Security Token Service (STS) 的專用驗證微服務來驗證使用者。 信任決策會透過安全性權杖或 Cookie 在服務之間共用 (如有必要，可透過[資料保護服務](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)在 ASP.NET Core 應用程式之間共用)。圖 11-2 說明的就是這種模式。

![](./media/image2.png)

**圖 11-2**. 由識別微服務驗證並透過授權權杖共用信任

## <a name="authenticating-using-aspnet-core-identity"></a>使用 ASP.NET Core Identity 進行驗證

ASP.NET Core 中用來識別應用程式使用者的主要機制是 [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) 成員資格系統。 ASP.NET Core Identity 會將使用者資訊 (包括登入資訊、角色和宣告) 儲存在開發人員所設定的資料存放區中。 一般而言，ASP.NET Core Identity 資料存放區是 Microsoft.AspNetCore.Identity.EntityFrameworkCore 套件中所提供的 Entity Framework 存放區。 不過，您可以使用自訂存放區或其他協力廠商套件，將身分識別資訊儲存在 Azure 資料表儲存體、DocumentDB 或其他位置。

下列程式碼擷取自 ASP.NET Core Web 應用程式專案範本，並已選取個別使用者帳戶驗證。 其示範如何使用 Startup.ConfigureServices 方法中的 EntityFramework.Core 來設定 ASP.NET Core Identity。

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

設定 ASP.NET Core Identity 之後，您可以在服務的 Startup.Configure 方法中呼叫 app.UseIdentity 加以啟用。

您可以在下列幾個情況下使用 ASP.NET Code Identity：

-   使用 UserManager 類型 (userManager.CreateAsync) 建立新的使用者資訊。

-   使用 SignInManager 類型驗證使用者。 您可以使用 signInManager.SignInAsync 直接登入，或使用 signInManager.PasswordSignInAsync 確認使用者的密碼正確後再將他們登入。

-   根據儲存在 Cookie 中的資訊 (由 ASP.NET Core Identity 中介軟體讀取) 識別使用者；如此一來，來自瀏覽器的後續要求就會包含已登入使用者的身分識別和宣告。

ASP.NET Core Identity 也支援[雙因素驗證](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)。

針對使用本機使用者資料存放區，以及使用 Cookie 在要求之間保存身分識別 (通常適用於 MVC Web 應用程式) 的驗證案例，ASP.NET Core Identity 是建議的解決方案。

## <a name="authenticating-using-external-providers"></a>使用外部提供者進行驗證

ASP.NET Core 也支援使用[外部驗證提供者](https://docs.microsoft.com/aspnet/core/security/authentication/social/)，讓使用者透過 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流程登入。 這表示使用者可以使用來自 Microsoft、Google、Facebook 或 Twitter 等提供者的現有驗證程序進行登入，並將這些身分識別與您應用程式中的 ASP.NET Core Identity 建立關聯。

若要使用外部驗證，您可以在應用程式的 HTTP 要求處理管線中包含適當的驗證中介軟體。 此中介軟體會負責處理從驗證提供者傳回 URI 路由的要求、擷取身分識別資訊，並透過 SignInManager.GetExternalLoginInfo 方法來提供此資訊。

以下顯示熱門的外部驗證提供者及其關聯的 NuGet 套件。

**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

在所有情況下，會使用類似於 app.Use{ExternalProvider}Authentication in Startup.Configure 的註冊方法來註冊中介軟體。 視提供者需要，這些註冊方法會接受選項物件，其中包含應用程式識別碼和秘密資訊 (例如密碼)。 外部驗證提供者需要註冊應用程式 (如 [ASP.NET Core 文件](https://docs.microsoft.com/aspnet/core/security/authentication/social/)中所述)，才能通知使用者哪個應用程式要求存取其身分識別。

在 Startup.Configure 中註冊中介軟體之後，您可以提示使用者透過任何控制器動作登入。 若要這樣做，您可以建立 AuthenticationProperties 物件，其中包含驗證提供者的名稱和重新導向 URL。 然後，您會傳回傳遞 AuthenticationProperties 物件的挑戰回應。 下列程式碼將示範這項作業。

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

如果當您在 Visual Studio 中建立 ASP.NET Code Web 應用程式專案時，選擇 [Individual User Account] (個別使用者帳戶) 驗證選項，專案中已有使用外部提供者登入所需的所有程式碼，如圖 11-3 所示。

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**圖 11-3**. 建立 Web 應用程式專案時選取使用外部驗證的選項

除了先前所列的外部驗證提供者，還有協力廠商套件提供中介軟體以使用其他更多外部驗證提供者。 如需清單，請參閱 GitHub 上的 [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) 存放庫。

您當然也可以建立自己的外部驗證中介軟體。

## <a name="authenticating-with-bearer-tokens"></a>使用持有人權杖進行驗證

使用 ASP.NET Core Identity (或 Identity 加上外部驗證提供者) 進行驗證適用於許多 Web 應用程式案例，在這類案例中，適合將使用者資訊儲存在 Cookie 中。 不過在其他案例中，Cookie 不是保存及傳輸資料的自然方式。

例如，在公開 RESTful 端點的 ASP.NET Core Web API 中，由於這些端點可能是由單一頁面應用程式 (SPA)、原生用戶端或甚至是其他 Web API 存取，因此您通常會想要改用持有人權杖驗證。 這些類型的應用程式不適用於 Cookie，但可輕鬆地擷取持有人權杖，並將它包含在後續要求的授權標頭中。 若要啟用權杖驗證，ASP.NET Core 支援使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](http://openid.net/connect/) 的數個選項。

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>使用 OpenID Connect 或 OAuth 2.0 識別提供者進行驗證

如果使用者資訊儲存在 Azure Active Directory 或是支援 OpenID Connect 或 OAuth 2.0 的其他身分識別解決方案中，您可以使用 Microsoft.AspNetCore.Authentication.OpenIdConnect 套件透過 OpenID Connect 工作流程進行驗證。 例如，若要[對 Azure Active Directory 進行驗證](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)，ASP.NET Core Web 應用程式可以使用該套件中的中介軟體，如下列範例所示：

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

設定值會是將您的應用程式[註冊為 Azure AD 用戶端](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)時所建立的 Azure Active Directory 值。 如果應用程式中的多個微服務全部需要透過 Azure Active Directory 驗證使用者，則會在這些微服務之間共用單一用戶端識別碼。

請注意，當您使用此工作流程時，不需要 ASP.NET Core Identity 中介軟體，因為 Azure Active Directory 會處理所有使用者資訊的儲存與驗證。

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>從 ASP.NET Core 服務發行安全性權杖

如果您想要對本機 ASP.NET Core Identity 使用者發行安全性權杖，而不是使用外部識別提供者，您可以利用一些不錯的協力廠商程式庫。

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) 和 [OpenIddict](https://github.com/openiddict/openiddict-core) 是 OpenID Connect 提供者，可輕鬆地與 ASP.NET Core Identity 整合，讓您從 ASP.NET Core 服務發行安全性權杖。 [IdentityServer4 文件](https://identityserver4.readthedocs.io/en/release/)深入說明如何使用程式庫。 不過，使用 IdentityServer4 發行權杖的基本步驟如下。

1.  您在 Startup.Configure 方法中呼叫 app.UseIdentityServer，以將 IdentityServer4 新增至應用程式的 HTTP 要求處理管線。 這可讓程式庫服務 OpenID Connect 和 OAuth2 端點的要求，例如 /connect/token。

2.  您呼叫 services.AddIdentityServer，以設定 IdentityServer4 in Startup.ConfigureServices。

3.  若要設定識別伺服器，請提供下列資料：

-   用於簽署的[認證](https://identityserver4.readthedocs.io/en/release/topics/crypto.html)。

-   使用者可能要求存取的[身分識別和 API 資源](https://identityserver4.readthedocs.io/en/release/topics/resources.html)：

<!-- -->

-   代表使用者可透過存取權杖存取之受保護資料或功能的 API 資源。 API 資源的一個範例是需要授權的 Web API (或一組 API)。

-   代表資訊 (宣告) 的資源，這些資訊 (宣告) 已提供給用戶端來識別使用者。 宣告可能包含使用者名稱、電子郵件地址等等。

<!-- -->

-   將連線以要求權杖的[用戶端](https://identityserver4.readthedocs.io/en/release/topics/clients.html)。

-   使用者資訊的儲存機制，例如 [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) 或替代方案。

當您指定要讓 IdentityServer4 使用的用戶端和資源時，您可以將適當類型的 IEnumerable&lt;T&gt; 集合傳遞至接受記憶體內部用戶端或資源存放區的方法。 在更複雜的情況下，您可能會透過相依性插入提供用戶端或資源提供者類型。

讓 IdentityServer4 使用自訂 IClientStore 類型所提供之記憶體內部資源和用戶端的範例設定可能如下列範例所示：

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>取用安全性權杖

對 OpenID Connect 端點進行驗證或發行您自己的安全性權杖涵蓋一些案例。 但如果服務只需要將存取權限制給具有其他服務所提供之有效安全性權杖的使用者，又如何？

針對該案例，Microsoft.AspNetCore.Authentication.JwtBearer 套件會提供用於處理 JWT 權杖的驗證中介軟體。 JWT 代表 "[JSON Web Token](https://tools.ietf.org/html/rfc7519)"，這是用於傳達安全性宣告的常見安全性權杖格式 (由 RFC 7519 定義)。 一個示範如何使用中介軟體來取用這類權杖的簡單範例可能如下列範例所示。 此程式碼必須在呼叫 ASP.NET Core MVC 中介軟體 (app.UseMvc) 之前。

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

此用法的參數如下：

-   Audience 代表權杖授與存取權之傳入權杖或資源的接收者。 如果此參數中指定的值不符合權杖中的 aud 參數，則會拒絕此權杖。

-   Authority 是發行權杖之驗證伺服器的位址。 JWT 持有人驗證中介軟體使用此 URI 來取得公開金鑰，以用來驗證權杖的簽章。 中介軟體也會確認權杖中的 iss 參數符合此 URI。

-   AutomaticAuthenticate 是布林值，指出由權杖定義的使用者是否應該自動登入。

另一個參數 RequireHttpsMetadata 不會在此範例中使用。 它可供測試之用；您可以將此參數設定為 false，以便在沒有憑證的環境中進行測試。 在真實世界部署中，JWT 持有人權杖一律只能透過 HTTPS 傳遞。

準備好此中介軟體之後，就會從授權標頭自動擷取 JWT 權杖。 這些權杖會接著還原序列化、驗證 (使用 Audience 和 Authority 參數中的值) 並儲存為使用者資訊，以供 MVC 動作或授權篩選稍後參考。

JWT 持有人驗證中介軟體也可以支援更進階的案例；例如，在沒有授權單位的情況下，使用本機憑證來驗證權杖。 針對此案例，您可以在 JwtBearerOptions 物件中指定 TokenValidationParameters 物件。

## <a name="additional-resources"></a>其他資源

-   **Sharing cookies between applications** (共用應用程式之間的 Cookie)
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Introduction to Identity** (Identity 簡介)
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson，Two-factor authentication with SMS** (使用 SMS 的雙因素驗證)
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Enabling authentication using Facebook, Google and other external providers** (使用 Facebook、Google 和其他外部提供者啟用驗證)
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas，An Introduction to OAuth 2** (OAuth 2 簡介)
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (ASP.NET OAuth 提供者的 GitHub 存放庫。
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis，Integrating Azure AD into an ASP.NET Core web app** (將 Azure AD 整合到 ASP.NET Core Web 應用程式中)
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4，官方文件**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[上一個] (../implement-resilient-applications/monitor-app-health.md) [下一個] (authorization-net-microservices-web-applications.md)

