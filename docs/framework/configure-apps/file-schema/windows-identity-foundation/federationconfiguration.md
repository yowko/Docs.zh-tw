---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: c4dbb31bb7961f0d33df9d1faee8fe36ecb520a3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988334"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
透過 WS-同盟通訊協定來<xref:System.IdentityModel.Services.SessionAuthenticationModule>使用聯合驗證時, 會設定(WSFAM)和(SAM)。<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 使用或<xref:System.Security.Claims.ClaimsAuthorizationManager> 類別<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>來提供宣告型存取控制時, 設定。 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
  
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
|NAME|此同盟設定元素的名稱。 這個屬性主要是針對未來的通訊協定提供擴充點。 選擇性。|  
|identityConfigurationName|要使用之[ \<identityConfiguration >](identityconfiguration.md)專案中所指定的身分識別設定區段的名稱。 如果未指定此屬性, 則會使用預設的身分識別設定區段。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 SAM 所使用的 cookie 處理常式。 選擇性。|  
|[\<serviceCertificate>](servicecertificate.md)|設定用來加密和解密權杖的憑證。 選擇性。|  
|[\<wsFederation>](wsfederation.md)|設定 WS-同盟驗證模組 (WSFAM)。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|使用 WS-同盟通訊協定進行驗證的設定區段。|  
  
## <a name="remarks"></a>備註  
 \<FederationConfiguration > 元素會在兩個不同的案例中提供設定:  
  
- 在被動 Web 應用程式中使用 WS-同盟時, 元素會<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>包含設定 (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) 的設定。 它也會參考要用來設定安全性權杖處理常式和憑證的身分識別設定, 以及宣告授權管理員和宣告驗證管理員等元件。  
  
- 當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>或類別在您的程式碼中提供宣告型存取控制時, 元素會參考身分設定, 以設定宣告授權管理員和用來進行授權的原則。決策. 即使在不是被動 Web 案例的情況下, 也是如此。例如, Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動 Web 應用程式, `<federationConfiguration>` [ \<](claimsauthorizationmanager.md)則專案所參考之身分識別設定的 claimsAuthorizationManager > 專案 (及其子原則元素, 如果有的話) 是唯一的設定套用. 其他所有項目都會被忽略。  
  
 不論是哪一種情況, 執行時間都會載入預設的同盟設定。 其行為定義如下:  
  
1. 如果沒有專案, `<federationConfiguration>`執行時間會建立同盟設定, 並以預設值填入該設定。 此預設同盟設定會參考預設的身分識別設定。  
  
2. 如果單一`<federationConfiguration>`專案存在, 則它是預設的同盟設定, 不論其名稱為或未命名。 如果指定`identityConfiguration`了它的屬性, 就會參考指定的身分識別設定, 否則會參考預設的身分識別設定。  
  
3. 如果未命名`<federationConfiguration>`的元素存在, 則為預設的同盟設定。 如果指定`identityConfiguration`了它的屬性, 就會參考指定的身分識別設定, 否則會參考預設的身分識別設定。  
  
4. 如果有多`<federationConfiguration>`個已命名的專案, `<federationConfiguration>`而且沒有任何未命名的元素存在, 則會擲回例外狀況。  
  
 通常只會定義單一`<federationConfiguration>`區段。 此區段是預設的同盟設定。 您可以指定多個以唯一命名`<federationConfiguration>`的專案; 不過, 在此情況下, 如果您想要載入未命名的同盟設定, 則必須提供的處理常式。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件, 並將<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>處理常式內的屬性設定<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>為使用設定檔中適當`<federationConfiguration>`專案的值來初始化的物件。  
  
 `<federationConfiguration>`元素是<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>由類別表示。 設定物件本身是以<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別表示。 在<xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>上設定單一實例, 並提供應用程式的同盟設定。  
  
## <a name="example"></a>範例  
 下列 XML 顯示`<federationConfiguration>`的元素會指定 WSFAM 的設定, 並指定 SAM 使用預設的 cookie 處理常式 ( <xref:System.IdentityModel.Services.ChunkedCookieHandler>類別的實例)。  
  
> [!WARNING]
> 在此範例中, cookie 處理常式或 WSFAM 都不需要使用 HTTPS。 `requireHttps`這是因為`false` `<cookieHandlerElement>` `requireSsl`元素上的屬性和上的屬性為。 `<wsFederation>` 在大部分的生產環境中, 不建議使用這些設定, 因為它們可能會有安全性風險。  
  
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

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
