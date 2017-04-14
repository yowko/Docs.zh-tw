---
title: "&lt;samlSecurityTokenRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;samlSecurityTokenRequirement&gt;
提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 這些類別的其中一個衍生的類別提供設定。  表示由 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 類別。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
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
|mapToWindows|指定這個語彙基元的處理常式會使用傳入的 UPN 要求時，是否應將這個驗證語彙基元到 Windows 帳戶。  預設值為「false」。|  
|issuerCertificateRevocationMode|指定撤銷模式為 X.509 憑證所使用的 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  預設值為「線上」。|  
|issuerCertificateValidationMode|指定驗證模式的 X.509 憑證 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 使用的值。  預設值為「PeerOrChainTrust」。|  
|issuerCertificateTrustedStoreLocation|指定 X.509 憑證存放區的 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值。  預設值為「LocalMachine」。|  
|issuerCertificateValidator|從 <xref:System.IdentityModel.Selectors.X509CertificateValidator>衍生自類別的自訂型別。  如果 `issuerCertificateValidationMode` 屬性為「Custom」，這個型別的執行個體為發行者憑證進行驗證。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[\<nameClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|設定指定 <xref:System.Security.Principal.IIdentity.Name%2A> 屬性的需求類型。|  
|[\<roleClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|指定可定義動作型別需要在 <xref:System.Security.Claims.ClaimsIdentity> 物件集合語彙基元之處理常式的 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 方法傳回的需求類型。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|將指定的安全性語彙基元的處理常式加入至指定的處理常式集合。|  
  
## 備註  
 `<samlSecurityTokenRequirement>` 元素由物件模型的 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 類別表示和可用來設定 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>的 `SamlSecurityTokenRequirement` 屬性。  
  
## 範例  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```