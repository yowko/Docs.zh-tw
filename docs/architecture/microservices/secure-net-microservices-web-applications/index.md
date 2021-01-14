---
title: 保護 .NET 微服務和 Web 應用程式
description: .NET 微服務和 Web 應用程式中的安全性 - 了解 ASP.NET Core Web 應用程式中的驗證選項。
author: mjrousos
ms.date: 01/13/2021
ms.openlocfilehash: 1bb03e8abdf6daa0b6c4570eb35643898f797cc0
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188040"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="e6e92-103">製作安全的 .NET 微服務和 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6e92-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="e6e92-104">在微服務和 web 應用程式中，有許多關於安全性的層面，主題可以輕易地採用這類書籍。</span><span class="sxs-lookup"><span data-stu-id="e6e92-104">There are so many aspects about security in microservices and web applications that the topic could easily take several books like this one.</span></span> <span data-ttu-id="e6e92-105">因此，在本節中，我們將著重于驗證、授權和應用程式秘密。</span><span class="sxs-lookup"><span data-stu-id="e6e92-105">So, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="e6e92-106">在 .NET 微服務和 Web 應用程式中實作驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-106">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="e6e92-107">您通常必須將服務發佈的資源和 API 限制給某些信任的使用者或用戶端。</span><span class="sxs-lookup"><span data-stu-id="e6e92-107">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="e6e92-108">制定這類 API 層級信任決策的第一個步驟是驗證。</span><span class="sxs-lookup"><span data-stu-id="e6e92-108">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="e6e92-109">驗證是可靠地驗證使用者身分識別的程式。</span><span class="sxs-lookup"><span data-stu-id="e6e92-109">Authentication is the process of reliably verifying a user's identity.</span></span>

<span data-ttu-id="e6e92-110">在微服務案例中，驗證通常會集中處理。</span><span class="sxs-lookup"><span data-stu-id="e6e92-110">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="e6e92-111">如果您使用 API 閘道，則閘道會是適合驗證的位置，如圖 9-1 所示。</span><span class="sxs-lookup"><span data-stu-id="e6e92-111">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="e6e92-112">如果您使用此方法，請確定若沒有 API 閘道，就無法直接到達個別微服務，除非有其他安全性機制可驗證訊息，而不論其是否來自閘道。</span><span class="sxs-lookup"><span data-stu-id="e6e92-112">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![顯示用戶端行動應用程式如何與後端互動的圖表。](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="e6e92-114">**圖 9-1**.</span><span class="sxs-lookup"><span data-stu-id="e6e92-114">**Figure 9-1**.</span></span> <span data-ttu-id="e6e92-115">使用 API 閘道的集中式驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-115">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="e6e92-116">當 API 閘道將驗證集中時，會在將要求轉送給微服務時新增使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="e6e92-116">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="e6e92-117">如果可以直接存取服務，則驗證服務 (例如 Azure Active Directory 或專用驗證微服務) 會作為安全性權杖服務 (STS)，可用來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="e6e92-117">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="e6e92-118">信任決策會在服務與安全性權杖或 Cookie 之間共用。</span><span class="sxs-lookup"><span data-stu-id="e6e92-118">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="e6e92-119"> (可以在 ASP.NET Core 應用程式之間共用這些權杖（如有需要），方法是執行 [cookie 共用](/aspnet/core/security/cookie-sharing)。如圖9-2 中所示，會 ) 此模式。</span><span class="sxs-lookup"><span data-stu-id="e6e92-119">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![顯示透過後端微服務進行驗證的圖表。](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="e6e92-121">**圖 9-2**：</span><span class="sxs-lookup"><span data-stu-id="e6e92-121">**Figure 9-2**.</span></span> <span data-ttu-id="e6e92-122">由識別微服務驗證並透過授權權杖共用信任</span><span class="sxs-lookup"><span data-stu-id="e6e92-122">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="e6e92-123">有人直接存取微服務時，包含驗證和授權的信任將由專用微服務發行的安全性權杖處理，於微服務間共用。</span><span class="sxs-lookup"><span data-stu-id="e6e92-123">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="e6e92-124">使用 ASP.NET Core Identity 進行驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-124">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="e6e92-125">ASP.NET Core 中識別應用程式使用者的主要機制是 [ASP.NET Core 身分識別](/aspnet/core/security/authentication/identity) 成員資格系統。</span><span class="sxs-lookup"><span data-stu-id="e6e92-125">The primary mechanism in ASP.NET Core for identifying an application's users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="e6e92-126">ASP.NET Core 身分識別會將使用者資訊 (包括登入資訊、角色及宣告) 儲存在由開發人員設定的資料存放區中。</span><span class="sxs-lookup"><span data-stu-id="e6e92-126">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="e6e92-127">一般而言，ASP.NET Core Identity 資料存放區是 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 套件中所提供的 Entity Framework 存放區。</span><span class="sxs-lookup"><span data-stu-id="e6e92-127">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="e6e92-128">不過，您可以使用自訂存放區或其他協力廠商套件，將身分識別資訊儲存在 Azure 表格儲存體、CosmosDB 或其他位置。</span><span class="sxs-lookup"><span data-stu-id="e6e92-128">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="e6e92-129">ASP.NET Core 2.1 和更新版本以[Razor 類別庫](/aspnet/core/razor-pages/ui-class)的形式提供[ASP.NET Core 身分識別](/aspnet/core/security/authentication/identity)，因此您不會在專案中看到許多必要的程式碼，就像舊版的情況一樣。</span><span class="sxs-lookup"><span data-stu-id="e6e92-129">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="e6e92-130">如需如何自訂身分識別程式碼以符合您的需求的詳細資訊，請參閱 [ASP.NET Core 專案中的 Scaffold 身分識別](/aspnet/core/security/authentication/scaffold-identity)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-130">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="e6e92-131">下列程式碼取自已選取個別使用者帳戶驗證的 ASP.NET Core Web 應用程式 MVC 3.1 專案範本。</span><span class="sxs-lookup"><span data-stu-id="e6e92-131">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="e6e92-132">它會示範如何在方法中使用 Entity Framework Core 來設定 ASP.NET Core 身分識別 `Startup.ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="e6e92-132">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

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

<span data-ttu-id="e6e92-133">設定 ASP.NET Core 身分識別之後，您可以藉由新增來啟用它， `app.UseAuthentication()` `endpoints.MapRazorPages()` 如服務的方法中的下列程式碼所示 `Startup.Configure` ：</span><span class="sxs-lookup"><span data-stu-id="e6e92-133">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

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
> <span data-ttu-id="e6e92-134">上述程式碼中的程式程式碼 **必須依照顯示的順序** ，才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="e6e92-134">The lines in the preceding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="e6e92-135">您可以在下列幾個情況下使用 ASP.NET Code Identity：</span><span class="sxs-lookup"><span data-stu-id="e6e92-135">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="e6e92-136">使用 UserManager 類型 (userManager.CreateAsync) 建立新的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="e6e92-136">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="e6e92-137">使用 SignInManager 類型驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="e6e92-137">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="e6e92-138">您可以使用 `signInManager.SignInAsync` 來直接登入，或 `signInManager.PasswordSignInAsync` 確認使用者的密碼正確，然後將其登入。</span><span class="sxs-lookup"><span data-stu-id="e6e92-138">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user's password is correct and then sign them in.</span></span>

- <span data-ttu-id="e6e92-139">根據儲存在 cookie 中的資訊來識別使用者 (由 ASP.NET Core 身分識別中介軟體) 讀取，讓瀏覽器的後續要求將會包含已登入使用者的身分識別和宣告。</span><span class="sxs-lookup"><span data-stu-id="e6e92-139">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user's identity and claims.</span></span>

<span data-ttu-id="e6e92-140">ASP.NET Core Identity 也支援[雙因素驗證](/aspnet/core/security/authentication/2fa)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-140">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="e6e92-141">針對使用本機使用者資料存放區，以及使用 Cookie 在要求之間保存身分識別 (通常適用於 MVC Web 應用程式) 的驗證案例，ASP.NET Core Identity 是建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e6e92-141">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="e6e92-142">使用外部提供者進行驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-142">Authenticate with external providers</span></span>

<span data-ttu-id="e6e92-143">ASP.NET Core 也支援使用[外部驗證提供者](/aspnet/core/security/authentication/social/)，讓使用者透過 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流程登入。</span><span class="sxs-lookup"><span data-stu-id="e6e92-143">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="e6e92-144">這表示使用者可以使用來自 Microsoft、Google、Facebook 或 Twitter 等提供者的現有驗證程序進行登入，並將這些身分識別與您應用程式中的 ASP.NET Core Identity 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="e6e92-144">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="e6e92-145">若要使用外部驗證，除了包含先前提及的驗證中介軟體之外，使用 `app.UseAuthentication()` 方法，您也必須在中註冊外部提供者， `Startup` 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e6e92-145">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

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

<span data-ttu-id="e6e92-146">下表顯示熱門的外部驗證提供者及其關聯的 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="e6e92-146">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="e6e92-147">**提供者**</span><span class="sxs-lookup"><span data-stu-id="e6e92-147">**Provider**</span></span>  | <span data-ttu-id="e6e92-148">**套件**</span><span class="sxs-lookup"><span data-stu-id="e6e92-148">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="e6e92-149">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="e6e92-149">**Microsoft**</span></span> | <span data-ttu-id="e6e92-150">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="e6e92-150">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="e6e92-151">**Google**</span><span class="sxs-lookup"><span data-stu-id="e6e92-151">**Google**</span></span>    | <span data-ttu-id="e6e92-152">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="e6e92-152">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="e6e92-153">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="e6e92-153">**Facebook**</span></span>  | <span data-ttu-id="e6e92-154">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="e6e92-154">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="e6e92-155">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="e6e92-155">**Twitter**</span></span>   | <span data-ttu-id="e6e92-156">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="e6e92-156">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="e6e92-157">在所有情況下，您都必須完成與廠商相依的應用程式註冊程式，且通常包含：</span><span class="sxs-lookup"><span data-stu-id="e6e92-157">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="e6e92-158">取得用戶端應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6e92-158">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="e6e92-159">取得用戶端應用程式秘密。</span><span class="sxs-lookup"><span data-stu-id="e6e92-159">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="e6e92-160">設定重新導向 URL，此 URL 是由授權中介軟體和已註冊的提供者所處理</span><span class="sxs-lookup"><span data-stu-id="e6e92-160">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="e6e92-161">（選擇性）設定登出 URL，以在單一登入 (SSO) 案例中適當地處理登出。</span><span class="sxs-lookup"><span data-stu-id="e6e92-161">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="e6e92-162">如需為外部提供者設定應用程式的詳細資訊，請參閱 [ASP.NET Core 檔中的外部提供者驗證](/aspnet/core/security/authentication/social/)) 。</span><span class="sxs-lookup"><span data-stu-id="e6e92-162">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="e6e92-163">所有詳細資料都是由先前所述的授權中介軟體和服務所處理。</span><span class="sxs-lookup"><span data-stu-id="e6e92-163">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="e6e92-164">因此，當您在 Visual Studio 中建立 ASP.NET 程式碼 web 應用程式專案時，您只需要選擇 **個別的使用者帳戶** 驗證選項，如 [圖 9-3] 所示，除了註冊先前提及的驗證提供者之外。</span><span class="sxs-lookup"><span data-stu-id="e6e92-164">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![[新增 ASP.NET Core Web 應用程式] 對話方塊的螢幕擷取畫面。](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="e6e92-166">**圖 9-3**。</span><span class="sxs-lookup"><span data-stu-id="e6e92-166">**Figure 9-3**.</span></span> <span data-ttu-id="e6e92-167">在 Visual Studio 2019 中建立 web 應用程式專案時，選取 [個別使用者帳戶] 選項，以用於使用外部驗證。</span><span class="sxs-lookup"><span data-stu-id="e6e92-167">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="e6e92-168">除了先前所列的外部驗證提供者，還有協力廠商套件提供中介軟體以使用其他更多外部驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="e6e92-168">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="e6e92-169">如需清單，請參閱 GitHub 上的 AspNet. 資訊儲存 [機制](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) 。</span><span class="sxs-lookup"><span data-stu-id="e6e92-169">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="e6e92-170">您也可以建立自己的外部驗證中介軟體來解決某些特殊需求。</span><span class="sxs-lookup"><span data-stu-id="e6e92-170">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="e6e92-171">使用持有人權杖進行驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-171">Authenticate with bearer tokens</span></span>

<span data-ttu-id="e6e92-172">使用 ASP.NET Core Identity (或 Identity 加上外部驗證提供者) 進行驗證適用於許多 Web 應用程式案例，在這類案例中，適合將使用者資訊儲存在 Cookie 中。</span><span class="sxs-lookup"><span data-stu-id="e6e92-172">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="e6e92-173">不過在其他案例中，Cookie 不是保存及傳輸資料的自然方式。</span><span class="sxs-lookup"><span data-stu-id="e6e92-173">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="e6e92-174">例如，在公開 RESTful 端點的 ASP.NET Core Web API 中，由於這些端點可能是由單一頁面應用程式 (SPA)、原生用戶端或甚至是其他 Web API 存取，因此您通常會想要改用持有人權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="e6e92-174">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="e6e92-175">這些類型的應用程式不適用於 Cookie，但可輕鬆地擷取持有人權杖，並將它包含在後續要求的授權標頭中。</span><span class="sxs-lookup"><span data-stu-id="e6e92-175">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="e6e92-176">若要啟用權杖驗證，ASP.NET Core 支援使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](https://openid.net/connect/) 的數個選項。</span><span class="sxs-lookup"><span data-stu-id="e6e92-176">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="e6e92-177">使用 OpenID Connect 或 OAuth 2.0 識別提供者進行驗證</span><span class="sxs-lookup"><span data-stu-id="e6e92-177">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="e6e92-178">如果使用者資訊儲存在 Azure Active Directory 或其他支援 OpenID Connect 或 OAuth 2.0 的身分識別解決方案中，您可以使用 OpenID Connect 的工作流程來驗證 **OpenIdConnect** 套件。</span><span class="sxs-lookup"><span data-stu-id="e6e92-178">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="e6e92-179">例如，若要對 eShopOnContainers 中的 Identity.Api 微服務進行驗證，ASP.NET Core Web 應用程式可以使用該套件中的中介軟體，如以下 `Startup.cs` 中的簡例所示：</span><span class="sxs-lookup"><span data-stu-id="e6e92-179">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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
    var sessionCookieLifetime = Configuration.GetValue("SessionCookieLifetimeMinutes", 60);

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

<span data-ttu-id="e6e92-180">請注意，當您使用此工作流程時，不需要 ASP.NET Core Identity 中介軟體，因為識別服務會處理所有使用者資訊的儲存與驗證。</span><span class="sxs-lookup"><span data-stu-id="e6e92-180">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="e6e92-181">從 ASP.NET Core 服務發行安全性權杖</span><span class="sxs-lookup"><span data-stu-id="e6e92-181">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="e6e92-182">如果您想要對本機 ASP.NET Core Identity 使用者發行安全性權杖，而不是使用外部識別提供者，您可以利用一些不錯的協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="e6e92-182">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="e6e92-183">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) 和 [OpenIddict](https://github.com/openiddict/openiddict-core) 是 OpenID Connect 提供者，可輕鬆地與 ASP.NET Core Identity 整合，讓您從 ASP.NET Core 服務發行安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="e6e92-183">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="e6e92-184">[IdentityServer4 文件](https://identityserver4.readthedocs.io/en/latest/)深入說明如何使用程式庫。</span><span class="sxs-lookup"><span data-stu-id="e6e92-184">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="e6e92-185">不過，使用 IdentityServer4 發行權杖的基本步驟如下。</span><span class="sxs-lookup"><span data-stu-id="e6e92-185">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="e6e92-186">您會呼叫應用程式。在 Startup.Configu) 方法中 UseIdentityServer，以將 IdentityServer4 加入至應用程式的 HTTP 要求處理管線。</span><span class="sxs-lookup"><span data-stu-id="e6e92-186">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application's HTTP request processing pipeline.</span></span> <span data-ttu-id="e6e92-187">這可讓程式庫服務 OpenID Connect 和 OAuth2 端點的要求，例如 /connect/token。</span><span class="sxs-lookup"><span data-stu-id="e6e92-187">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="e6e92-188">您呼叫 services.AddIdentityServer，以設定 IdentityServer4 in Startup.ConfigureServices。</span><span class="sxs-lookup"><span data-stu-id="e6e92-188">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="e6e92-189">若要設定識別伺服器，請設定下列資料：</span><span class="sxs-lookup"><span data-stu-id="e6e92-189">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="e6e92-190">用於簽署的[認證](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-190">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="e6e92-191">使用者可能要求存取的[身分識別和 API 資源](https://identityserver4.readthedocs.io/en/latest/topics/resources.html)：</span><span class="sxs-lookup"><span data-stu-id="e6e92-191">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="e6e92-192">代表使用者可透過存取權杖存取之受保護資料或功能的 API 資源。</span><span class="sxs-lookup"><span data-stu-id="e6e92-192">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="e6e92-193">API 資源的一個範例是需要授權的 Web API (或一組 API)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-193">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="e6e92-194">代表資訊 (宣告) 的資源，這些資訊 (宣告) 已提供給用戶端來識別使用者。</span><span class="sxs-lookup"><span data-stu-id="e6e92-194">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="e6e92-195">宣告可能包含使用者名稱、電子郵件地址等等。</span><span class="sxs-lookup"><span data-stu-id="e6e92-195">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="e6e92-196">將連線以要求權杖的[用戶端](https://identityserver4.readthedocs.io/en/latest/topics/clients.html)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-196">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="e6e92-197">使用者資訊的儲存機制，例如 [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) 或替代方案。</span><span class="sxs-lookup"><span data-stu-id="e6e92-197">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="e6e92-198">當您指定要讓 IdentityServer4 使用的用戶端和資源時，您可以將適當類型的 <xref:System.Collections.Generic.IEnumerable%601> 集合傳遞至接受記憶體內部用戶端或資源存放區的方法。</span><span class="sxs-lookup"><span data-stu-id="e6e92-198">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="e6e92-199">在更複雜的情況下，您可能會透過相依性插入提供用戶端或資源提供者類型。</span><span class="sxs-lookup"><span data-stu-id="e6e92-199">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="e6e92-200">讓 IdentityServer4 使用自訂 IClientStore 類型所提供之記憶體內部資源和用戶端的範例設定可能如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e6e92-200">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

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

### <a name="consume-security-tokens"></a><span data-ttu-id="e6e92-201">取用安全性權杖</span><span class="sxs-lookup"><span data-stu-id="e6e92-201">Consume security tokens</span></span>

<span data-ttu-id="e6e92-202">對 OpenID Connect 端點進行驗證或發行您自己的安全性權杖涵蓋一些案例。</span><span class="sxs-lookup"><span data-stu-id="e6e92-202">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="e6e92-203">但如果服務只需要將存取權限制給具有其他服務所提供之有效安全性權杖的使用者，又如何？</span><span class="sxs-lookup"><span data-stu-id="e6e92-203">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="e6e92-204">在該案例中，會在 **JwtBearer** 套件中提供處理 JWT 權杖的驗證中介軟體。</span><span class="sxs-lookup"><span data-stu-id="e6e92-204">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="e6e92-205">JWT 代表 "[JSON Web Token](https://tools.ietf.org/html/rfc7519)"，這是用於傳達安全性宣告的常見安全性權杖格式 (由 RFC 7519 定義)。</span><span class="sxs-lookup"><span data-stu-id="e6e92-205">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="e6e92-206">使用中介軟體來取用該等權杖的簡例看起來就像此程式碼片段，取自 eShopOnContainers 的 Ordering.Api 微服務。</span><span class="sxs-lookup"><span data-stu-id="e6e92-206">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="e6e92-207">此用法的參數如下：</span><span class="sxs-lookup"><span data-stu-id="e6e92-207">The parameters in this usage are:</span></span>

- <span data-ttu-id="e6e92-208">`Audience` 代表權杖授與存取權之傳入權杖或資源的接收者。</span><span class="sxs-lookup"><span data-stu-id="e6e92-208">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="e6e92-209">如果此參數中指定的值不符合權杖中的參數，則會拒絕此權杖。</span><span class="sxs-lookup"><span data-stu-id="e6e92-209">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="e6e92-210">`Authority` 是發行權杖之驗證伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="e6e92-210">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="e6e92-211">JWT 持有人驗證中介軟體使用此 URI 來取得公開金鑰，以用來驗證權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="e6e92-211">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="e6e92-212">中介軟體也會確認權杖中的 `iss` 參數符合此 URI。</span><span class="sxs-lookup"><span data-stu-id="e6e92-212">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="e6e92-213">另一個參數 `RequireHttpsMetadata`；您可以將此參數設定為 false，以便在沒有憑證的環境中進行測試。</span><span class="sxs-lookup"><span data-stu-id="e6e92-213">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="e6e92-214">在真實世界部署中，JWT 持有人權杖一律只能透過 HTTPS 傳遞。</span><span class="sxs-lookup"><span data-stu-id="e6e92-214">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="e6e92-215">準備好此中介軟體之後，就會從授權標頭自動擷取 JWT 權杖。</span><span class="sxs-lookup"><span data-stu-id="e6e92-215">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="e6e92-216">這些權杖會接著還原序列化、驗證 (使用 `Audience` 和 `Authority` 參數中的值) 並儲存為使用者資訊，以供 MVC 動作或授權篩選稍後參考。</span><span class="sxs-lookup"><span data-stu-id="e6e92-216">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="e6e92-217">JWT 持有人驗證中介軟體也可以支援更進階的案例；例如，在沒有授權單位的情況下，使用本機憑證來驗證權杖。</span><span class="sxs-lookup"><span data-stu-id="e6e92-217">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="e6e92-218">在此案例中，您可以在 `JwtBearerOptions`物件中指定 `TokenValidationParameters` 物件。</span><span class="sxs-lookup"><span data-stu-id="e6e92-218">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e6e92-219">其他資源</span><span class="sxs-lookup"><span data-stu-id="e6e92-219">Additional resources</span></span>

- <span data-ttu-id="e6e92-220">**在應用程式之間共用 cookie** </span><span class="sxs-lookup"><span data-stu-id="e6e92-220">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="e6e92-221">**身分識別簡介** </span><span class="sxs-lookup"><span data-stu-id="e6e92-221">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="e6e92-222">**Rick Anderson。使用 SMS 的雙因素驗證** </span><span class="sxs-lookup"><span data-stu-id="e6e92-222">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="e6e92-223">**使用 Facebook、Google 和其他外部提供者啟用驗證** </span><span class="sxs-lookup"><span data-stu-id="e6e92-223">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="e6e92-224">**Michell Anicas。OAuth 2 簡介** </span><span class="sxs-lookup"><span data-stu-id="e6e92-224">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="e6e92-225">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth 提供者的 GitHub 存放庫) </span><span class="sxs-lookup"><span data-stu-id="e6e92-225">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="e6e92-226">**IdentityServer4.官方檔** </span><span class="sxs-lookup"><span data-stu-id="e6e92-226">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="e6e92-227">[上一個](../implement-resilient-applications/monitor-app-health.md) 
>[下一步](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="e6e92-227">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
