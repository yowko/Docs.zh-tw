---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394252"
---
### <a name="authentication-google-deprecated-and-replaced"></a>身份驗證：Google+ 已棄用並更換

谷歌最早于2019年1月28日開始[關閉](https://developers.google.com/+/api-shutdown)谷歌®應用程式登錄。

#### <a name="change-description"></a>變更描述

ASP.NET 4.x 和 ASP.NET Core 一直在使用 Google+ 登錄 API 對 Web 應用中的 Google 帳戶使用者進行身份驗證。 受影響的 NuGet 套裝軟體是[Microsoft.AspNetCore.身份驗證.GoogleASP.NET](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/)核心和[微軟.Owin.Security.Google，](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/)用於`Microsoft.Owin`ASP.NET Web 表單和 MVC。

Google 的替換 API 使用不同的資料來源和格式。 下文提供的緩解措施和解決辦法考慮到了結構變化。 應用應驗證資料本身是否仍滿足其要求。 例如，姓名、電子郵件地址、個人資料連結和個人資料照片可能提供與以前略有不同的值。

#### <a name="version-introduced"></a>介紹的版本

所有版本。 此更改是 ASP.NET 核心的外部更改。

#### <a name="recommended-action"></a>建議的動作

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>具有ASP.NET Web 表單和 MVC 的 Owin

對於`Microsoft.Owin`3.1.0 及更高版本，[此處](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)概述了臨時緩解。 應用應完成測試，並緩解，以檢查資料格式的更改。 有計劃發佈`Microsoft.Owin`4.0.1 與修復. 使用任何先前版本的應用應更新到版本 4.0.1。

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

[Owin 中帶有ASP.NET Web 表單和 MVC](#owin-with-aspnet-web-forms-and-mvc)的緩解可以適應ASP.NET Core 1.x。 NuGet 包修補程式未計畫，因為 1.x 已達到[生命週期結束](https://dotnet.microsoft.com/platform/support-policy)狀態。

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2.x

對於`Microsoft.AspNetCore.Authentication.Google`版本 2.x，用以下代碼替換`AddGoogle`您`Startup.ConfigureServices`現有的對 中的調用：

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

2 月 2.1 和 2.2 修補程式將前面的重新配置合併為新預設值。 沒有補丁計畫ASP.NET核心2.0，因為它已經達到了[壽命結束](https://dotnet.microsoft.com/platform/support-policy)。

##### <a name="aspnet-core-30"></a>ASP.NET核心 3.0

為ASP.NET Core 2.x 提供的緩解也可用於ASP.NET核心 3.0。 在將來的 3.0 預覽`Microsoft.AspNetCore.Authentication.Google`中，可能會刪除包。 使用者將被定向到`Microsoft.AspNetCore.Authentication.OpenIdConnect`。 以下代碼演示如何替換為`AddGoogle``AddOpenIdConnect`in `Startup.ConfigureServices`。 此替換可用於ASP.NET酷睿 2.0 及更高版本，並可根據需要ASP.NET核心 1.x 進行調整。

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
