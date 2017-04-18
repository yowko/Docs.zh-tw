---
title: "&lt;claimsAuthorizationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;claimsAuthorizationManager&gt;
註冊連入宣告的宣告授權管理員。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子項目  
 如果沒有任何`type`屬性，或是否`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別， `<claimsAuthorizationManager>`不致於項目的子項目。 然而，類別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>可以定義組態項目子系。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
  
## 備註  
 透過提供的預設行為<xref:System.Security.Claims.ClaimsAuthorizationManager>類別永遠會授與連入宣告。  如果沒有`type`指定屬性或 if `type`屬性會指定<xref:System.Security.Claims.ClaimsAuthorizationManager>類別， `<claimsAuthorizationManager>`項目並不產生任何子項目。  您可以指定`type`屬性，以註冊的型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別來實作自訂行為。  在衍生的類別可支援透過子項目的`<claimsAuthorizationManager>`項目，藉由覆寫<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>方法來處理這些項目。  子項目所定義的結構描述是由類別的設計工具。  
  
> [!IMPORTANT]
>  當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別來提供您的程式碼所參考的識別身份組態中的宣告式存取控制`<federationConfiguration>`元素設定了宣告授權管理員和原則，用來製作授權決策。  都是如此，即使是在不是被動 Web 的案例，例如 \[Windows 通訊資格應用程式\] 或 \[不是以 Web 為基礎的應用程式的案例。  如果應用程式不是被動的 Web 應用程式中， `<claimsAuthorizationManager>`項目 \(與其子原則項目，如果有的話\) 的參考的識別設定所套用的唯一設定。  會忽略所有其他設定。  如需詳細資訊，請參閱 [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目。  
  
 這個項目設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=fullName>屬性。  
  
## 範例  
 下列 XML 程式碼會顯示宣告的授權的組態管理員，它會實作的原則組成資源動作 」 配對的每一種指定之宣告的要求者必須擁有在資源上執行的動作，則為 true 的組合。  實作宣告授權管理員能夠使用這項原則的程式碼位於`ClaimsBasedAuthorization`範例。  
  
```  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```