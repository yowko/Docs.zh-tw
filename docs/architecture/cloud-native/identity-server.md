---
title: 適用于雲端原生應用程式的 IdentityServer
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: bdf193aac348b54f2ebf5b537beef5d61a1d5a1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163826"
---
# <a name="identityserver-for-cloud-native-applications"></a>適用于雲端原生應用程式的 IdentityServer

IdentityServer 是一種開放原始碼驗證服務器，可針對 ASP.NET Core 執行 (OIDC) 和 OAuth 2.0 標準的 OpenID Connect。 其設計目的是要提供一種通用方式來驗證所有應用程式的要求，不論這些應用程式是 web、原生、行動或 API 端點。 IdentityServer 可以用來針對多個應用程式和應用程式類型，執行單一登入 (SSO) 。 它可以用來透過登入表單和類似的使用者介面，以及類似的使用者介面和服務型驗證（通常牽涉到權杖發行、驗證和續約，而不需要任何使用者介面）來驗證實際的使用者。 IdentityServer 是設計為可自訂的解決方案。 每個實例通常會自訂，以符合個別組織及/或應用程式需求的組合。

## <a name="common-web-app-scenarios"></a>常見的 web 應用程式案例

一般來說，應用程式必須支援下列部分或所有案例：

- 使用瀏覽器存取 web 應用程式的人類使用者。
- 以瀏覽器為基礎的應用程式存取後端 Web Api 的使用者。
- 行動/原生用戶端上的使用者存取後端 Web Api。
- 存取後端 Web Api 的其他應用程式 (沒有作用中使用者或使用者介面) 。
- 任何應用程式都可能需要使用自己的身分識別與其他 Web Api 互動，或委派給使用者的身分識別。

![應用程式類型和案例](./media/application-types.png)

**圖 8-1**： 應用程式類型和案例。

在上述每個案例中，公開的功能都必須受到保護，以避免未經授權的使用。 通常，這通常需要驗證提出資源要求的使用者或主體。 這項驗證可以使用數種常見的通訊協定，例如 SAML2p、WS-送出或 OpenID Connect。 與 Api 通訊通常會使用 OAuth2 通訊協定及其對安全性權杖的支援。 從應用程式本身分離這些重要的跨領域安全性考慮和其實作為詳細資料，可確保一致性並改進安全性與維護性。 將這些考慮外包給專用產品（例如 IdentityServer），可協助每個應用程式自行解決這些問題。

IdentityServer 提供在 ASP.NET Core 應用程式內執行的中介軟體，並新增 OpenID Connect 和 OAuth2 的支援 (請參閱 [支援的規格](https://docs.identityserver.io/en/latest/intro/specs.html)) 。 組織會使用 IdentityServer 中介軟體來建立自己的 ASP.NET Core 應用程式，以作為其所有權杖型安全性通訊協定的 STS。 IdentityServer 中介軟體會公開端點以支援標準功能，包括：

- 授權 (驗證終端使用者) 
- 權杖 (以程式設計方式要求權杖) 
- 探索 (有關伺服器) 的中繼資料
- 使用者資訊 (取得具有有效存取權杖的使用者資訊) 
- 裝置授權 (用來啟動裝置流程授權) 
- 自我檢查 (token 驗證) 
- 撤銷 (權杖撤銷) 
- 結束會話 (在所有應用程式) 觸發單一登出

## <a name="getting-started"></a>開始使用

IdentityServer4 是開放原始碼且可免費使用。 您可以使用 NuGet 套件將它新增至您的應用程式。 主要套件是已下載超過4000000次的 [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) 。 基底套件不包含任何使用者介面程式碼，而且只支援記憶體中的設定。 若要搭配資料庫使用它，您也需要一個資料提供者，例如 [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) ，其使用 Entity Framework Core 儲存 IdentityServer 的設定和運算元據。 針對使用者介面，您可以從 [快速入門 UI 存放庫將檔案](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) 複製到 ASP.NET Core MVC 應用程式，以新增使用 IdentityServer 中介軟體進行登入和登出的支援。

## <a name="configuration"></a>設定

IdentityServer 支援不同類型的通訊協定和社交驗證提供者，可設定為每個自訂安裝的一部分。 這通常是在方法的 ASP.NET Core 應用程式 `Startup` 類別中完成 `ConfigureServices` 。 設定包含指定支援的通訊協定，以及將使用之伺服器和端點的路徑。 圖8-2 顯示取自 IdentityServer4 快速入門 UI 專案的範例設定：

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
                options.ClientSecret = "<insert here>";
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

**圖 8-2**。 正在設定 IdentityServer。

IdentityServer 也會裝載公用示範網站，可用來測試各種通訊協定和設定。 它位於 [https://demo.identityserver.io/](https://demo.identityserver.io/) 並包含如何根據提供的來設定其行為的資訊 `client_id` 。

## <a name="javascript-clients"></a>JavaScript 用戶端

許多雲端原生應用程式都利用伺服器端 Api 和豐富型用戶端單一頁面應用程式 (Spa) 前端。 IdentityServer 隨附 [JavaScript 用戶端](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via 可新增至 spa 的 NPM，可讓他們使用 IdentityServer 進行登入、登出，以及 web api 的權杖型驗證。

## <a name="references"></a>參考資料

- [IdentityServer 檔](https://docs.identityserver.io/en/latest/)
- [應用程式類型](/azure/active-directory/develop/app-types)
- [JavaScript OIDC 用戶端](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
>[上一個](azure-active-directory.md) 
>[下一步](security.md)
