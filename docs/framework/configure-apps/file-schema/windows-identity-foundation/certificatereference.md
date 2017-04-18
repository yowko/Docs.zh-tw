---
title: "&lt;certificateReference&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateReference&gt;
指定用來找出並驗證 x.509 憑證存放區中的設定。  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName=”AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher”  
        storeLocation=”CurrentUser||LocalMachine”  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|storeName|X.509 憑證存放區的名稱。  預設值是"My"。  選擇項。|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定的 X.509 憑證存放區位置。  預設值為"LocalMachine"。  選擇項。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定要執行的搜尋種類。  預設為"FindBySubjectDistinguishedName"。  選擇項。|  
|findValue|要在 X.509 憑證存放區內搜尋的值。  選擇項。|  
|isChainIncluded|指定是否應該使用的憑證鏈結中執行驗證。  預設值是 「 真正 」 ； 藉由使用的憑證鏈結，會執行驗證。  選擇項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|設定憑證，用來加密和解密語彙基元。|  
  
## 備註  
 `<certificateReference>`項目會指定用來找出並驗證 x.509 憑證存放區中的設定。  當已指定為子項目， `<serviceCertficate>`項目，它會指定 X.509 憑證，用來加密和解密語彙基元的位置\] 與 \[驗證設定。  `<certificateReference>`項目會以<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。