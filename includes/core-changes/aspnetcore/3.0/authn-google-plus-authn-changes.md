---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394252"
---
### <a name="authentication-google-deprecated-and-replaced"></a>驗證： Google + 已淘汰並已取代

Google 即將開始[關閉](https://developers.google.com/+/api-shutdown)適用于應用程式的 google + 登入，早于2019年1月28日。

#### <a name="change-description"></a>變更描述

ASP.NET 4.x 和 ASP.NET Core 已使用 Google + 登入 Api 來驗證 web apps 中的 Google 帳戶使用者。 受影響的 NuGet 套件為 AspNetCore 的 ASP.NET Core 和[Owin](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)的[google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) ，適用于使用 ASP.NET Web Forms 和 MVC 的 `Microsoft.Owin`。

Google 的更換 Api 會使用不同的資料來源和格式。 以下提供的緩和措施和解決方案會考慮結構變更。 應用程式應該確認資料本身仍然滿足其需求。 例如，名稱、電子郵件地址、設定檔連結和設定檔相片可能會提供比以前更細微的值。

#### <a name="version-introduced"></a>引進的版本

所有版本。 這是 ASP.NET Core 外部變更。

#### <a name="recommended-action"></a>建議的動作

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>使用 ASP.NET Web Forms 和 MVC 的 Owin

針對 `Microsoft.Owin` 3.1.0 和更新版本，[這裡](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)會概述暫時的緩和措施。 應用程式應該使用緩和措施來完成測試，以檢查資料格式是否有變更。 有計劃可以發行 `Microsoft.Owin` 4.0.1 與修正程式。 使用任何先前版本的應用程式應該更新為版本4.0.1。

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1。x

[使用 ASP.NET Web Forms 和 MVC Owin](#owin-with-aspnet-web-forms-and-mvc)的緩和措施可以調整為 ASP.NET Core 1.x。 因為1.x 已達到[生命週期的結束](https://dotnet.microsoft.com/platform/support-policy)狀態，所以不會規劃 NuGet 套件修補程式。

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2。x

若為 `Microsoft.AspNetCore.Authentication.Google` 2.x 版，請使用下列程式碼，將您現有的呼叫取代為 `Startup.ConfigureServices` 中的 `AddGoogle`：

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

2\.1 年2月和2.2 修補程式併入了先前的重新設定，做為新的預設值。 因為已達到[生命週期的結尾](https://dotnet.microsoft.com/platform/support-policy)，所以未規劃 ASP.NET Core 2.0 的修補程式。

##### <a name="aspnet-core-30"></a>ASP.NET Core 3。0

針對 ASP.NET Core 2.x 所提供的緩和也可以用於 ASP.NET Core 3.0。 在未來的3.0 預覽中，可能會移除 `Microsoft.AspNetCore.Authentication.Google` 套件。 使用者會改為導向至 `Microsoft.AspNetCore.Authentication.OpenIdConnect`。 下列程式碼示範如何在 `Startup.ConfigureServices` 中以 `AddOpenIdConnect` 取代 `AddGoogle`。 這種取代可以搭配 ASP.NET Core 2.0 和更新版本使用，而且可以視需要針對 ASP.NET Core 1.x 進行調整。

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

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
