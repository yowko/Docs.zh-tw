---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032327"
---
### <a name="authentication-google-deprecated-and-replaced"></a>驗證： Google + 已淘汰和已取代

Google 即將開始 [關閉](https://developers.google.com/+/api-shutdown) google + 登入應用程式，其方式早于2019年1月28日。

#### <a name="change-description"></a>變更描述

ASP.NET 4.x 和 ASP.NET Core 已使用 Google + 登入 Api 在 web apps 中驗證 Google 帳戶使用者。 受影響的 NuGet 套件[是適用于](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)ASP.NET Core 的 google 和適用于 ASP.NET WEB FORMS 和 MVC 的[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) google。 `Microsoft.Owin`

Google 的取代 Api 使用不同的資料來源和格式。 以下提供的緩和措施和解決方案會說明結構變更。 應用程式應該確認資料本身仍符合其需求。 例如，名稱、電子郵件地址、設定檔連結和設定檔相片可以提供比之前更細微的不同值。

#### <a name="version-introduced"></a>引進的版本

所有版本。 這項變更是 ASP.NET Core 外部。

#### <a name="recommended-action"></a>建議的動作

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>使用 ASP.NET Web Forms 和 MVC 的 Owin

在 `Microsoft.Owin` 3.1.0 和更新版本中，會在 [此](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)概述暫時的緩和措施。 應用程式應該透過緩和措施完成測試，以檢查資料格式的變更。 有計劃發行 `Microsoft.Owin` 4.0.1 與修正程式。 使用任何先前版本的應用程式應該會更新為版本4.0.1。

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

[ASP.NET Web Forms 和 MVC 的 Owin](#owin-with-aspnet-web-forms-and-mvc)緩和可以調整為 ASP.NET Core 1.x。 因為1.x 已達到 [生命週期的結束](https://dotnet.microsoft.com/platform/support-policy) 狀態，所以不會規劃 NuGet 套件修補程式。

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2.x

針對 2.x `Microsoft.AspNetCore.Authentication.Google` 版，請 `AddGoogle` 使用下列程式碼取代中的現有呼叫 `Startup.ConfigureServices` ：

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

2.1 年2月和2.2 修補程式將先前的重新設定併入新的預設值。 尚未規劃 ASP.NET Core 2.0 的修補程式，因為已達 [生命週期結束](https://dotnet.microsoft.com/platform/support-policy)。

##### <a name="aspnet-core-30"></a>ASP.NET Core 3。0

針對 ASP.NET Core 2.x 提供的緩和也可用於 ASP.NET Core 3.0。 在未來的3.0 預覽版中， `Microsoft.AspNetCore.Authentication.Google` 可能會移除套件。 相反地，會將使用者導向 `Microsoft.AspNetCore.Authentication.OpenIdConnect` 。 下列程式碼示範如何以 `AddGoogle` 中的 `AddOpenIdConnect` 取代 `Startup.ConfigureServices` 。 這種取代可搭配 ASP.NET Core 2.0 和更新版本使用，並可在需要時針對 ASP.NET Core 1.x 進行調整。

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

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
