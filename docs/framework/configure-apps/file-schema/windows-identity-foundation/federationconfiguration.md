---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152732"
---
# \<federationConfiguration>
<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 透過 WS-同盟通訊協定來使用聯合驗證時，會設定（WSFAM）和（SAM）。 <xref:System.Security.Claims.ClaimsAuthorizationManager>使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別來提供宣告型存取控制時，設定。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a>語法  
  
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
  
|元素|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 SAM 所使用的 cookie 處理常式。 選擇性。|  
|[\<serviceCertificate>](servicecertificate.md)|設定用來加密和解密權杖的憑證。 選擇性。|  
|[\<wsFederation>](wsfederation.md)|設定 WS-同盟驗證模組（WSFAM）。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|使用 WS-同盟通訊協定進行驗證的設定區段。|  
  
## <a name="remarks"></a>備註  
 \<federationConfiguration>元素會在兩個不同的案例中提供設定：  
  
- 在被動 Web 應用程式中使用 WS-同盟時，元素會包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的設定。 它也會參考要用來設定安全性權杖處理常式和憑證的身分識別設定，以及宣告授權管理員和宣告驗證管理員等元件。  
  
- 當使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，元素會參考身分設定，以設定宣告授權管理員和原則，以用來進行授權決策。 即使在不是被動 Web 案例的情況下，也是如此。例如，Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動 Web 應用程式，則專案所參考之身分 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 識別設定的專案（及其子原則元素（如果有的話） `<federationConfiguration>` 是唯一套用的設定。 其他所有項目都會被忽略。  
  
 不論是哪一種情況，執行時間都會載入預設的同盟設定。 其行為定義如下：  
  
1. 如果沒有專案 `<federationConfiguration>` ，執行時間會建立同盟設定，並以預設值填入該設定。 此預設同盟設定會參考預設的身分識別設定。  
  
2. 如果單一專案 `<federationConfiguration>` 存在，則它是預設的同盟設定，不論其名稱為或未命名。 如果指定了它 `identityConfiguration` 的屬性，就會參考指定的身分識別設定，否則會參考預設的身分識別設定。  
  
3. 如果未命名的 `<federationConfiguration>` 元素存在，則為預設的同盟設定。 如果指定了它 `identityConfiguration` 的屬性，就會參考指定的身分識別設定，否則會參考預設的身分識別設定。  
  
4. 如果有多個已命名的專案， `<federationConfiguration>` 而且沒有任何未命名的 `<federationConfiguration>` 元素存在，則會擲回例外狀況。  
  
 通常只 `<federationConfiguration>` 會定義單一區段。 此區段是預設的同盟設定。 您可以指定多個以唯一命名的專案 `<federationConfiguration>` ; 不過，在此情況下，如果您想要載入未命名的同盟設定，則必須提供的處理常式。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件，並將 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 處理常式內的屬性設定為 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 使用 `<federationConfiguration>` 設定檔中適當專案的值來初始化的物件。  
  
 `<federationConfiguration>`元素是由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> 類別表示。 設定物件本身是以 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 類別表示。 在 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上設定單一實例 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，並提供應用程式的同盟設定。  
  
## <a name="example"></a>範例  
 下列 XML 顯示的 `<federationConfiguration>` 元素會指定 WSFAM 的設定，並指定 SAM 使用預設的 cookie 處理常式（類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> ）。  
  
> [!WARNING]
> 在此範例中，cookie 處理常式或 WSFAM 都不需要使用 HTTPS。 這是因為 `requireHttps` 元素上的屬性 `<wsFederation>` 和上的 `requireSsl` 屬性為 `<cookieHandlerElement>` `false` 。 在大部分的生產環境中，不建議使用這些設定，因為它們可能會有安全性風險。  
  
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
