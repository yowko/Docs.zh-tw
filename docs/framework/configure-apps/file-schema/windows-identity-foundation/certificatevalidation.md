---
title: "&lt;certificateValidation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateValidation&gt;
控制語彙基元的處理常式用來驗證憑證的設定。  如果它自己的驗證程式設定特定的處理常式，則會覆寫這些設定。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證的驗證模式。  預設值為"PeerOrChainTrust"。  若要指定自訂驗證程式，請將這個屬性為 \[自訂\] 設定，指定使用驗證程式[\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)項目。  選擇項。|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> ，指定要使用的 X.509 憑證的撤銷模式的值。  預設值是 「 線上 」。  選擇項。|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation>指定的 X.509 憑證存放區的值。  預設值為"LocalMachine"。  選擇項。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|指定為憑證驗證的自訂型別。  只有當使用這個型別`certificateValidationMode`屬性的[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設為 \[自訂\]。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供設定一系列安全性語彙基元的處理常式。|  
  
## 備註  
 A `<certificateValidation>`項目，請指定在服務層級下`<identityConfiguration>`項目或安全性語彙基元的處理常式集合下的層級上`<securityTokenHandlerConfiguration>`項目。  在 \[語彙基元的處理常式集合的設定會覆寫所指定的服務。  某些語彙基元的處理常式可讓您在組態中指定憑證驗證設定。  設定個別語彙基元的處理常式覆寫以上所指的服務層級與安全性語彙基元的處理常式集合。  
  
## 範例  
  
```  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```