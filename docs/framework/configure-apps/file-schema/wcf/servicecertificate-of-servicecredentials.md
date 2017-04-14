---
title: "&lt;serviceCredentials&gt; 的 &lt;serviceCertificate&gt;  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;serviceCredentials&gt; 的 &lt;serviceCertificate&gt; 
指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。  
  
## 語法  
  
```  
  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。  屬性所包含的型別必須滿足指定之 X509FindType 的需求。  預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。  有效值包括以下的值：<br /><br /> -   LocalMachine：指派給本機電腦的憑證存放區。<br />-   CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。  有效值包括以下的值：<br /><br /> -   AddressBook：其他使用者的憑證存放區。<br />-   AuthRoot：協力廠商憑證授權單位 \(CA\) 的憑證存放區。<br />-   CertificatAuthority：中繼憑證授權單位 \(CA\) 的憑證存放區。<br />-   Disallowed：已撤銷之憑證的憑證存放區。<br />-   My：個人憑證的憑證存放區。<br />-   Root：信任之根憑證授權單位 \(CA\) 的憑證存放區。<br />-   TrustedPeople：直接信任之人員和資源的憑證存放區。<br />-   TrustedPublisher：直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`X509FindType`|定義要執行之 X.509 搜尋的類型。  有效值包括以下的值：<br /><br /> -   FindByThumbprint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 備註  
 使用此項目指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。  如果您使用的是會定期更新的憑證，則其指紋將會變更。  在這種情況下，請使用主體名稱當成 `X509FindType`，因為憑證可以使用相同的主體名稱重新發出。  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]使用項目的詳細資訊，請參閱 [HOW TO：指定用戶端認證值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>   
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>   
 [HOW TO：指定用戶端認證值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)