---
title: "&lt;system.identityModel.services&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;system.identityModel.services&gt;
使用 「 WS\-同盟通訊協定進行驗證的組態區段。  
  
 \<system.identityModel.services\>  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 None  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) HTTP 模組。|  
  
### 父項目  
 None  
  
## 備註  
 新增`<system.identityModel.services>`一節，以提供設定的 SAM 和 WSFAM 應用程式組態檔。  
  
> [!IMPORTANT]
>  使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供在程式碼，宣告的授權管理員中的宣告式存取控制 \(<xref:System.Security.Claims.ClaimsAuthorizationManager>\)，且用來製作授權決策的原則設定透過`<identityConfiguration>`隱含或明確地從參考的項目`<federationConfiguration>`在這一節中的項目。  如需詳細資訊，請參閱**註解**下[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。  
  
 `<system.identityModel.services>`區段會顯示由<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>類別。  子系的集合`<federationConfiguration>`一節中所設定的項目會以<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>類別。  
  
## 範例  
 下列 XML 程式碼顯示如何將`<system.identityModel.services>`一節，以組態檔。  您必須先新增區段宣告兩個`<system.identityModel.services>`一節並`<system.identityModel>`區段。  \(當您將加入`<system.identityModel.services>` \] 區段中，您應該加入宣告`<system.identityModel>`一節，以確保預設的`<identityConfiguration>`可以由執行階段建立區段，如有必要。\)加入區段宣告之後，您可以設定聯盟的驗證設定，在`<system.identityModel.services>`項目。  
  
```  
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