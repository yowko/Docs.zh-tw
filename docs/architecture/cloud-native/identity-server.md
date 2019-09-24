---
title: 雲端原生應用程式的 IdentityServer
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: 6217f6093d8dc9df6ab058ebdbf99197752aee0c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214019"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="fc137-103">雲端原生應用程式的 IdentityServer</span><span class="sxs-lookup"><span data-stu-id="fc137-103">IdentityServer for cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fc137-104">IdentityServer 是一種開放原始碼驗證服務器，可執行 ASP.NET Core 的 OpenID Connect （OIDC）和 OAuth 2.0 標準。</span><span class="sxs-lookup"><span data-stu-id="fc137-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="fc137-105">其設計目的是要提供一種常見的方式來驗證所有應用程式的要求，不論它們是 web、原生、行動或 API 端點。</span><span class="sxs-lookup"><span data-stu-id="fc137-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="fc137-106">IdentityServer 可以用來為多個應用程式和應用程式類型執行單一登入（SSO）。</span><span class="sxs-lookup"><span data-stu-id="fc137-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="fc137-107">它可用來透過登入表單和類似的使用者介面來驗證實際的使用者，以及通常牽涉到不需要任何使用者介面之權杖發行、驗證和更新的服務型驗證。</span><span class="sxs-lookup"><span data-stu-id="fc137-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="fc137-108">IdentityServer 是設計成可自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="fc137-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="fc137-109">每個實例通常會自訂，以符合個別組織及/或一組應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="fc137-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="fc137-110">一般 web 應用程式案例</span><span class="sxs-lookup"><span data-stu-id="fc137-110">Common web app scenarios</span></span>

<span data-ttu-id="fc137-111">通常，應用程式必須支援下列部分或所有案例：</span><span class="sxs-lookup"><span data-stu-id="fc137-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="fc137-112">人類使用者使用瀏覽器存取 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc137-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="fc137-113">使用者從瀏覽器型應用程式存取後端 Web Api 的人。</span><span class="sxs-lookup"><span data-stu-id="fc137-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="fc137-114">行動/原生用戶端上的人為存取後端 Web Api 的使用者。</span><span class="sxs-lookup"><span data-stu-id="fc137-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="fc137-115">存取後端 Web Api 的其他應用程式（不含作用中的使用者或使用者介面）。</span><span class="sxs-lookup"><span data-stu-id="fc137-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="fc137-116">任何應用程式都可能需要使用自己的身分識別來與其他 Web Api 互動，或委派給使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="fc137-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

<span data-ttu-id="fc137-117">![應用程式類型和](./media/application-types.png)
案例**圖 8-1**。</span><span class="sxs-lookup"><span data-stu-id="fc137-117">![Application types and scenarios](./media/application-types.png)
**Figure 8-1**.</span></span> <span data-ttu-id="fc137-118">應用程式類型和案例。</span><span class="sxs-lookup"><span data-stu-id="fc137-118">Application types and scenarios.</span></span>

<span data-ttu-id="fc137-119">在上述每個案例中，所公開的功能必須受到保護，以避免未經授權的使用。</span><span class="sxs-lookup"><span data-stu-id="fc137-119">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="fc137-120">至少，這通常需要驗證對資源提出要求的使用者或主體。</span><span class="sxs-lookup"><span data-stu-id="fc137-120">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="fc137-121">這項驗證可能會使用其中一個常見的通訊協定，例如 SAML2p、WS-送出或 OpenID Connect。</span><span class="sxs-lookup"><span data-stu-id="fc137-121">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="fc137-122">與 Api 通訊通常會使用 OAuth2 通訊協定和其對安全性權杖的支援。</span><span class="sxs-lookup"><span data-stu-id="fc137-122">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="fc137-123">將這些重要的跨領域安全性考慮和其執行詳細資料，從應用程式本身來確保一致性並改善了安全性與維護性。</span><span class="sxs-lookup"><span data-stu-id="fc137-123">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="fc137-124">將這些考慮外包給專用的產品（例如 IdentityServer），可協助每個應用程式自行解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="fc137-124">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="fc137-125">IdentityServer 提供在 ASP.NET Core 應用程式中執行的中介軟體，並新增 OpenID Connect 和 OAuth2 的支援（請參閱[支援的規格](http://docs.identityserver.io/en/latest/intro/specs.html)）。</span><span class="sxs-lookup"><span data-stu-id="fc137-125">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](http://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="fc137-126">組織會使用 IdentityServer 中介軟體來建立自己的 ASP.NET Core 應用程式，以做為其所有權杖型安全性通訊協定的 STS。</span><span class="sxs-lookup"><span data-stu-id="fc137-126">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="fc137-127">IdentityServer 中介軟體會公開端點以支援標準功能，包括：</span><span class="sxs-lookup"><span data-stu-id="fc137-127">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="fc137-128">授權（驗證終端使用者）</span><span class="sxs-lookup"><span data-stu-id="fc137-128">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="fc137-129">Token （以程式設計方式要求權杖）</span><span class="sxs-lookup"><span data-stu-id="fc137-129">Token (request a token programmatically)</span></span>
- <span data-ttu-id="fc137-130">探索（關於伺服器的中繼資料）</span><span class="sxs-lookup"><span data-stu-id="fc137-130">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="fc137-131">使用者資訊（使用有效的存取權杖取得使用者資訊）</span><span class="sxs-lookup"><span data-stu-id="fc137-131">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="fc137-132">裝置授權（用來啟動裝置流程授權）</span><span class="sxs-lookup"><span data-stu-id="fc137-132">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="fc137-133">自我檢查（權杖驗證）</span><span class="sxs-lookup"><span data-stu-id="fc137-133">Introspection (token validation)</span></span>
- <span data-ttu-id="fc137-134">撤銷（權杖撤銷）</span><span class="sxs-lookup"><span data-stu-id="fc137-134">Revocation (token revocation)</span></span>
- <span data-ttu-id="fc137-135">結束會話（在所有應用程式中觸發單一登出）</span><span class="sxs-lookup"><span data-stu-id="fc137-135">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="fc137-136">使用者入門</span><span class="sxs-lookup"><span data-stu-id="fc137-136">Getting started</span></span>

<span data-ttu-id="fc137-137">IdentityServer4 是開放原始碼且可免費使用。</span><span class="sxs-lookup"><span data-stu-id="fc137-137">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="fc137-138">您可以使用 NuGet 套件，將它新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc137-138">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="fc137-139">主要套件是已下載超過4000000次的[IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) 。</span><span class="sxs-lookup"><span data-stu-id="fc137-139">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="fc137-140">基底套件不包含任何使用者介面程式碼，而且只支援記憶體設定。</span><span class="sxs-lookup"><span data-stu-id="fc137-140">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="fc137-141">若要將它與資料庫搭配使用，您也會想要使用 Entity Framework Core 來儲存 IdentityServer 之設定和運算元據的資料提供者，例如[IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) 。</span><span class="sxs-lookup"><span data-stu-id="fc137-141">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="fc137-142">針對使用者介面，您可以將[檔案從快速入門 UI 存放庫](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI)複製到 ASP.NET Core MVC 應用程式中，以新增使用 IdentityServer 中介軟體進行登入和登出的支援。</span><span class="sxs-lookup"><span data-stu-id="fc137-142">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="fc137-143">設定</span><span class="sxs-lookup"><span data-stu-id="fc137-143">Configuration</span></span>

<span data-ttu-id="fc137-144">IdentityServer 支援不同種類的通訊協定和社交驗證提供者，可設定為每個自訂安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="fc137-144">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="fc137-145">這通常會在`Startup` `ConfigureServices`方法中的 ASP.NET Core 應用程式類別中完成。</span><span class="sxs-lookup"><span data-stu-id="fc137-145">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="fc137-146">設定牽涉到指定支援的通訊協定，以及將使用的伺服器和端點的路徑。</span><span class="sxs-lookup"><span data-stu-id="fc137-146">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="fc137-147">圖8-2 顯示從 IdentityServer4 快速入門 UI 專案取得的範例設定：</span><span class="sxs-lookup"><span data-stu-id="fc137-147">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        
        // some details omitted
        services.AddIdentityServer();
        
          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<inser here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="fc137-148">**圖 8-2**：</span><span class="sxs-lookup"><span data-stu-id="fc137-148">**Figure 8-2**.</span></span> <span data-ttu-id="fc137-149">正在設定 IdentityServer。</span><span class="sxs-lookup"><span data-stu-id="fc137-149">Configuring IdentityServer.</span></span>

<span data-ttu-id="fc137-150">IdentityServer 也會裝載公用示範網站，可用來測試各種通訊協定和設定。</span><span class="sxs-lookup"><span data-stu-id="fc137-150">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="fc137-151">它位於[https://demo.identityserver.io/](https://demo.identityserver.io/) ，並包含如何根據提供的`client_id` 來設定其行為的資訊。</span><span class="sxs-lookup"><span data-stu-id="fc137-151">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="fc137-152">JavaScript 用戶端</span><span class="sxs-lookup"><span data-stu-id="fc137-152">JavaScript clients</span></span>

<span data-ttu-id="fc137-153">許多雲端原生應用程式會利用前端的伺服器端 Api 和豐富型用戶端單頁應用程式（Spa）。</span><span class="sxs-lookup"><span data-stu-id="fc137-153">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="fc137-154">IdentityServer 透過 NPM 提供的[JavaScript 用戶端](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)（`oidc-client.js`）可新增至 spa，讓他們能夠使用 IdentityServer 進行登入、登出，以及 web api 的權杖型驗證。</span><span class="sxs-lookup"><span data-stu-id="fc137-154">IdentityServer ships a [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="fc137-155">reference</span><span class="sxs-lookup"><span data-stu-id="fc137-155">References</span></span>

- [<span data-ttu-id="fc137-156">IdentityServer 檔</span><span class="sxs-lookup"><span data-stu-id="fc137-156">IdentityServer documentation</span></span>](http://docs.identityserver.io/)
- [<span data-ttu-id="fc137-157">應用程式類型</span><span class="sxs-lookup"><span data-stu-id="fc137-157">Application types</span></span>](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [<span data-ttu-id="fc137-158">JavaScript OIDC 用戶端</span><span class="sxs-lookup"><span data-stu-id="fc137-158">JavaScript OIDC client</span></span>](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="fc137-159">[上一頁](azure-active-directory.md)
>[下一頁](security.md)</span><span class="sxs-lookup"><span data-stu-id="fc137-159">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
