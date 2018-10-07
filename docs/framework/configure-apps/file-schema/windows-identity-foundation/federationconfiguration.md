---
title: '&lt;Federationconfiguration>&gt;'
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 66fa16992d779b08ee8c55598efc98f8f5267656
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847798"
---
# <a name="ltfederationconfigurationgt"></a>&lt;Federationconfiguration>&gt;
會設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) 時使用同盟驗證透過 WS-同盟通訊協定。 會設定<xref:System.Security.Claims.ClaimsAuthorizationManager>使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供的宣告型存取控制。  
  
 \<system.identityModel.services >  
\<Federationconfiguration> >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|這個同盟組態項目的名稱。 這個屬性主要是提供的擴充點，針對未來的通訊協定。 選擇性。|  
|identityConfigurationName|身分識別組態區段中所指定的名稱[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)若要使用的項目。 如果未指定此屬性，則會使用預設的身分識別組態區段。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定 SAM 所使用的 cookie 處理常式。 選擇性。|  
|[\<v >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|設定用來加密和解密權杖的憑證。 選擇性。|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|設定 WS-同盟驗證模組 (WSFAM)。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|使用 WS-同盟通訊協定進行驗證的組態區段。|  
  
## <a name="remarks"></a>備註  
 \<Federationconfiguration> > 項目會提供兩種不同案例中的設定：  
  
-   項目時使用 WS-同盟被動式 Web 應用程式中，包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。 它也會參考用來設定安全性權杖處理常式和憑證，以及元件，例如宣告授權管理員和宣告驗證管理員的身分識別組態。  
  
-   使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供您的程式碼中的宣告型存取控制，項目會參考的識別組態，以設定宣告授權管理員和用來進行授權的原則決策。 這是為 true，即使在不是被動的 Web 案例; 的案例比方說，Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動的 Web 應用程式中， [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)項目 （和其子原則項目，如果有的話） 所參考的識別組態的`<federationConfiguration>`項目唯一的設定會套用。 其他所有項目都會被忽略。  
  
 此案例中，不論執行階段會載入預設的同盟設定。 定義行為，如下所示：  
  
1.  如果沒有任何`<federationConfiguration>`元素，執行階段會建立同盟設定，並填入預設值。 這個預設的同盟組態會參考預設身分識別組態。  
  
2.  如果單一`<federationConfiguration>`項目已存在，它是預設的同盟設定，不論它是具名或未命名的。 如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態，否則參考預設身分識別組態。  
  
3.  如果有未命名`<federationConfiguration>`項目已存在，它是預設的同盟設定。 如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態，否則參考預設身分識別組態。  
  
4.  如果多個名為`<federationConfiguration>`項目會存在且未具名`<federationConfiguration>`項目存在，則會擲回例外狀況。  
  
 一般而言，只有一個`<federationConfiguration>`區段定義。 本節是預設的同盟設定。 您可以指定多個唯一命名`<federationConfiguration>`項目; 不過，在此情況下，如果您想要載入非未命名的同盟設定，您必須提供的處理常式。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> 事件和設定<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>內的處理常式屬性<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件從適當的值初始化`<federationConfiguration>`組態檔中的項目。  
  
 `<federationConfiguration>`項目由<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>類別。 設定物件本身由<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別。 單一<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>上設定執行個體<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性，並提供應用程式的同盟的設定。  
  
## <a name="example"></a>範例  
 下列 XML 會說明`<federationConfiguration>`項目，指定 WSFAM 設定，並指定預設的 cookie 處理常式 (的執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別) 可供 SAM。  
  
> [!WARNING]
>  在此範例中，cookie 處理常式和 WSFAM 都不需要使用 HTTPS。 這是因為`requireHttps`屬性`<wsFederation>`項目並`requireSsl`屬性`<cookieHandlerElement>`是`false`。 因為它們可能會有安全性風險，這些設定不建議用於大部分的生產環境。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
