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
# <a name="identityserver-for-cloud-native-applications"></a>雲端原生應用程式的 IdentityServer

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

IdentityServer 是一種開放原始碼驗證服務器，可執行 ASP.NET Core 的 OpenID Connect （OIDC）和 OAuth 2.0 標準。 其設計目的是要提供一種常見的方式來驗證所有應用程式的要求，不論它們是 web、原生、行動或 API 端點。 IdentityServer 可以用來為多個應用程式和應用程式類型執行單一登入（SSO）。 它可用來透過登入表單和類似的使用者介面來驗證實際的使用者，以及通常牽涉到不需要任何使用者介面之權杖發行、驗證和更新的服務型驗證。 IdentityServer 是設計成可自訂的解決方案。 每個實例通常會自訂，以符合個別組織及/或一組應用程式的需求。

## <a name="common-web-app-scenarios"></a>一般 web 應用程式案例

通常，應用程式必須支援下列部分或所有案例：

- 人類使用者使用瀏覽器存取 web 應用程式。
- 使用者從瀏覽器型應用程式存取後端 Web Api 的人。
- 行動/原生用戶端上的人為存取後端 Web Api 的使用者。
- 存取後端 Web Api 的其他應用程式（不含作用中的使用者或使用者介面）。
- 任何應用程式都可能需要使用自己的身分識別來與其他 Web Api 互動，或委派給使用者的身分識別。

![應用程式類型和](./media/application-types.png)
案例**圖 8-1**。 應用程式類型和案例。

在上述每個案例中，所公開的功能必須受到保護，以避免未經授權的使用。 至少，這通常需要驗證對資源提出要求的使用者或主體。 這項驗證可能會使用其中一個常見的通訊協定，例如 SAML2p、WS-送出或 OpenID Connect。 與 Api 通訊通常會使用 OAuth2 通訊協定和其對安全性權杖的支援。 將這些重要的跨領域安全性考慮和其執行詳細資料，從應用程式本身來確保一致性並改善了安全性與維護性。 將這些考慮外包給專用的產品（例如 IdentityServer），可協助每個應用程式自行解決這些問題。

IdentityServer 提供在 ASP.NET Core 應用程式中執行的中介軟體，並新增 OpenID Connect 和 OAuth2 的支援（請參閱[支援的規格](http://docs.identityserver.io/en/latest/intro/specs.html)）。 組織會使用 IdentityServer 中介軟體來建立自己的 ASP.NET Core 應用程式，以做為其所有權杖型安全性通訊協定的 STS。 IdentityServer 中介軟體會公開端點以支援標準功能，包括：

- 授權（驗證終端使用者）
- Token （以程式設計方式要求權杖）
- 探索（關於伺服器的中繼資料）
- 使用者資訊（使用有效的存取權杖取得使用者資訊）
- 裝置授權（用來啟動裝置流程授權）
- 自我檢查（權杖驗證）
- 撤銷（權杖撤銷）
- 結束會話（在所有應用程式中觸發單一登出）

## <a name="getting-started"></a>使用者入門

IdentityServer4 是開放原始碼且可免費使用。 您可以使用 NuGet 套件，將它新增至您的應用程式。 主要套件是已下載超過4000000次的[IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) 。 基底套件不包含任何使用者介面程式碼，而且只支援記憶體設定。 若要將它與資料庫搭配使用，您也會想要使用 Entity Framework Core 來儲存 IdentityServer 之設定和運算元據的資料提供者，例如[IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) 。 針對使用者介面，您可以將[檔案從快速入門 UI 存放庫](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI)複製到 ASP.NET Core MVC 應用程式中，以新增使用 IdentityServer 中介軟體進行登入和登出的支援。

## <a name="configuration"></a>設定

IdentityServer 支援不同種類的通訊協定和社交驗證提供者，可設定為每個自訂安裝的一部分。 這通常會在`Startup` `ConfigureServices`方法中的 ASP.NET Core 應用程式類別中完成。 設定牽涉到指定支援的通訊協定，以及將使用的伺服器和端點的路徑。 圖8-2 顯示從 IdentityServer4 快速入門 UI 專案取得的範例設定：

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

**圖 8-2**： 正在設定 IdentityServer。

IdentityServer 也會裝載公用示範網站，可用來測試各種通訊協定和設定。 它位於[https://demo.identityserver.io/](https://demo.identityserver.io/) ，並包含如何根據提供的`client_id` 來設定其行為的資訊。

## <a name="javascript-clients"></a>JavaScript 用戶端

許多雲端原生應用程式會利用前端的伺服器端 Api 和豐富型用戶端單頁應用程式（Spa）。 IdentityServer 透過 NPM 提供的[JavaScript 用戶端](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)（`oidc-client.js`）可新增至 spa，讓他們能夠使用 IdentityServer 進行登入、登出，以及 web api 的權杖型驗證。

## <a name="references"></a>reference

- [IdentityServer 檔](http://docs.identityserver.io/)
- [應用程式類型](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [JavaScript OIDC 用戶端](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)

>[!div class="step-by-step"]
>[上一頁](azure-active-directory.md)
>[下一頁](security.md)
