---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394252"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="c725f-101">驗證： Google + 已淘汰並已取代</span><span class="sxs-lookup"><span data-stu-id="c725f-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="c725f-102">Google 即將開始[關閉](https://developers.google.com/+/api-shutdown)適用于應用程式的 google + 登入，早于2019年1月28日。</span><span class="sxs-lookup"><span data-stu-id="c725f-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c725f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="c725f-103">Change description</span></span>

<span data-ttu-id="c725f-104">ASP.NET 4.x 和 ASP.NET Core 已使用 Google + 登入 Api 來驗證 web apps 中的 Google 帳戶使用者。</span><span class="sxs-lookup"><span data-stu-id="c725f-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="c725f-105">受影響的 NuGet 套件為 AspNetCore 的 ASP.NET Core 和[Owin](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)的[google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) ，適用于使用 ASP.NET Web Forms 和 MVC 的 `Microsoft.Owin`。</span><span class="sxs-lookup"><span data-stu-id="c725f-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="c725f-106">Google 的更換 Api 會使用不同的資料來源和格式。</span><span class="sxs-lookup"><span data-stu-id="c725f-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="c725f-107">以下提供的緩和措施和解決方案會考慮結構變更。</span><span class="sxs-lookup"><span data-stu-id="c725f-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="c725f-108">應用程式應該確認資料本身仍然滿足其需求。</span><span class="sxs-lookup"><span data-stu-id="c725f-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="c725f-109">例如，名稱、電子郵件地址、設定檔連結和設定檔相片可能會提供比以前更細微的值。</span><span class="sxs-lookup"><span data-stu-id="c725f-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c725f-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c725f-110">Version introduced</span></span>

<span data-ttu-id="c725f-111">所有版本。</span><span class="sxs-lookup"><span data-stu-id="c725f-111">All versions.</span></span> <span data-ttu-id="c725f-112">這是 ASP.NET Core 外部變更。</span><span class="sxs-lookup"><span data-stu-id="c725f-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c725f-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c725f-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="c725f-114">使用 ASP.NET Web Forms 和 MVC 的 Owin</span><span class="sxs-lookup"><span data-stu-id="c725f-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="c725f-115">針對 `Microsoft.Owin` 3.1.0 和更新版本，[這裡](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)會概述暫時的緩和措施。</span><span class="sxs-lookup"><span data-stu-id="c725f-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="c725f-116">應用程式應該使用緩和措施來完成測試，以檢查資料格式是否有變更。</span><span class="sxs-lookup"><span data-stu-id="c725f-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="c725f-117">有計劃可以發行 `Microsoft.Owin` 4.0.1 與修正程式。</span><span class="sxs-lookup"><span data-stu-id="c725f-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="c725f-118">使用任何先前版本的應用程式應該更新為版本4.0.1。</span><span class="sxs-lookup"><span data-stu-id="c725f-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="c725f-119">ASP.NET Core 1。x</span><span class="sxs-lookup"><span data-stu-id="c725f-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="c725f-120">[使用 ASP.NET Web Forms 和 MVC Owin](#owin-with-aspnet-web-forms-and-mvc)的緩和措施可以調整為 ASP.NET Core 1.x。</span><span class="sxs-lookup"><span data-stu-id="c725f-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="c725f-121">因為1.x 已達到[生命週期的結束](https://dotnet.microsoft.com/platform/support-policy)狀態，所以不會規劃 NuGet 套件修補程式。</span><span class="sxs-lookup"><span data-stu-id="c725f-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="c725f-122">ASP.NET Core 2。x</span><span class="sxs-lookup"><span data-stu-id="c725f-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="c725f-123">若為 `Microsoft.AspNetCore.Authentication.Google` 2.x 版，請使用下列程式碼，將您現有的呼叫取代為 `Startup.ConfigureServices` 中的 `AddGoogle`：</span><span class="sxs-lookup"><span data-stu-id="c725f-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="c725f-124">2\.1 年2月和2.2 修補程式併入了先前的重新設定，做為新的預設值。</span><span class="sxs-lookup"><span data-stu-id="c725f-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="c725f-125">因為已達到[生命週期的結尾](https://dotnet.microsoft.com/platform/support-policy)，所以未規劃 ASP.NET Core 2.0 的修補程式。</span><span class="sxs-lookup"><span data-stu-id="c725f-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="c725f-126">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="c725f-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="c725f-127">針對 ASP.NET Core 2.x 所提供的緩和也可以用於 ASP.NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="c725f-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="c725f-128">在未來的3.0 預覽中，可能會移除 `Microsoft.AspNetCore.Authentication.Google` 套件。</span><span class="sxs-lookup"><span data-stu-id="c725f-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="c725f-129">使用者會改為導向至 `Microsoft.AspNetCore.Authentication.OpenIdConnect`。</span><span class="sxs-lookup"><span data-stu-id="c725f-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="c725f-130">下列程式碼示範如何在 `Startup.ConfigureServices` 中以 `AddOpenIdConnect` 取代 `AddGoogle`。</span><span class="sxs-lookup"><span data-stu-id="c725f-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="c725f-131">這種取代可以搭配 ASP.NET Core 2.0 和更新版本使用，而且可以視需要針對 ASP.NET Core 1.x 進行調整。</span><span class="sxs-lookup"><span data-stu-id="c725f-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="c725f-132">分類</span><span class="sxs-lookup"><span data-stu-id="c725f-132">Category</span></span>

<span data-ttu-id="c725f-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c725f-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c725f-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c725f-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
