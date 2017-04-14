---
title: "&lt;claimsAuthenticationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;claimsAuthenticationManager&gt;
註冊連入宣告宣告驗證管理的者。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|指定自訂的型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferencess)。|  
  
### 子項目  
 如果沒有任何`type`屬性，或者如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別， `<claimsAuthenticationManager>`不致於項目的子項目。 然而，類別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>可以定義組態項目子系。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
  
## 備註  
 透過提供的預設行為<xref:System.Security.Claims.ClaimsAuthenticationManager>類別會回應連入宣告。  如果沒有`type`指定屬性或`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthenticationManager>類別， `<claimsAuthenticationManager>`不致於項目的子項目。  您可以指定`type`屬性，以註冊的型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別來實作自訂行為。  在衍生的類別可支援透過子項目的`<claimsAuthenticationManager>`項目，藉由覆寫<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>方法來處理這些項目。  子項目所定義的結構描述是由類別的設計工具。  
  
 `<claimsAuthenticationManager>`項目集合<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=fullName>屬性。  
  
## 範例  
  
```  
<system.identityModel>  
    <identityConfiguration name=”MyIdentity”>  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```