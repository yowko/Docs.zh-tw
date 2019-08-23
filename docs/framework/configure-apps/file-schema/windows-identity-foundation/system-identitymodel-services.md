---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943663"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
使用 WS-同盟通訊協定進行驗證的設定區段。  
  
 \<system.identityModel.services>  
  
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
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) HTTP 模組的設定。|  
  
### <a name="parent-elements"></a>父項目  
 None  
  
## <a name="remarks"></a>備註  
 `<system.identityModel.services>`將區段新增至應用程式的設定檔, 以提供 SAM 和 WSFAM 的設定。  
  
> [!IMPORTANT]
> 當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>或類別在您的程式碼中提供宣告型存取控制時, 宣告授權管理員 () 和用`<identityConfiguration>`來進行授權決策的原則會透過<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>從這個區段的`<federationConfiguration>`元素隱含或明確參考的專案。 如需詳細資訊, 請參閱[ \<federationConfiguration >](federationconfiguration.md)元素底下的**備註**。  
  
 `<system.identityModel.services>`區段是<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>由類別表示。 區段中所設定`<federationConfiguration>`之子專案的集合是<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>由類別表示。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何將`<system.identityModel.services>`區段新增至設定檔。 您必須先為`<system.identityModel.services>`區段`<system.identityModel>`和區段新增區段宣告。 (當您新增`<system.identityModel.services>`區段時, 您也應該新增`<system.identityModel>`區段的宣告, 以確保執行時間可以視`<identityConfiguration>`需要建立預設區段)。新增區段宣告之後, 您可以在`<system.identityModel.services>`元素下設定同盟驗證設定。  
  
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
