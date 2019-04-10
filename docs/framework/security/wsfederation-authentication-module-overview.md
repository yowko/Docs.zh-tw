---
title: WSFederation 驗證模組概觀
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: b13536acf71018eb21b6930d7542a9911add8261
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310248"
---
# <a name="wsfederation-authentication-module-overview"></a>WSFederation 驗證模組概觀
Windows Identity Foundation (WIF) 內含可在 ASP.NET 應用程式中透過 WS-同盟驗證模組 (WS-FAM) 提供同盟驗證的支援。 本主題將協助您了解同盟驗證的運作方式以及如何使用它。  
  
### <a name="overview-of-federated-authentication"></a>同盟驗證的概觀  
 同盟驗證可讓一個信任網域中的安全性權杖服務 (STS) 將驗證資訊提供給另一個信任網域中的 STS，條件是這兩個網域之間要有信任關係。 下圖將示範其中一種範例。  
  
 ![同盟驗證情節](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1. Fabrikam 信任網域中的用戶端將某個要求傳送到 Contoso 信任網域中的信賴憑證者 (RP) 應用程式。  
  
2. RP 將用戶端重新導向至 Contoso 信任網域中的 STS。 這個 STS 對該用戶端一無所知。  
  
3. Contoso STS 將用戶端重新導向至與 Contoso 信任網域具有信任關係的 Fabrikam 信任網域中的 STS。  
  
4. Fabrikam STS 驗證用戶端的身分識別，並簽發安全性權杖給 Contoso STS。  
  
5. Contoso STS 使用 Fabrikam 權杖來建立屬於其自身且可由 RP 使用的權杖，並將它傳送到 RP。  
  
6. RP 從安全性權杖擷取用戶端的宣告，並進行授權決策。  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>搭配 ASP.NET 來使用同盟驗證模組  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WS-FAM) 是 HTTP 模組，讓您新增的同盟的驗證[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]應用程式。 同盟驗證會將驗證邏輯交給 STS 處理，讓您可以專心地撰寫商務邏輯。  
  
 您可以設定 WS-FAM，以便指定非驗證要求將重新導向至其中的 STS。 WIF 可讓您使用兩種方式來驗證使用者：  
  
1. 被動式重新導向：當未驗證的使用者嘗試存取受保護的資源，並想要只是重新導向至 STS 而不需要登入頁面時，這是正確的方法。 STS 會驗證使用者的身分識別，並簽發包含該使用者之適當宣告的安全性權杖。 這個選項會要求 WS-FAM 必須加入 HTTP 模組管線中。 您可以使用 Visual Studio 2012 的身分識別與存取工具 ，修改應用程式組態檔來使用 WS-FAM 以及建立與 STS 的同盟。 如需詳細資訊，請參閱 [Visual Studio 2012 的身分識別與存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)。  
  
2. 您可以針對 RP 應用程式的登入頁面，在程式碼後置中呼叫 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> 方法或 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> 方法。  
  
 在被動式重新導向中，所有通訊都是透過用戶端 (通常是瀏覽器) 的回應/重新導向來執行。 您可以將 WS-FAM 新增至應用程式的 HTTP 管線，它會在其中監看是否有未經驗證的使用者要求，並將使用者重新導向至您指定的 STS。  
  
 WS FAM 還會引發數個事件，讓您能夠在 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式中自訂其功能。  
  
### <a name="how-the-ws-fam-works"></a>WS-FAM 的運作方式  
 WS-FAM 會使用 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 類別進行實作。 一般來說，您會將 WS-FAM 加入 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP 應用程式的 HTTP 管線。 當未驗證使用者嘗試存取受保護資源時，RP 就會傳回「401 授權遭拒」HTTP 回應。 WS-FAM 會攔截這個回應而不讓用戶端接收，接著將使用者重新導向至指定的 STS。 STS 會簽發安全性權杖，而 WS-FAM 又會再度攔截此權杖。 WS-FAM 會使用此權杖來為已驗證的使用者建立 <xref:System.Security.Claims.ClaimsPrincipal> 執行個體，如此便可使標準的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 授權機制開始運作。  
  
 因為 HTTP 是無狀態的，所以我們需要採用一種方法，以避免每當使用者嘗試存取其他受保護資源時，就得重複這一整個程序的狀況。 這時就需要用到 <xref:System.IdentityModel.Services.SessionAuthenticationModule>。 當 STS 簽發使用者的安全性權杖時，<xref:System.IdentityModel.Services.SessionAuthenticationModule> 也會建立該使用者的工作階段安全性權杖，並將它放入 Cookie 中。 在處理後續要求時，<xref:System.IdentityModel.Services.SessionAuthenticationModule> 會攔截這個 Cookie，並使用它來重新建構使用者的 <xref:System.Security.Claims.ClaimsPrincipal>。  
  
 下圖顯示在被動式重新導向情況下的整體資訊流程。 該要求會自動透過 STS 進行重新導向來建立認證，而無需使用登入頁面：  
  
 ![使用被動式重新導向進行登入的時機圖表](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 下圖針對使用者已向 STS 完成驗證，其安全性權杖接著由 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 處理時所發生的狀況，提供更多詳細資料：  
  
 ![使用被動式重新導向進行權杖處理的時機](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 下圖針對使用者的安全性權杖已序列化為 Cookie，並由 <xref:System.IdentityModel.Services.SessionAuthenticationModule> 進行攔截時所發生的狀況，提供更多的詳細資料：  
  
 ![顯示使用控制項進行登入的 SAM 時機圖表](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>事件  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule><xref:System.IdentityModel.Services.SessionAuthenticationModule>，和其父類別<xref:System.IdentityModel.Services.HttpModuleBase>，在處理 HTTP 要求的各個階段引發事件。 您可以在 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式的 `global.asax` 檔案中處理這些事件。  
  
-   ASP.NET 基礎結構會叫用模組的 <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> 方法來初始化模組。  
  
-   當 ASP.NET 基礎結構在衍生自 <xref:System.IdentityModel.Services.HttpModuleBase> 的其中一個應用程式模組上第一次叫用 <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> 方法時，就會引發 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> 事件。 這個方法會存取靜態 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> 屬性，因而導致從 Web.config 檔案中載入組態。 只有在第一次存取這個屬性時才會引發此事件。 從組態初始化的 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 物件可以透過事件處理常式中的 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 屬性進行存取。 在將組態套用到任何模組之前，可以使用此事件來修改組態。 您可以在 Application_Start 方法中加入此事件的處理常式：  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     每個模組都會覆寫 <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> 抽象方法。 其中的第一個方法會新增與模組相關之 ASP.NET 管線事件的處理常式。 在大部分情況下，模組的預設實作便已足夠。 其中的第二個方法則會從其下列屬性初始化模組的屬性：<xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> 屬性。 (這是先前所載入之組態的複本)。如果您想要針對類別組態中衍生自 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 或 <xref:System.IdentityModel.Services.SessionAuthenticationModule> 的新屬性支援其初始化作業，則可以覆寫第二個方法。 在這種情況下，您也必須衍生自適當的組態物件，才能支援新增的組態屬性；例如，衍生自 <xref:System.IdentityModel.Configuration.IdentityConfiguration>、<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> 或 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>。  
  
-   WS-FAM 在攔截 STS 所簽發的安全性權杖時，會引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> 事件。  
  
-   WS-FAM 在驗證權杖之後，會引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> 事件。  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> 在建立使用者的工作階段安全性權杖時，會引發 <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> 事件。  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> 在攔截其 Cookie 包含工作階段安全性權杖的後續要求時，會引發 <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> 事件。  
  
-   在 WS-FAM 將使用者重新導向至簽發者之前，它會引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> 事件。 WS-同盟登入要求是透過事件所傳遞之 <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> 的 <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> 屬性來提供。 您可以選擇修改要求，再將此要求傳送給簽發者。  
  
-   當 Cookie 順利寫入且使用者已登入時，WS-FAM 會引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> 事件。  
  
-   WS-FAM 會在每個使用者的工作階段關閉時，針對每一個工作階段引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> 事件一次。 如果工作階段是在用戶端上關閉 (例如，藉由刪除工作階段 Cookie)，則不會引發此事件。 在 SSO 環境中，IP-STS 也可以要求每個 RP 登出。 若將 <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> 設定為 `true`，這也會引發此事件。  
  
> [!NOTE]
>  您不應該在 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 或 <xref:System.IdentityModel.Services.SessionAuthenticationModule> 所引發的任何事件期間使用 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性。 這是因為 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 會在驗證程序之後才設定，而事件則是在驗證程序期間引發。  
  
### <a name="configuration-of-federated-authentication"></a>同盟驗證的組態  
 WS-FAM 和 SAM 是透過 [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 元素進行設定。 [\<wsFederation>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) 子元素可設定 WS-FAM 屬性的預設值；例如 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> 屬性和 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> 屬性。 (藉由提供某些 WS FAM 事件的處理常式，即可依要求來變更這些值；例如 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>)。SAM 所使用的 Cookie 處理常式則是透過 [\<cookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) 子元素進行設定。 WIF 提供了已在 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 類別中實作的預設 Cookie 處理常式，其區塊大小可透過 [\<chunkedCookieHandler>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) 元素來設定。 `<federationConfiguration>` 元素會參考 <xref:System.IdentityModel.Configuration.IdentityConfiguration>，這樣便可提供應用程式所使用之其他 WIF 元件的組態，例如 <xref:System.Security.Claims.ClaimsAuthenticationManager> 和 <xref:System.Security.Claims.ClaimsAuthorizationManager>。 透過在 `<federationConfiguration>` 元素的 `identityConfigurationName` 屬性中指定具名的 [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 元素，即可明確參考身分識別組態。 如果未明確參考身分識別組態，將會使用預設的身分識別組態。  
  
 下列 XML 顯示 ASP.NET 信賴憑證者 (RP) 應用程式的組態。 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> 和 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 組態區段會新增到 `<configSections>` 元素下。 SAM 和 WS-FAM 則會新增到 `<system.webServer>`/`<modules>` 元素下的 HTTP 模組。 最後，會在 `<system.identityModel>`/`<identityConfiguration>`和 `<system.identityModel.services>`/`<federationConfiguration>` 元素下設定 WIF 元件。 這個組態會指定區塊 Cookie 處理常式，因為它是預設的 Cookie 處理常式，但沒有在 `<cookieHandler>` 元素中指定的 Cookie 處理常式類型。  
  
> [!WARNING]
>  在下列範例中，`<wsFederation>` 元素的 `requireHttps` 屬性和 `<cookieHandler>` 元素的 `requireSsl` 屬性都是 `false`。 這會造成潛在的安全性威脅。 在生產環境中，這兩個值都應該設定為 `true`。  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
