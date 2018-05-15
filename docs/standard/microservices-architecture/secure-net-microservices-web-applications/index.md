---
title: 保護 .NET 微服務和 Web 應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 保護 .NET 微服務和 Web 應用程式
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c2c7d692517c6a46225542936e05656db915bf0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="237f2-103">保護 .NET 微服務和 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="237f2-103">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="237f2-104">您通常必須將服務所公開的資源和 API 限制給某些信任的使用者或用戶端。</span><span class="sxs-lookup"><span data-stu-id="237f2-104">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="237f2-105">制定這類 API 層級信任決策的第一個步驟是驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-105">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="237f2-106">驗證是可靠地確認使用者身分識別的程序。</span><span class="sxs-lookup"><span data-stu-id="237f2-106">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="237f2-107">在微服務案例中，通常會集中處理驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-107">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="237f2-108">如果您使用 API 閘道，閘道是適合驗證的位置，如圖 11-1 所示。</span><span class="sxs-lookup"><span data-stu-id="237f2-108">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="237f2-109">如果您使用此方法，請確定若沒有 API 閘道，就無法直接到達個別微服務，除非有其他安全性機制可驗證訊息，而不論其是否來自閘道。</span><span class="sxs-lookup"><span data-stu-id="237f2-109">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="237f2-110">**圖 11-1**.</span><span class="sxs-lookup"><span data-stu-id="237f2-110">**Figure 11-1**.</span></span> <span data-ttu-id="237f2-111">使用 API 閘道的集中式驗證</span><span class="sxs-lookup"><span data-stu-id="237f2-111">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="237f2-112">如果服務可供直接存取，則可以使用 Azure Active Directory 等驗證服務或作為 Security Token Service (STS) 的專用驗證微服務來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="237f2-112">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="237f2-113">信任決策會透過安全性權杖或 Cookie 在服務之間共用</span><span class="sxs-lookup"><span data-stu-id="237f2-113">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="237f2-114">(如有必要，可透過[資料保護服務](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)在 ASP.NET Core 應用程式之間共用)。圖 11-2 說明的就是這種模式。</span><span class="sxs-lookup"><span data-stu-id="237f2-114">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="237f2-115">**圖 11-2**.</span><span class="sxs-lookup"><span data-stu-id="237f2-115">**Figure 11-2**.</span></span> <span data-ttu-id="237f2-116">由識別微服務驗證並透過授權權杖共用信任</span><span class="sxs-lookup"><span data-stu-id="237f2-116">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="237f2-117">使用 ASP.NET Core Identity 進行驗證</span><span class="sxs-lookup"><span data-stu-id="237f2-117">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="237f2-118">ASP.NET Core 中用來識別應用程式使用者的主要機制是 [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) 成員資格系統。</span><span class="sxs-lookup"><span data-stu-id="237f2-118">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="237f2-119">ASP.NET Core Identity 會將使用者資訊 (包括登入資訊、角色和宣告) 儲存在開發人員所設定的資料存放區中。</span><span class="sxs-lookup"><span data-stu-id="237f2-119">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="237f2-120">一般而言，ASP.NET Core Identity 資料存放區是 Microsoft.AspNetCore.Identity.EntityFrameworkCore 套件中所提供的 Entity Framework 存放區。</span><span class="sxs-lookup"><span data-stu-id="237f2-120">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="237f2-121">不過，您可以使用自訂存放區或其他協力廠商套件，將身分識別資訊儲存在 Azure 資料表儲存體、DocumentDB 或其他位置。</span><span class="sxs-lookup"><span data-stu-id="237f2-121">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="237f2-122">下列程式碼擷取自 ASP.NET Core Web 應用程式專案範本，並已選取個別使用者帳戶驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-122">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="237f2-123">其示範如何使用 Startup.ConfigureServices 方法中的 EntityFramework.Core 來設定 ASP.NET Core Identity。</span><span class="sxs-lookup"><span data-stu-id="237f2-123">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="237f2-124">設定 ASP.NET Core Identity 之後，您可以在服務的 Startup.Configure 方法中呼叫 app.UseIdentity 加以啟用。</span><span class="sxs-lookup"><span data-stu-id="237f2-124">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="237f2-125">您可以在下列幾個情況下使用 ASP.NET Code Identity：</span><span class="sxs-lookup"><span data-stu-id="237f2-125">Using ASP.NET Code Identity enables several scenarios:</span></span>

-   <span data-ttu-id="237f2-126">使用 UserManager 類型 (userManager.CreateAsync) 建立新的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="237f2-126">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="237f2-127">使用 SignInManager 類型驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="237f2-127">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="237f2-128">您可以使用 signInManager.SignInAsync 直接登入，或使用 signInManager.PasswordSignInAsync 確認使用者的密碼正確後再將他們登入。</span><span class="sxs-lookup"><span data-stu-id="237f2-128">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="237f2-129">根據儲存在 Cookie 中的資訊 (由 ASP.NET Core Identity 中介軟體讀取) 識別使用者；如此一來，來自瀏覽器的後續要求就會包含已登入使用者的身分識別和宣告。</span><span class="sxs-lookup"><span data-stu-id="237f2-129">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="237f2-130">ASP.NET Core Identity 也支援[雙因素驗證](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)。</span><span class="sxs-lookup"><span data-stu-id="237f2-130">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="237f2-131">針對使用本機使用者資料存放區，以及使用 Cookie 在要求之間保存身分識別 (通常適用於 MVC Web 應用程式) 的驗證案例，ASP.NET Core Identity 是建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="237f2-131">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="237f2-132">使用外部提供者進行驗證</span><span class="sxs-lookup"><span data-stu-id="237f2-132">Authenticating using external providers</span></span>

<span data-ttu-id="237f2-133">ASP.NET Core 也支援使用[外部驗證提供者](https://docs.microsoft.com/aspnet/core/security/authentication/social/)，讓使用者透過 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流程登入。</span><span class="sxs-lookup"><span data-stu-id="237f2-133">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="237f2-134">這表示使用者可以使用來自 Microsoft、Google、Facebook 或 Twitter 等提供者的現有驗證程序進行登入，並將這些身分識別與您應用程式中的 ASP.NET Core Identity 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="237f2-134">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="237f2-135">若要使用外部驗證，您可以在應用程式的 HTTP 要求處理管線中包含適當的驗證中介軟體。</span><span class="sxs-lookup"><span data-stu-id="237f2-135">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="237f2-136">此中介軟體會負責處理從驗證提供者傳回 URI 路由的要求、擷取身分識別資訊，並透過 SignInManager.GetExternalLoginInfo 方法來提供此資訊。</span><span class="sxs-lookup"><span data-stu-id="237f2-136">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="237f2-137">以下顯示熱門的外部驗證提供者及其關聯的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="237f2-137">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="237f2-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="237f2-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="237f2-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="237f2-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="237f2-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="237f2-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="237f2-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="237f2-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="237f2-142">在所有情況下，會使用類似於 app.Use{ExternalProvider}Authentication in Startup.Configure 的註冊方法來註冊中介軟體。</span><span class="sxs-lookup"><span data-stu-id="237f2-142">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="237f2-143">視提供者需要，這些註冊方法會接受選項物件，其中包含應用程式識別碼和秘密資訊 (例如密碼)。</span><span class="sxs-lookup"><span data-stu-id="237f2-143">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="237f2-144">外部驗證提供者需要註冊應用程式 (如 [ASP.NET Core 文件](https://docs.microsoft.com/aspnet/core/security/authentication/social/)中所述)，才能通知使用者哪個應用程式要求存取其身分識別。</span><span class="sxs-lookup"><span data-stu-id="237f2-144">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="237f2-145">在 Startup.Configure 中註冊中介軟體之後，您可以提示使用者透過任何控制器動作登入。</span><span class="sxs-lookup"><span data-stu-id="237f2-145">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="237f2-146">若要這樣做，您可以建立 AuthenticationProperties 物件，其中包含驗證提供者的名稱和重新導向 URL。</span><span class="sxs-lookup"><span data-stu-id="237f2-146">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="237f2-147">然後，您會傳回傳遞 AuthenticationProperties 物件的挑戰回應。</span><span class="sxs-lookup"><span data-stu-id="237f2-147">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="237f2-148">下列程式碼將示範這項作業。</span><span class="sxs-lookup"><span data-stu-id="237f2-148">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="237f2-149">redirectUrl 參數包含驗證使用者之後，外部提供者應該重新導向的目標 URL。</span><span class="sxs-lookup"><span data-stu-id="237f2-149">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="237f2-150">此 URL 應該代表根據外部身分識別資訊將使用者登入的動作，如下列簡化範例所示：</span><span class="sxs-lookup"><span data-stu-id="237f2-150">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="237f2-151">如果當您在 Visual Studio 中建立 ASP.NET Code Web 應用程式專案時，選擇 [Individual User Account] (個別使用者帳戶) 驗證選項，專案中已有使用外部提供者登入所需的所有程式碼，如圖 11-3 所示。</span><span class="sxs-lookup"><span data-stu-id="237f2-151">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="237f2-152">**圖 11-3**.</span><span class="sxs-lookup"><span data-stu-id="237f2-152">**Figure 11-3**.</span></span> <span data-ttu-id="237f2-153">建立 Web 應用程式專案時選取使用外部驗證的選項</span><span class="sxs-lookup"><span data-stu-id="237f2-153">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="237f2-154">除了先前所列的外部驗證提供者，還有協力廠商套件提供中介軟體以使用其他更多外部驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="237f2-154">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="237f2-155">如需清單，請參閱 GitHub 上的 [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="237f2-155">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="237f2-156">您當然也可以建立自己的外部驗證中介軟體。</span><span class="sxs-lookup"><span data-stu-id="237f2-156">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="237f2-157">使用持有人權杖進行驗證</span><span class="sxs-lookup"><span data-stu-id="237f2-157">Authenticating with bearer tokens</span></span>

<span data-ttu-id="237f2-158">使用 ASP.NET Core Identity (或 Identity 加上外部驗證提供者) 進行驗證適用於許多 Web 應用程式案例，在這類案例中，適合將使用者資訊儲存在 Cookie 中。</span><span class="sxs-lookup"><span data-stu-id="237f2-158">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="237f2-159">不過在其他案例中，Cookie 不是保存及傳輸資料的自然方式。</span><span class="sxs-lookup"><span data-stu-id="237f2-159">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="237f2-160">例如，在公開 RESTful 端點的 ASP.NET Core Web API 中，由於這些端點可能是由單一頁面應用程式 (SPA)、原生用戶端或甚至是其他 Web API 存取，因此您通常會想要改用持有人權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-160">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="237f2-161">這些類型的應用程式不適用於 Cookie，但可輕鬆地擷取持有人權杖，並將它包含在後續要求的授權標頭中。</span><span class="sxs-lookup"><span data-stu-id="237f2-161">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="237f2-162">若要啟用權杖驗證，ASP.NET Core 支援使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](https://openid.net/connect/) 的數個選項。</span><span class="sxs-lookup"><span data-stu-id="237f2-162">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="237f2-163">使用 OpenID Connect 或 OAuth 2.0 識別提供者進行驗證</span><span class="sxs-lookup"><span data-stu-id="237f2-163">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="237f2-164">如果使用者資訊儲存在 Azure Active Directory 或是支援 OpenID Connect 或 OAuth 2.0 的其他身分識別解決方案中，您可以使用 Microsoft.AspNetCore.Authentication.OpenIdConnect 套件透過 OpenID Connect 工作流程進行驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-164">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="237f2-165">例如，若要[對 Azure Active Directory 進行驗證](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)，ASP.NET Core Web 應用程式可以使用該套件中的中介軟體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="237f2-165">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="237f2-166">設定值會是將您的應用程式[註冊為 Azure AD 用戶端](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)時所建立的 Azure Active Directory 值。</span><span class="sxs-lookup"><span data-stu-id="237f2-166">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="237f2-167">如果應用程式中的多個微服務全部需要透過 Azure Active Directory 驗證使用者，則會在這些微服務之間共用單一用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="237f2-167">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="237f2-168">請注意，當您使用此工作流程時，不需要 ASP.NET Core Identity 中介軟體，因為 Azure Active Directory 會處理所有使用者資訊的儲存與驗證。</span><span class="sxs-lookup"><span data-stu-id="237f2-168">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="237f2-169">從 ASP.NET Core 服務發行安全性權杖</span><span class="sxs-lookup"><span data-stu-id="237f2-169">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="237f2-170">如果您想要對本機 ASP.NET Core Identity 使用者發行安全性權杖，而不是使用外部識別提供者，您可以利用一些不錯的協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="237f2-170">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="237f2-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) 和 [OpenIddict](https://github.com/openiddict/openiddict-core) 是 OpenID Connect 提供者，可輕鬆地與 ASP.NET Core Identity 整合，讓您從 ASP.NET Core 服務發行安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="237f2-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="237f2-172">[IdentityServer4 文件](https://identityserver4.readthedocs.io/en/release/)深入說明如何使用程式庫。</span><span class="sxs-lookup"><span data-stu-id="237f2-172">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="237f2-173">不過，使用 IdentityServer4 發行權杖的基本步驟如下。</span><span class="sxs-lookup"><span data-stu-id="237f2-173">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="237f2-174">您在 Startup.Configure 方法中呼叫 app.UseIdentityServer，以將 IdentityServer4 新增至應用程式的 HTTP 要求處理管線。</span><span class="sxs-lookup"><span data-stu-id="237f2-174">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="237f2-175">這可讓程式庫服務 OpenID Connect 和 OAuth2 端點的要求，例如 /connect/token。</span><span class="sxs-lookup"><span data-stu-id="237f2-175">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="237f2-176">您呼叫 services.AddIdentityServer，以設定 IdentityServer4 in Startup.ConfigureServices。</span><span class="sxs-lookup"><span data-stu-id="237f2-176">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="237f2-177">若要設定識別伺服器，請提供下列資料：</span><span class="sxs-lookup"><span data-stu-id="237f2-177">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="237f2-178">用於簽署的[認證](https://identityserver4.readthedocs.io/en/release/topics/crypto.html)。</span><span class="sxs-lookup"><span data-stu-id="237f2-178">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="237f2-179">使用者可能要求存取的[身分識別和 API 資源](https://identityserver4.readthedocs.io/en/release/topics/resources.html)：</span><span class="sxs-lookup"><span data-stu-id="237f2-179">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="237f2-180">代表使用者可透過存取權杖存取之受保護資料或功能的 API 資源。</span><span class="sxs-lookup"><span data-stu-id="237f2-180">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="237f2-181">API 資源的一個範例是需要授權的 Web API (或一組 API)。</span><span class="sxs-lookup"><span data-stu-id="237f2-181">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="237f2-182">代表資訊 (宣告) 的資源，這些資訊 (宣告) 已提供給用戶端來識別使用者。</span><span class="sxs-lookup"><span data-stu-id="237f2-182">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="237f2-183">宣告可能包含使用者名稱、電子郵件地址等等。</span><span class="sxs-lookup"><span data-stu-id="237f2-183">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="237f2-184">將連線以要求權杖的[用戶端](https://identityserver4.readthedocs.io/en/release/topics/clients.html)。</span><span class="sxs-lookup"><span data-stu-id="237f2-184">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="237f2-185">使用者資訊的儲存機制，例如 [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) 或替代方案。</span><span class="sxs-lookup"><span data-stu-id="237f2-185">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="237f2-186">當您指定要讓 IdentityServer4 使用的用戶端和資源時，您可以將適當類型的 IEnumerable&lt;T&gt; 集合傳遞至接受記憶體內部用戶端或資源存放區的方法。</span><span class="sxs-lookup"><span data-stu-id="237f2-186">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="237f2-187">在更複雜的情況下，您可能會透過相依性插入提供用戶端或資源提供者類型。</span><span class="sxs-lookup"><span data-stu-id="237f2-187">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="237f2-188">讓 IdentityServer4 使用自訂 IClientStore 類型所提供之記憶體內部資源和用戶端的範例設定可能如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="237f2-188">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="237f2-189">取用安全性權杖</span><span class="sxs-lookup"><span data-stu-id="237f2-189">Consuming security tokens</span></span>

<span data-ttu-id="237f2-190">對 OpenID Connect 端點進行驗證或發行您自己的安全性權杖涵蓋一些案例。</span><span class="sxs-lookup"><span data-stu-id="237f2-190">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="237f2-191">但如果服務只需要將存取權限制給具有其他服務所提供之有效安全性權杖的使用者，又如何？</span><span class="sxs-lookup"><span data-stu-id="237f2-191">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="237f2-192">針對該案例，Microsoft.AspNetCore.Authentication.JwtBearer 套件會提供用於處理 JWT 權杖的驗證中介軟體。</span><span class="sxs-lookup"><span data-stu-id="237f2-192">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="237f2-193">JWT 代表 "[JSON Web Token](https://tools.ietf.org/html/rfc7519)"，這是用於傳達安全性宣告的常見安全性權杖格式 (由 RFC 7519 定義)。</span><span class="sxs-lookup"><span data-stu-id="237f2-193">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="237f2-194">一個示範如何使用中介軟體來取用這類權杖的簡單範例可能如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="237f2-194">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="237f2-195">此程式碼必須在呼叫 ASP.NET Core MVC 中介軟體 (app.UseMvc) 之前。</span><span class="sxs-lookup"><span data-stu-id="237f2-195">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="237f2-196">此用法的參數如下：</span><span class="sxs-lookup"><span data-stu-id="237f2-196">The parameters in this usage are:</span></span>

-   <span data-ttu-id="237f2-197">Audience 代表權杖授與存取權之傳入權杖或資源的接收者。</span><span class="sxs-lookup"><span data-stu-id="237f2-197">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="237f2-198">如果此參數中指定的值不符合權杖中的 aud 參數，則會拒絕此權杖。</span><span class="sxs-lookup"><span data-stu-id="237f2-198">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="237f2-199">Authority 是發行權杖之驗證伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="237f2-199">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="237f2-200">JWT 持有人驗證中介軟體使用此 URI 來取得公開金鑰，以用來驗證權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="237f2-200">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="237f2-201">中介軟體也會確認權杖中的 iss 參數符合此 URI。</span><span class="sxs-lookup"><span data-stu-id="237f2-201">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="237f2-202">AutomaticAuthenticate 是布林值，指出由權杖定義的使用者是否應該自動登入。</span><span class="sxs-lookup"><span data-stu-id="237f2-202">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="237f2-203">另一個參數 RequireHttpsMetadata 不會在此範例中使用。</span><span class="sxs-lookup"><span data-stu-id="237f2-203">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="237f2-204">它可供測試之用；您可以將此參數設定為 false，以便在沒有憑證的環境中進行測試。</span><span class="sxs-lookup"><span data-stu-id="237f2-204">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="237f2-205">在真實世界部署中，JWT 持有人權杖一律只能透過 HTTPS 傳遞。</span><span class="sxs-lookup"><span data-stu-id="237f2-205">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="237f2-206">準備好此中介軟體之後，就會從授權標頭自動擷取 JWT 權杖。</span><span class="sxs-lookup"><span data-stu-id="237f2-206">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="237f2-207">這些權杖會接著還原序列化、驗證 (使用 Audience 和 Authority 參數中的值) 並儲存為使用者資訊，以供 MVC 動作或授權篩選稍後參考。</span><span class="sxs-lookup"><span data-stu-id="237f2-207">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="237f2-208">JWT 持有人驗證中介軟體也可以支援更進階的案例；例如，在沒有授權單位的情況下，使用本機憑證來驗證權杖。</span><span class="sxs-lookup"><span data-stu-id="237f2-208">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="237f2-209">針對此案例，您可以在 JwtBearerOptions 物件中指定 TokenValidationParameters 物件。</span><span class="sxs-lookup"><span data-stu-id="237f2-209">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="237f2-210">其他資源</span><span class="sxs-lookup"><span data-stu-id="237f2-210">Additional resources</span></span>

-   <span data-ttu-id="237f2-211">**共用應用程式間的 Cookie**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="237f2-211">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="237f2-212">**身分識別簡介**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="237f2-212">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="237f2-213">**Rick Anderson，使用 SMS 的雙因素驗證**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="237f2-213">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="237f2-214">**使用 Facebook、Google 和其他外部提供者啟用驗證**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="237f2-214">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="237f2-215">**Michell Anicas，OAuth 2 簡介**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="237f2-215">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="237f2-216">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth 提供者的 GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="237f2-216">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="237f2-217">**Danny Strockis，將 Azure AD 整合到 ASP.NET Core Web 應用程式**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="237f2-217">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="237f2-218">**IdentityServer4，正式文件**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="237f2-218">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="237f2-219">[上一個] (../implement-resilient-applications/monitor-app-health.md) [下一個] (authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="237f2-219">[Previous] (../implement-resilient-applications/monitor-app-health.md) [Next] (authorization-net-microservices-web-applications.md)</span></span>
