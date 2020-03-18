---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394252"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="0569c-101">身份驗證：Google+ 已棄用並更換</span><span class="sxs-lookup"><span data-stu-id="0569c-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="0569c-102">谷歌最早于2019年1月28日開始[關閉](https://developers.google.com/+/api-shutdown)谷歌®應用程式登錄。</span><span class="sxs-lookup"><span data-stu-id="0569c-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0569c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0569c-103">Change description</span></span>

<span data-ttu-id="0569c-104">ASP.NET 4.x 和 ASP.NET Core 一直在使用 Google+ 登錄 API 對 Web 應用中的 Google 帳戶使用者進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="0569c-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="0569c-105">受影響的 NuGet 套裝軟體是[Microsoft.AspNetCore.身份驗證.GoogleASP.NET](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/)核心和[微軟.Owin.Security.Google，](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)用於`Microsoft.Owin`ASP.NET Web 表單和 MVC。</span><span class="sxs-lookup"><span data-stu-id="0569c-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="0569c-106">Google 的替換 API 使用不同的資料來源和格式。</span><span class="sxs-lookup"><span data-stu-id="0569c-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="0569c-107">下文提供的緩解措施和解決辦法考慮到了結構變化。</span><span class="sxs-lookup"><span data-stu-id="0569c-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="0569c-108">應用應驗證資料本身是否仍滿足其要求。</span><span class="sxs-lookup"><span data-stu-id="0569c-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="0569c-109">例如，姓名、電子郵件地址、個人資料連結和個人資料照片可能提供與以前略有不同的值。</span><span class="sxs-lookup"><span data-stu-id="0569c-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0569c-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="0569c-110">Version introduced</span></span>

<span data-ttu-id="0569c-111">所有版本。</span><span class="sxs-lookup"><span data-stu-id="0569c-111">All versions.</span></span> <span data-ttu-id="0569c-112">此更改是 ASP.NET 核心的外部更改。</span><span class="sxs-lookup"><span data-stu-id="0569c-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0569c-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0569c-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="0569c-114">具有ASP.NET Web 表單和 MVC 的 Owin</span><span class="sxs-lookup"><span data-stu-id="0569c-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="0569c-115">對於`Microsoft.Owin`3.1.0 及更高版本，[此處](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)概述了臨時緩解。</span><span class="sxs-lookup"><span data-stu-id="0569c-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="0569c-116">應用應完成測試，並緩解，以檢查資料格式的更改。</span><span class="sxs-lookup"><span data-stu-id="0569c-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="0569c-117">有計劃發佈`Microsoft.Owin`4.0.1 與修復.</span><span class="sxs-lookup"><span data-stu-id="0569c-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="0569c-118">使用任何先前版本的應用應更新到版本 4.0.1。</span><span class="sxs-lookup"><span data-stu-id="0569c-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="0569c-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0569c-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="0569c-120">[Owin 中帶有ASP.NET Web 表單和 MVC](#owin-with-aspnet-web-forms-and-mvc)的緩解可以適應ASP.NET Core 1.x。</span><span class="sxs-lookup"><span data-stu-id="0569c-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="0569c-121">NuGet 包修補程式未計畫，因為 1.x 已達到[生命週期結束](https://dotnet.microsoft.com/platform/support-policy)狀態。</span><span class="sxs-lookup"><span data-stu-id="0569c-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="0569c-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0569c-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="0569c-123">對於`Microsoft.AspNetCore.Authentication.Google`版本 2.x，用以下代碼替換`AddGoogle`您`Startup.ConfigureServices`現有的對 中的調用：</span><span class="sxs-lookup"><span data-stu-id="0569c-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

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

<span data-ttu-id="0569c-124">2 月 2.1 和 2.2 修補程式將前面的重新配置合併為新預設值。</span><span class="sxs-lookup"><span data-stu-id="0569c-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="0569c-125">沒有補丁計畫ASP.NET核心2.0，因為它已經達到了[壽命結束](https://dotnet.microsoft.com/platform/support-policy)。</span><span class="sxs-lookup"><span data-stu-id="0569c-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="0569c-126">ASP.NET核心 3.0</span><span class="sxs-lookup"><span data-stu-id="0569c-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="0569c-127">為ASP.NET Core 2.x 提供的緩解也可用於ASP.NET核心 3.0。</span><span class="sxs-lookup"><span data-stu-id="0569c-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="0569c-128">在將來的 3.0 預覽`Microsoft.AspNetCore.Authentication.Google`中，可能會刪除包。</span><span class="sxs-lookup"><span data-stu-id="0569c-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="0569c-129">使用者將被定向到`Microsoft.AspNetCore.Authentication.OpenIdConnect`。</span><span class="sxs-lookup"><span data-stu-id="0569c-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="0569c-130">以下代碼演示如何替換為`AddGoogle``AddOpenIdConnect`in `Startup.ConfigureServices`。</span><span class="sxs-lookup"><span data-stu-id="0569c-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="0569c-131">此替換可用於ASP.NET酷睿 2.0 及更高版本，並可根據需要ASP.NET核心 1.x 進行調整。</span><span class="sxs-lookup"><span data-stu-id="0569c-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

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

#### <a name="category"></a><span data-ttu-id="0569c-132">類別</span><span class="sxs-lookup"><span data-stu-id="0569c-132">Category</span></span>

<span data-ttu-id="0569c-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0569c-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0569c-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0569c-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
