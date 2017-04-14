---
title: "&lt;knownCertificates&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# &lt;knownCertificates&gt;
表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 \(STS\) 發行的安全性認證。  
  
## 語法  
  
```  
  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|將 X.509 憑證加入至集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|指定發行為服務認證的權杖。|  
  
## 備註  
 發行之權杖的情況有三個階段。  在第一個階段中，用戶端會嘗試存取稱為「*安全權杖服務*」\(Secure Token Service\) 的服務。  此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 \(SAML\) 權杖。  用戶端接著會以權杖傳回服務。  此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。  若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。  
  
 [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 項目是任何此類安全權杖服務憑證的存放庫。  若要加入憑證，請使用 [\<knownCertificates\> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。  為每個憑證插入 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)，如下列範例所示。  
  
```  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 根據預設，必須從安全權杖服務取得憑證。  這些「已知的」憑證可確保只有合法的用戶端可以存取服務。  
  
 若要檢視將由聯合服務驗證之用戶端的必要條件，以及使用此組態項目的詳細資訊，請參閱 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  如需聯合案例的詳細資訊，請參閱[聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
 如需示範如何在組態中填入集合的範例，請參閱 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)   
 [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)