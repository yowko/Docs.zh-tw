---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362951"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
使用 WS-同盟通訊協定進行驗證的組態區段。  
  
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
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) HTTP 模組。|  
  
### <a name="parent-elements"></a>父項目  
 無  
  
## <a name="remarks"></a>備註  
 新增`<system.identityModel.services>`SAM 和 WSFAM 提供設定您的應用程式組態檔的區段。  
  
> [!IMPORTANT]
>  使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼宣告授權管理員中的宣告型存取控制 (<xref:System.Security.Claims.ClaimsAuthorizationManager>) 和用來製作授權決策的原則已透過`<identityConfiguration>`參考項目隱含或明確地從`<federationConfiguration>`在本節中的項目。 如需詳細資訊，請參閱**備註**下方[ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。  
  
 `<system.identityModel.services>`一節以<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>類別。 子系的集合`<federationConfiguration>`一節中設定的項目由<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>類別。  
  
## <a name="example"></a>範例  
 下列 XML 示範如何加入`<system.identityModel.services>`組態檔的區段。 您必須先新增區段宣告兩個`<system.identityModel.services>`一節和`<system.identityModel>`區段。 (當您將加入`<system.identityModel.services>`區段中，您應該加入宣告`<system.identityModel>`一節，以確定預設`<identityConfiguration>`可以由執行階段建立區段，如有必要。)已新增區段宣告之後，您可以設定下的聯合的驗證設定`<system.identityModel.services>`項目。  
  
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
