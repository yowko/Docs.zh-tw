---
title: "&lt;allowedAudienceUris&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;allowedAudienceUris&gt; 的 &lt;add&gt;
加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。  
  
## 語法  
  
```  
  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|allowedAudienceUri|包含目標 URI 的字串，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以該目標 URI 為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<allowedAudienceUris\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。|  
  
## 備註  
 您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 \(Security Token Service，STS\) 的聯合應用程式中使用這個集合。  當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。  如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：  
  
-   將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode>。  
  
-   將 URI 加入此集合，以指定有效的 URI 集合。  
  
 如需詳細資訊，請參閱<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。  
  
 如需使用此組態項目的詳細資訊，請參閱 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>   
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>   
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>   
 [\<allowedAudienceUris\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)   
 [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)