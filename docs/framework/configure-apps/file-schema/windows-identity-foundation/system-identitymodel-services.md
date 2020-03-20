---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152500"
---
# <a name="systemidentitymodelservices"></a>\<系統.身份模型.服務>
使用 WS-聯合協定進行身份驗證的配置部分。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;**\<系統.身份模型.服務>**  
  
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
 None  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<聯合配置>](federationconfiguration.md)|包含配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和 （SAM） <xref:System.IdentityModel.Services.SessionAuthenticationModule> HTTP 模組的設置。|  
  
### <a name="parent-elements"></a>父項目  
 None  
  
## <a name="remarks"></a>備註  
 向應用程式的`<system.identityModel.services>`設定檔添加一節，以提供 SAM 和 WSFAM 的設置。  
  
> [!IMPORTANT]
> 當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類在代碼中提供基於聲明的存取控制時，用於做出授權決策的聲明授權<xref:System.Security.Claims.ClaimsAuthorizationManager>管理器 （ ） 和策略通過從本節中`<identityConfiguration>``<federationConfiguration>`的元素隱式或顯式引用的元素進行配置。 有關詳細資訊，請參閱[\<聯合配置>](federationconfiguration.md)元素下的**備註**。  
  
 該`<system.identityModel.services>`節由類<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>表示。 在節中配置的`<federationConfiguration>`子項目的集合由類<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>表示。  
  
## <a name="example"></a>範例  
 以下 XML 演示如何向設定檔添加`<system.identityModel.services>`節。 必須首先為`<system.identityModel.services>`節和`<system.identityModel>`節添加節聲明。 （添加`<system.identityModel.services>`節時，還應為`<system.identityModel>`節添加聲明，以確保運行時在必要時可以創建預設`<identityConfiguration>`節。添加節聲明後，可以在`<system.identityModel.services>`元素下配置識別身分同盟設置。  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
