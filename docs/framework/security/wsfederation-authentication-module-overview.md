---
title: "WSFederation 驗證模組概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# WSFederation 驗證模組概觀
Windows Identity Foundation \(WIF\) 在 ASP.NET 應用程式支援聯合驗證透過 WS\-Federation 驗證模組 \(WS\-FAM\)。  本主題將協助您了解等位的驗證如何運作以及如何使用它。  
  
### 等位的驗證摘要  
 當有兩個網域之間時，的信任關係等位的允許驗證安全性權杖服務以信任網域的 \(STS\) 提供驗證資訊給其他信任網域的 STS。  這個的範例如下圖所示。  
  
 ![同盟驗證情節](../../../docs/framework/security/media/federatedauthentication.png "FederatedAuthentication")  
  
1.  Fabrikam 信任網域的用戶端傳送要求至 Contoso 信任網域的信賴憑證者 \(RP\) 應用程式。  
  
2.  RP 將用戶端重新導向至 Contoso 信任網域的 STS。  這個 STS 不了解用戶端。  
  
3.  Contoso STS 將用戶端重新導向至 Fabrikam 信任網域的 STS， Contoso 信任網域不信任關係。  
  
4.  Fabrikam STS 驗證用戶端的識別和發行安全性權杖至 Contoso STS。  
  
5.  Contoso STS Fabrikam 使用語彙基元建立可由 RP 使用其語彙基元並傳送給 RP。  
  
6.  RP 從安全性權杖提取用戶端之宣告並做出授權決策。  
  
### 搭配 ASP.NET 的等位的驗證模組。  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WS\-FAM\) 是可讓您將等位的驗證加入至 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式的 HTTP 模組。  等位的驗證可讓驗證邏輯由 STS 處理並讓您專注於撰寫商務邏輯。  
  
 您設定 WS\-FAM 指定未經驗證的要求應該重新導向的 STS。  WIF 讓您驗證使用者有兩種:  
  
1.  被動重新導向:當一個未經驗證的使用者嘗試存取受保護的資源時，，而且您想要將它們重新導向至 STS，而不需要登入頁面，則這是正確的方法。  表示驗證使用者的身分識別，並發行包含該使用者的適當宣告的安全性權杖。  這個選項在 HTTP 模組管線要求 WS\-FAM 增加。  您可以使用識別和存取為 Visual Studio 2012 的工具修改應用程式組態檔使用 WS\-FAM 和縮放成同盟與 STS。  如需詳細資訊，請參閱[Visual Studio 2012 的識別和存取工具](../../../docs/framework/security/identity-and-access-tool-for-vs.md)。  
  
2.  您可以呼叫 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=fullName> 方法或 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> 方法從程式碼後置登入頁面所 RP 應用程式。  
  
 在被動重新導向，所有通訊是透過回應執行與用戶端 \(通常是瀏覽器\) 重新導向。  您可以將 WS\-FAM 加入應用程式的 HTTP 管線，則請注意未經驗證的使用者要求並將使用者重新導向至 STS 您指定。  
  
 WS\-FAM 也會讓您自訂其在 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式功能的數個事件。  
  
### WS\-FAM 的運作方式  
 WS\-FAM 在 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 類別上實作。  通常，您將 WS\-FAM 加入到 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP 應用程式 HTTP 管線。  當一個未經驗證的使用者嘗試存取受保護的資源時， RP 傳回「401 授權拒絕」HTTP 回應。  WS\-FAM 攔截回應而不要讓用戶端接收它，然後將使用者重新導向至指定的 STS。  STS 發行安全性權杖， WS\-FAM 再攔截。  WS\-FAM 使用語彙基元建立 <xref:System.Security.Claims.ClaimsPrincipal> 執行個體已驗證使用者的規則，讓 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 授權機制運作。  
  
 由於 HTTP 沒有狀態，我們需要方法來避免每次重複這整個處理序使用者嘗試存取其他受保護的資源。  這是 <xref:System.IdentityModel.Services.SessionAuthenticationModule> 傳入的地方。  當 STS 發出使用者的安全性權杖， <xref:System.IdentityModel.Services.SessionAuthenticationModule> 也會建立使用者並放置的工作階段安全性權杖它在 Cookie。  在後續要求中， <xref:System.IdentityModel.Services.SessionAuthenticationModule> 會攔截這個 Cookie 並重建使用者的 <xref:System.Security.Claims.ClaimsPrincipal>。  
  
 下圖顯示在被動的整體資訊流變更大小寫方向。  要求已經藉由 STS 自動重新導向而建立的認證，而不需要登入網頁:  
  
 ![顯示使用被動式重新導向登入的時機圖表](../../../docs/framework/security/media/signinusingpassiveredirect.png "SignInUsingPassiveRedirect")  
  
 下圖顯示在發生原因的詳細資料，則驗證對 STS，而其安全性權杖由 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>管理:  
  
 ![顯示使用被動式重新導向處理語彙基元的時機](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.png "SignInUsingPassiveRedirect\_TokenProcessing")  
  
 下圖顯示在發生原因的詳細資料，在序列化至 Cookie 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule>時攔截使用者的安全性語彙基元:  
  
 ![顯示使用控制項登入的 SAM 時機圖表](../../../docs/framework/security/media/signinusingconrols-sam.png "SignInUsingConrols\_SAM")  
  
### 事件  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>、 <xref:System.IdentityModel.Services.SessionAuthenticationModule>和其父類別的，則為 <xref:System.IdentityModel.Services.HttpModuleBase>，則引發事件在各個階段處理 HTTP 要求。  您可以處理在 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式 `global.asax` 檔案中的這些事件。  
  
-   ASP.NET 基礎結構會叫用模組的 <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> 方法中初始化模組。  
  
-   引發 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=fullName> 事件，當 ASP.NET 基礎結構第一次叫用 <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> 方法在衍生自 <xref:System.IdentityModel.Services.HttpModuleBase>的其中一個應用程式模組時。  這個方法會存取靜態 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName> 屬性，導致組態從 Web.config 檔案載入。  第一次存取這個屬性時，才會引發這個事件。  從組態初始化的 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 物件可以透過在事件處理常式的 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=fullName> 屬性存取。  會套用至所有模組之前，您可以使用這個事件修改組態。  您可以將這個事件的處理常式在 Application\_Start 方法:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     每個模組覆寫 <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=fullName> 和 <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=fullName> 抽象方法。  第一種方法加入 ASP.NET 要注意到模組的管線事件的處理常式。  在大部分情況下模組的預設實作就足夠了。  第二個這些方法初始化從它的 <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=fullName> 屬性之模組的屬性。\(這是先前載入\) 組態的複本您可能需要覆寫這個第二個方法中，如果您要支援新屬性的初始化從組態中的 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 或衍生自 <xref:System.IdentityModel.Services.SessionAuthenticationModule>的類別。  此時您也會需要從適當的組態物件取得支援加入的組態屬性;例如，從 <xref:System.IdentityModel.Configuration.IdentityConfiguration>、 <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>或 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>。  
  
-   WS\-FAM 引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> 事件，以攔截由 STS 發行的安全性權杖時。  
  
-   在驗證語彙基元之後， WS\-FAM 引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> 事件。  
  
-   在建立使用者時，一個工作階段安全性權杖 <xref:System.IdentityModel.Services.SessionAuthenticationModule> 引發 <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> 事件。  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> 引發 <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> 事件，當包含工作階段安全性權杖的它攔截與 Cookie 時的要求。  
  
-   在 WS\-FAM 將使用者重新導向至簽發者之前，會引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> 事件。  WS\-Federation 登入要求傳遞之 <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> 的 <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> 屬性可以在事件。  您可以選擇在傳送之前修改此要求的簽發者。  
  
-   WS\-FAM 引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> 事件，當 Cookie 成功寫入時，而且使用者登入。  
  
-   因為這個工作階段是每個使用者，停止引發 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> 事件 WS\-FAM 每個工作階段一次。  它不會引發事件，如果工作階段是在用戶端上停止 \(例如，藉由刪除工作階段 Cookie\)。  在 SSO 環境， IP\-STS 可以要求每個 RP 簽署，則也是。  這也會引發這個事件，將 <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> 設為 `true`。  
  
> [!NOTE]
>  您不應該使用 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> 屬性在 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 或 <xref:System.IdentityModel.Services.SessionAuthenticationModule>所引發的任何事件期間。  這是因為， <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> 在驗證程序之後，設定，而事件會在驗證過程中引發。  
  
### 聯合驗證的組態  
 WS\-FAM 和 SAM 透過 [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目設定。  [\<wsFederation\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) 子項目設定 WS\-FAM 屬性的預設值;\( <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> 屬性和 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> 屬性。\(這些值中可以變更每個要求來提供處理常式為某些 WS\-FAM 事件;例如， <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>\)。SAM 使用的 Cookie 處理常式傳遞 [\<cookieHandler\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) 子項目配置。  WIF 提供在可能會透過 [\<chunkedCookieHandler\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) 項目設定其區塊大小的 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 類別實作的預設 Cookie 處理常式。  `<federationConfiguration>` 項目參考 <xref:System.IdentityModel.Configuration.IdentityConfiguration>，為應用程式中的其他元件 WIF 提供組態，例如 <xref:System.Security.Claims.ClaimsAuthenticationManager> 和 <xref:System.Security.Claims.ClaimsAuthorizationManager>。  識別組態可能藉由指定具名 [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 項目明確參考在 `<federationConfiguration>` 項目的 `identityConfigurationName` 屬性。  如果識別組態未明確參考，則會使用預設的識別組態。  
  
 下列 XML 顯示 ASP.NET 信賴憑證者 \(RP\) 應用程式的組態。  <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> 和 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 組態區段將在 `<configSections>` 項目底下。  SAM 和 WS\-FAM 加入 `<system.webServer>`\/`<modules>` 項目之下的 HTTP 模組。  最終 WIF 元件設定 `<system.identityModel>`\/`<identityConfiguration>` 和 `<system.identityModel.services>`\/`<federationConfiguration>` 項目之下。  這個組態指定區塊 cookie 處理常式，因為它是預設 Cookie 處理常式，但 `<cookieHandler>` 元素指定的 Cookie 處理常式類型。  
  
> [!WARNING]
>  在下列範例中，兩個 `<wsFederation>` 項目的 `requireHttps` 屬性和 `<cookieHandler>` 項目的 `requireSsl` 屬性為 `false`。  這樣會有潛在的安全性威脅。  在產生，這兩個值應該設定為 `true`。  
  
```  
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
  
## 請參閱  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>   
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)