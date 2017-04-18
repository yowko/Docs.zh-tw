---
title: "&lt;knownCertificates&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;knownCertificates&gt; 的 &lt;add&gt;
將 X.509 憑證加入至已知憑證的集合。  
  
## 語法  
  
```  
  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|findValue|字串。  要搜尋的值。|  
|storeLocation|列舉。  搜尋兩個存放位置中的一個。|  
|storeName|列舉。  搜尋的其中一個系統存放區。|  
|x509FindType|列舉。  要搜尋的其中一個憑證欄位。|  
  
## findValue 屬性  
  
|值|描述|  
|-------|--------|  
|String|這個值取決於要搜尋的欄位 \(由 X509FindType 屬性指定\)。  例如，如果搜尋指紋，則此值必須是十六進位數字字串。|  
  
## x509FindType 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier。|  
  
## storeLocation 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|CurrentUser 或 LocalMachine。|  
  
## storeName 屬性  
  
|值|描述|  
|-------|--------|  
|列舉|值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|表示 X.509 憑證的集合，這些憑證是由安全性權杖服務 \(STS\) 提供的，可用來驗證安全性權杖。|  
  
## 備註  
 發行之權杖的情況有三個階段。  在第一個階段中，用戶端會嘗試存取稱為「*安全權杖服務*」\(Secure Token Service\) 的服務。  此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 \(SAML\) 權杖。  用戶端接著會以權杖傳回服務。  此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。  若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。  
  
 [\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 項目是任何此類安全權杖服務憑證的存放庫。  若要加入憑證，請使用 [\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。  為每個憑證插入 [\<add\> element \<knownCertificates\> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)，如下列範例所示。  
  
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
  
## 範例  
 下列範例會將憑證加入至任何 STS 憑證的儲存機制。  
  
```  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>   
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>   
 [\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)