---
ms.openlocfilehash: 14d80f25c34465caa6dec10e5704fe0a3cbccc71
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478518"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="83bc4-101">驗證： Google + 已淘汰和已取代</span><span class="sxs-lookup"><span data-stu-id="83bc4-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="83bc4-102">Google 即將開始 [關閉](https://developers.google.com/+/api-shutdown) google + 登入應用程式，其方式早于2019年1月28日。</span><span class="sxs-lookup"><span data-stu-id="83bc4-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83bc4-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="83bc4-103">Change description</span></span>

<span data-ttu-id="83bc4-104">ASP.NET 4.x 和 ASP.NET Core 已使用 Google + 登入 Api 在 web apps 中驗證 Google 帳戶使用者。</span><span class="sxs-lookup"><span data-stu-id="83bc4-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="83bc4-105">受影響的 NuGet 套件[是適用于](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)ASP.NET Core 的 google 和適用于 ASP.NET WEB FORMS 和 MVC 的[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) google。 `Microsoft.Owin`</span><span class="sxs-lookup"><span data-stu-id="83bc4-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="83bc4-106">Google 的取代 Api 使用不同的資料來源和格式。</span><span class="sxs-lookup"><span data-stu-id="83bc4-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="83bc4-107">以下提供的緩和措施和解決方案會說明結構變更。</span><span class="sxs-lookup"><span data-stu-id="83bc4-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="83bc4-108">應用程式應該確認資料本身仍符合其需求。</span><span class="sxs-lookup"><span data-stu-id="83bc4-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="83bc4-109">例如，名稱、電子郵件地址、設定檔連結和設定檔相片可以提供比之前更細微的不同值。</span><span class="sxs-lookup"><span data-stu-id="83bc4-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83bc4-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="83bc4-110">Version introduced</span></span>

<span data-ttu-id="83bc4-111">所有版本。</span><span class="sxs-lookup"><span data-stu-id="83bc4-111">All versions.</span></span> <span data-ttu-id="83bc4-112">這項變更是 ASP.NET Core 外部。</span><span class="sxs-lookup"><span data-stu-id="83bc4-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83bc4-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="83bc4-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="83bc4-114">使用 ASP.NET Web Forms 和 MVC 的 Owin</span><span class="sxs-lookup"><span data-stu-id="83bc4-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="83bc4-115">在 `Microsoft.Owin` 3.1.0 和更新版本中，會在 [此](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)概述暫時的緩和措施。</span><span class="sxs-lookup"><span data-stu-id="83bc4-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="83bc4-116">應用程式應該透過緩和措施完成測試，以檢查資料格式的變更。</span><span class="sxs-lookup"><span data-stu-id="83bc4-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="83bc4-117">有計劃發行 `Microsoft.Owin` 4.0.1 與修正程式。</span><span class="sxs-lookup"><span data-stu-id="83bc4-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="83bc4-118">使用任何先前版本的應用程式應該會更新為版本4.0.1。</span><span class="sxs-lookup"><span data-stu-id="83bc4-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="83bc4-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="83bc4-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="83bc4-120">[ASP.NET Web Forms 和 MVC 的 Owin](#owin-with-aspnet-web-forms-and-mvc)緩和可以調整為 ASP.NET Core 1.x。</span><span class="sxs-lookup"><span data-stu-id="83bc4-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="83bc4-121">因為1.x 已達到 [生命週期的結束](https://dotnet.microsoft.com/platform/support-policy) 狀態，所以不會規劃 NuGet 套件修補程式。</span><span class="sxs-lookup"><span data-stu-id="83bc4-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="83bc4-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="83bc4-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="83bc4-123">針對 2.x `Microsoft.AspNetCore.Authentication.Google` 版，請 `AddGoogle` 使用下列程式碼取代中的現有呼叫 `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="83bc4-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

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

<span data-ttu-id="83bc4-124">2.1 年2月和2.2 修補程式將先前的重新設定併入新的預設值。</span><span class="sxs-lookup"><span data-stu-id="83bc4-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="83bc4-125">尚未規劃 ASP.NET Core 2.0 的修補程式，因為已達 [生命週期結束](https://dotnet.microsoft.com/platform/support-policy)。</span><span class="sxs-lookup"><span data-stu-id="83bc4-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="83bc4-126">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="83bc4-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="83bc4-127">針對 ASP.NET Core 2.x 提供的緩和也可用於 ASP.NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="83bc4-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="83bc4-128">在未來的3.0 預覽版中， `Microsoft.AspNetCore.Authentication.Google` 可能會移除套件。</span><span class="sxs-lookup"><span data-stu-id="83bc4-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="83bc4-129">相反地，會將使用者導向 `Microsoft.AspNetCore.Authentication.OpenIdConnect` 。</span><span class="sxs-lookup"><span data-stu-id="83bc4-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="83bc4-130">下列程式碼示範如何以 `AddGoogle` 中的 `AddOpenIdConnect` 取代 `Startup.ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="83bc4-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="83bc4-131">這種取代可搭配 ASP.NET Core 2.0 和更新版本使用，並可在需要時針對 ASP.NET Core 1.x 進行調整。</span><span class="sxs-lookup"><span data-stu-id="83bc4-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/signin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="83bc4-132">類別</span><span class="sxs-lookup"><span data-stu-id="83bc4-132">Category</span></span>

<span data-ttu-id="83bc4-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="83bc4-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83bc4-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="83bc4-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
