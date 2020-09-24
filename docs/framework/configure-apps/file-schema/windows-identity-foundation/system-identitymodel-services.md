---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e909756a58d5008d917fca84af0e478fc4878d2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156806"
---
# \<system.identityModel.services>

使用 WS-同盟通訊協定進行驗證的設定區段。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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

 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP 模組的設定。|  
  
### <a name="parent-elements"></a>父項目  

 None  
  
## <a name="remarks"></a>備註  

 將 `<system.identityModel.services>` 區段新增至您的應用程式佈建檔，以提供 SAM 和 WSFAM 的設定。  
  
> [!IMPORTANT]
> 使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，宣告授權管理員 (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ，以及用來進行授權決策的原則，是透過 `<identityConfiguration>` `<federationConfiguration>` 此區段中的元素隱含或明確參考的元素來設定。 如需詳細資訊，請參閱元素底下的 **備註** [\<federationConfiguration>](federationconfiguration.md) 。  
  
 `<system.identityModel.services>`區段是由 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 類別表示。 在 `<federationConfiguration>` 區段中設定之子項目的集合是由類別表示 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> 。  
  
## <a name="example"></a>範例  

 下列 XML 說明如何將 `<system.identityModel.services>` 區段新增至設定檔。 您必須先為 `<system.identityModel.services>` 區段和區段加入區段宣告 `<system.identityModel>` 。  (當您加入 `<system.identityModel.services>` 區段時，您也應該加入區段的宣告， `<system.identityModel>` 以確保執行時間可以在 `<identityConfiguration>` 必要時建立預設區段。 ) 加入區段宣告之後，您可以在專案下設定同盟驗證設定 `<system.identityModel.services>` 。  
  
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
