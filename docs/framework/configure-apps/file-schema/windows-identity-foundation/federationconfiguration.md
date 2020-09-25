---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 39e96a161a2e75d5f00b73f6b08b1e4a0c109aee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201352"
---
# \<federationConfiguration>

<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 使用透過 WS-同盟通訊協定的同盟驗證時，設定 (WSFAM) 和 (SAM) 。 <xref:System.Security.Claims.ClaimsAuthorizationManager>使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別來提供宣告式存取控制時，設定。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|這個聯合組態項目的名稱。 這個屬性主要是針對未來的通訊協定提供擴充點。 選擇性。|  
|identityConfigurationName|身分識別設定區段的名稱，如要使用的元素中所指定 [\<identityConfiguration>](identityconfiguration.md) 。 如果未指定此屬性，則會使用預設的身分識別設定區段。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 SAM 所使用的 cookie 處理常式。 選擇性。|  
|[\<serviceCertificate>](servicecertificate.md)|設定用來加密和解密權杖的憑證。 選擇性。|  
|[\<wsFederation>](wsfederation.md)|設定 WS-同盟驗證模組 (WSFAM) 。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|使用 WS-同盟通訊協定進行驗證的設定區段。|  
  
## <a name="remarks"></a>備註  

 \<federationConfiguration>元素提供兩種不同案例中的設定：  
  
- 在被動 Web 應用程式中使用 WS-同盟時，元素包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的設定。 它也會參考用來設定安全性權杖處理常式和憑證的身分識別設定，以及宣告授權管理員和宣告驗證管理員等元件。  
  
- 使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，專案會參考設定宣告授權管理員的身分識別設定，以及用來進行授權決策的原則。 即使是在非被動 Web 案例的案例中，也是如此。例如，Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動 Web 應用程式，則專案 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 會 (和其子原則元素，如果專案所參考的身分識別設定有) ，則 `<federationConfiguration>` 唯一適用的設定。 其他所有項目都會被忽略。  
  
 無論何種情況，執行時間都會載入預設同盟設定。 此行為定義如下：  
  
1. 如果沒有任何專案 `<federationConfiguration>` ，執行時間會建立同盟設定，並以預設值填入。 此預設同盟設定會參考預設身分識別設定。  
  
2. 如果有單一專案 `<federationConfiguration>` ，它就是預設的同盟設定，不論它是否命名或未命名。 如果指定了其 `identityConfiguration` 屬性，則會參考命名身分識別設定，否則會參考預設身分識別設定。  
  
3. 如果有未命名的 `<federationConfiguration>` 元素，則為預設的同盟設定。 如果指定了其 `identityConfiguration` 屬性，則會參考命名身分識別設定，否則會參考預設身分識別設定。  
  
4. 如果有多個命名 `<federationConfiguration>` 元素存在，而且沒有未命名的 `<federationConfiguration>` 元素，則會擲回例外狀況。  
  
 通常只 `<federationConfiguration>` 會定義一個區段。 此區段是預設的同盟設定。 您可以指定多個唯一命名的專案 `<federationConfiguration>` ; 不過，在此情況下，如果您想要載入非未命名的同盟設定，則必須提供的處理常式。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> 事件，並將 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 處理常式中的屬性設定為 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 使用 `<federationConfiguration>` 設定檔中適當元素的值初始化的物件。  
  
 `<federationConfiguration>`元素是由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> 類別表示。 設定物件本身是以 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 類別表示。 在 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上設定單一實例 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，並為應用程式提供同盟設定。  
  
## <a name="example"></a>範例  

 下列 XML `<federationConfiguration>` 會顯示指定 WSFAM 設定的專案，並指定預設的 cookie 處理常式 (類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler>) 由 SAM 使用。  
  
> [!WARNING]
> 在此範例中，cookie 處理常式和 WSFAM 都不需要使用 HTTPS。 這是因為 `requireHttps` 元素上的屬性 `<wsFederation>` 和上的 `requireSsl` 屬性 `<cookieHandlerElement>` 是 `false` 。 這些設定不建議用於大部分的生產環境，因為它們可能會有安全性風險。  
  
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
