---
title: "&lt;nameClaimType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;nameClaimType&gt;
設定指定 <xref:System.Security.Principal.IIdentity.Name%2A> 屬性的需求類型。  要求型別是用來搜尋 <xref:System.Security.Claims.ClaimsIdentity> 物件集合的 <xref:System.Security.Claims.Claim> 這個語彙基元的處理常式 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 方法傳回的。  比對要求的值會設定為，則從這個語彙基元的處理常式會產生的 <xref:System.Security.Principal.IIdentity> 的名稱。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|值|指定 URI 表示所要求的型別。 <xref:System.Security.Principal.IIdentity.Name%2A> 屬性使用的字串。  必要項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 這些類別的其中一個衍生的類別提供設定。|  
  
## 備註  
 `<nameClaimType>` 項目集合 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> 屬性，當 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 物件從設定來初始化。  
  
## 範例  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>