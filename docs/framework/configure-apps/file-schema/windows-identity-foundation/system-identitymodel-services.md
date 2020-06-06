---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152500"
---
# \<system.identityModel.services>
使用 WS-同盟通訊協定進行驗證的設定區段。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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
 無  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM） HTTP 模組的設定。|  
  
### <a name="parent-elements"></a>父項目  
 None  
  
## <a name="remarks"></a>備註  
 將 `<system.identityModel.services>` 區段新增至應用程式的設定檔，以提供 SAM 和 WSFAM 的設定。  
  
> [!IMPORTANT]
> 當您使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，宣告授權管理員（ <xref:System.Security.Claims.ClaimsAuthorizationManager> ）和用來進行授權決策的原則，都是透過 `<identityConfiguration>` 這個區段中的元素隱含或明確參考的專案來設定 `<federationConfiguration>` 。 如需詳細資訊，請參閱元素底下的**備註** [\<federationConfiguration>](federationconfiguration.md) 。  
  
 `<system.identityModel.services>`區段是由 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 類別表示。 區段中所設定之子專案的集合 `<federationConfiguration>` 是由類別表示 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> 。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何將 `<system.identityModel.services>` 區段新增至設定檔。 您必須先為 `<system.identityModel.services>` 區段和區段新增區段宣告 `<system.identityModel>` 。 （當您新增 `<system.identityModel.services>` 區段時，您也應該新增區段的宣告， `<system.identityModel>` 以確保執行時間可以視 `<identityConfiguration>` 需要建立預設區段）。新增區段宣告之後，您可以在元素下設定同盟驗證設定 `<system.identityModel.services>` 。  
  
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
