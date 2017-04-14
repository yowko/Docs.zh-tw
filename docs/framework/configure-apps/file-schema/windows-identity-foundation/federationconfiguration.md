---
title: "&lt;federationConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;federationConfiguration&gt;
設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) 使用時同盟透過 WS\-同盟通訊協定的驗證。  設定<xref:System.Security.Claims.ClaimsAuthorizationManager>時使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供宣告式存取控制。  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|此聯盟的組態項目的名稱。  這個屬性主要是提供未來的通訊協定的擴充點。  選擇項。|  
|identityConfigurationName|識別組態區段中所指定的名稱[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)若要使用的項目。  如果不指定這個屬性，則會使用預設的識別身份的組態區段。  選擇項。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定 SAM 所使用的 cookie 處理常式。  選擇項。|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|設定憑證，用來加密和解密語彙基元。  選擇項。|  
|[\<wsFederation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|設定 WS\-同盟驗證模組 \(WSFAM\)。  選擇項。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.identityModel.services\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|使用 「 WS\-同盟通訊協定進行驗證的組態區段。|  
  
## 備註  
 \<federationConfiguration\> 項目會提供兩個不同的案例中的設定：  
  
-   項目使用時 WS\-同盟被動式的 Web 應用程式中，包含設定的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。  它也會參考用來設定安全性語彙基元的處理常式與憑證及元件，例如宣告的授權管理員和宣告驗證管理者的身分識別組態。  
  
-   當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別來提供在程式碼中的宣告式存取控制、 項目會參考識別組態，以設定宣告授權管理員和原則，用來製作授權決策。  這是，則為 true，甚至在案例中不是被動 Web 的案例。 比方說，Windows 通訊資格應用程式或不是以 Web 為基礎的應用程式。  如果應用程式不是被動的 Web 應用程式中， [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)項目 \(與其子原則項目，如果有的話\) 識別組態所參考的`<federationConfiguration>`項目所套用的唯一設定。  其他所有項目都會遭忽略。  
  
 不論案例而定，執行階段會載入預設的聯盟設定。  定義行為，如下所示：  
  
1.  如果沒有任何`<federationConfiguration>`項目存在，執行階段會建立聯盟設定，並填入預設值。  這個預設聯盟組態會參考預設身分的設定。  
  
2.  如果有一個`<federationConfiguration>`項目不存在，是預設的聯盟設定，不論它是具名或未命名的。  如果其`identityConfiguration`屬性指定，則會參考已命名的識別身份設定 ； 否則，就會參考預設身分的設定。  
  
3.  如果未命名`<federationConfiguration>`項目不存在，是預設的聯盟設定。  如果其`identityConfiguration`屬性指定，則會參考已命名的識別身份設定 ； 否則，就會參考預設身分的設定。  
  
4.  如果多個名為`<federationConfiguration>`項目是存在且無法命名`<federationConfiguration>`項目不存在，會擲回例外狀況。  
  
 一般而言，只會有一個`<federationConfiguration>`區段定義。  這一節是預設的聯盟設定。  您可以指定多個具有唯一名稱`<federationConfiguration>`項目。 不過，在此情況下，如果您想要載入不是未命名的聯盟組態，您必須提供的處理常式。  <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件和設定<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=fullName>屬性處理常式，以便在<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件，您可以從對應的值初始化`<federationConfiguration>`在組態檔中的項目。  
  
 `<federationConfiguration>`項目會以<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>類別。  組態物件本身由<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別。  會有一個<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>執行個體上設定<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>屬性，並提供應用程式的聯盟的設定。  
  
## 範例  
 下列 XML 顯示`<federationConfiguration>`項目，可指定 WSFAM 設定，並指定，預設 cookie 的處理常式 \(的執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別\) 供 SAM。  
  
> [!WARNING]
>  在這個範例中，cookie 的處理常式和 WSFAM 都不需要使用 HTTPS。  這是因為`requireHttps`在`<wsFederation>`項目和`requireSsl`在`<cookieHandlerElement>`是`false`。  這些設定大部分的實際執行環境下不建議使用，因為它們可能會有安全性風險。  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>   
 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)