---
title: "&lt;securityTokenHandlers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;securityTokenHandlers&gt;
指定登錄與端點的安全性語彙基元處理常式的集合。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|指定語彙基元的處理常式集合的名稱。  由架構所識別的唯一值是"ActAs"和"OnBehalfOf"。  如果其中一種這些名稱與指定語彙基元的處理常式集合，分別處理 ActAs 或 OnBehalfOf 語彙基元時，將會使用集合。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|加入語彙基元的處理常式集合中的安全性語彙基元的處理常式。|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|清除所有的安全性語彙基元處理常式，從語彙基元的處理常式集合。|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|移除語彙基元的處理常式集合中的安全性語彙基元的處理常式。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供集合的語彙基元的處理常式的組態。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
  
## 備註  
 服務設定中，您可以指定一或多個項目的安全性語彙基元的處理常式的具名的集合。  您可以使用指定的集合名稱`name`屬性。  架構會處理的唯一名稱是"ActAs"和"OnBehalfOf"。  如果存在這些集合中的處理常式，它們由安全性權杖服務 \(STS\) 而不是預設處理常式的處理時`ActAs`和`OnBehalfOf`語彙基元。  
  
 根據預設，集合會填入下列處理常式型別： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，以及<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。  您可修改該集合，藉由使用`<add>`， `<remove>`，以及`<clear>`項目。  您必須確定只有單一的處理常式特殊型別存在集合中。  比方說，如果您衍生處理常式與<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別，可能是您的處理常式或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>可能設定在單一的集合，但不可同時擁有兩者。  
  
 使用`<securityTokenHandlerConfiguration>`項目集合中指定的處理常式的組態設定。  透過這個項目指定的設定會覆寫指定於透過服務的[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。  某些 \(包括數個內建的處理常式型別\) 的處理常式可支援額外的設定，子項目，透過`<add>`項目。  在處理常式中指定的設定會覆寫集合或該服務上所指定的對等設定。