---
title: "&lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt;
指定發行為服務認證的自訂權杖。  
  
## 語法  
  
```  
  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`allowedAudienceUris`|取得目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣該 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。  如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>。|  
|`allowUntrustedRsaIssuers`|布林值，指定是否允許使用未受信任的 RSA 憑證簽發者。<br /><br /> 憑證是由憑證授權單位 \(CA\) 簽署，以確認真實性。  未受信任的簽發者，是指未指定為可信任進行簽署憑證的 CA。|  
|`audienceUriMode`|取得值，這個值會指定是否應驗證 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖的 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>。  這個值的型別為 <xref:System.IdentityModel.Selectors.AudienceUriMode>。  如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>。|  
|`certificateValidationMode`|設定憑證驗證模式。  <xref:System.ServiceModel.Security.X509CertificateValidationMode> 的其中一個有效值。  如果設定為 `Custom`，也必須提供 `customCertificateValidator`。  預設為 `ChainTrust`。|  
|`customCertificateValidatorType`|選擇性字串。  用來驗證自訂型別的型別和組件。  當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。|  
|`revocationMode`|設定撤銷模式，這個模式會指定是否進行撤銷檢查，並且指定以線上或離線的方式執行。  此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。|  
|`samlSerializer`|選用性字串屬性，指定用於服務認證之 SamlSerializer 的型別。  預設為空字串。|  
|`trustedStoreLocation`|選擇性列舉。  兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|`knownCertificates`|指定 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 項目的集合，這個集合會指定服務認證的受信任簽發者。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 備註  
 發行之權杖的情況有三個階段。  在第一個階段中，用戶端會嘗試存取稱為「*安全權杖服務*」\(Secure Token Service\) 的服務。  此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 \(SAML\) 權杖。  用戶端接著會以權杖傳回服務。  此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。  若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。  
  
 這個項目是任何此類安全權杖服務憑證的存放庫。  若要加入憑證，請使用 [\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。  為每個憑證插入 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)，如下列範例所示。  
  
```  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 根據預設，必須從安全權杖服務取得憑證。  這些「已知的」憑證可確保只有合法的用戶端可以存取服務。  
  
 如需使用此組態項目的詳細資訊，請參閱 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [HOW TO：設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)