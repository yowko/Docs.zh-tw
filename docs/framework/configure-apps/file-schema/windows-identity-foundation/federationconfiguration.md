---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152732"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
通過 WS-聯合協定使用識別身分同盟時配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>（SAM）。 配置<xref:System.Security.Claims.ClaimsAuthorizationManager>使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類時提供基於聲明的存取控制。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型.服務>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<聯合配置>**  
  
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
|NAME|這個聯合組態項目的名稱。 此屬性主要為未來的協定提供擴充點。 選擇性。|  
|標識配置名稱|標識配置中指定的標識配置部分的名稱>要使用的元素。 [ \< ](identityconfiguration.md) 如果未指定此屬性，則使用預設標識配置部分。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<餅乾漢德勒>](cookiehandler.md)|配置 SAM 使用的 Cookie 處理常式。 選擇性。|  
|[\<服務證書>](servicecertificate.md)|配置用於加密和解密權杖的證書。 選擇性。|  
|[\<ws聯邦>](wsfederation.md)|配置 WS-識別身分同盟模組 （WSFAM）。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<系統.身份模型.服務>](system-identitymodel-services.md)|使用 WS-聯合協定進行身份驗證的配置部分。|  
  
## <a name="remarks"></a>備註  
 聯合\<配置>元素在兩種不同的方案中提供設置：  
  
- 在被動 Web 應用程式中使用 WS-聯合時，元素包含配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和 （SAM） 的<xref:System.IdentityModel.Services.SessionAuthenticationModule>設置。 它還引用用於配置安全權杖處理常式和證書的標識配置，以及聲明授權管理員和聲明身份驗證管理器等元件。  
  
- 當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類在代碼中提供基於聲明的存取控制時，元素引用標識配置，該配置用於做出授權決策的聲明授權管理員和策略。 這是事實，即使在不是被動 Web 方案的情況下也是如此;例如，Windows 通信基礎 （WCF） 應用程式或非基於 Web 的應用程式。 如果應用程式不是被動 Web 應用程式，則`<federationConfiguration>`該元素引用的標識配置[\<的聲明授權管理員>](claimsauthorizationmanager.md)元素（及其子策略元素（如果存在）是應用的唯一設置。 其他所有項目都會被忽略。  
  
 無論方案如何，運行時都會載入預設識別身分同盟配置。 行為的定義如下：  
  
1. 如果沒有`<federationConfiguration>`元素存在，運行時將創建聯合配置，並將其填充為預設值。 此預設識別身分同盟配置將引用預設標識配置。  
  
2. 如果存在單個`<federationConfiguration>`元素，則無論它是命名還是未命名，它都是預設的聯合配置。 如果指定`identityConfiguration`了其屬性，則引用命名標識配置;如果指定標識配置被引用。否則，將引用預設標識配置。  
  
3. 如果存在未命名的`<federationConfiguration>`元素，則它是預設的聯合配置。 如果指定`identityConfiguration`了其屬性，則引用命名標識配置;如果指定標識配置被引用。否則，將引用預設標識配置。  
  
4. 如果存在多個命名`<federationConfiguration>`元素，並且不存在未命名`<federationConfiguration>`元素，則引發異常。  
  
 通常，只定義單個`<federationConfiguration>`節。 此部分是預設聯合配置。 您可以指定多個唯一命名的元素;`<federationConfiguration>`但是，您可以指定多個唯一命名的元素。但是，在這種情況下，如果要載入非命名配置以外的聯合配置，則必須為 提供處理常式。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件，並將處理常式<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>內的屬性設置為使用設定檔中<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>相應元素中的值`<federationConfiguration>`初始化的物件。  
  
 元素`<federationConfiguration>`由類<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>表示。 設定物件本身由類<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>表示。 在<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>屬性上設置單個實例<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>，並為應用程式提供聯合配置。  
  
## <a name="example"></a>範例  
 以下 XML 顯示了`<federationConfiguration>`一個元素，該元素指定 WSFAM 的設置，並指定 SAM 使用<xref:System.IdentityModel.Services.ChunkedCookieHandler>預設 Cookie 處理常式（類的實例）。  
  
> [!WARNING]
> 在此示例中，不需要 Cookie 處理常式和 WSFAM 使用 HTTPS。 這是因為`requireHttps``<wsFederation>`元素上的屬性和`requireSsl`上的屬性`<cookieHandlerElement>`是`false`。 不建議大多數生產環境使用這些設置，因為它們可能會帶來安全風險。  
  
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
- [\<身份配置>](identityconfiguration.md)
