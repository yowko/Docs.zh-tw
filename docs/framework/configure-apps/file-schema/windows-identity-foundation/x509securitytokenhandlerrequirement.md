---
title: "&lt;x509SecurityTokenHandlerRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# &lt;x509SecurityTokenHandlerRequirement&gt;
提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 類別或衍生類別 \(Derived Class\) 提供選擇性的設定。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|certificateValidationMode|指定驗證模式的 X.509 憑證 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 使用的值。  預設值為「PeerOrChainTrust」。|  
|mapToWindows|指定這個語彙基元的處理常式會使用傳入的 UPN 要求時，是否應將這個驗證語彙基元到 Windows 帳戶。  預設值為「false」。|  
|revocationMode|指定撤銷模式為 X.509 憑證所使用的 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  預設值為「線上」。|  
|trustedStoreLocation|指定 X.509 憑證存放區的 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值。  預設值為「LocalMachine」。|  
|certificateValidator|從 <xref:System.IdentityModel.Selectors.X509CertificateValidator>衍生自類別的自訂型別。  如果 `certificateValidationMode` 屬性為「Custom」，這個型別的執行個體為發行者憑證進行驗證。|  
  
### 子項目  
 None  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|將指定的安全性語彙基元的處理常式加入至指定的處理常式集合。|  
  
## 範例  
  
```  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```