---
title: "&lt;clientCertificate&gt; 的 &lt;certificate&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;clientCertificate&gt; 的 &lt;certificate&gt; 項目
指定用來簽署與加密訊息的 X.509 憑證。  
  
## 語法  
  
```  
  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。  屬性所包含的型別必須滿足指定之 X509FindType 的需求。  預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。  有效值包括以下的值：<br /><br /> -   LocalMachine：指派給本機電腦的憑證存放區。<br />-   CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。  有效值包括以下的值：<br /><br /> -   AddressBook：其他使用者的憑證存放區。<br />-   AuthRoot：協力廠商憑證授權單位 \(CA\) 的憑證存放區。<br />-   CertificationAuthority：中繼憑證授權單位 \(CA\) 的憑證存放區。<br />-   Disallowed：已撤銷之憑證的憑證存放區。<br />-   My：個人憑證的憑證存放區。<br />-   Root：信任之根憑證授權單位 \(CA\) 的憑證存放區。<br />-   TrustedPeople：直接信任之人員和資源的憑證存放區。<br />-   TrustedPublisher：直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`X509FindType`|定義要執行之 X.509 搜尋的類型。  有效值包括以下的值：<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## 備註  
 當服務必須具有用戶端的憑證，進而與用戶端安全地進行通訊時，則會使用 `<certificate>` 項目。  這種情況發生在使用雙工通訊模式時。  在較為典型的要求\/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。  然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。  所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。  如需雙工服務的詳細資訊，請參閱 [HOW TO：建立雙工合約](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
## 範例  
 下列程式碼說明如何在 `<authentication>` 項目中尋找適當的 X.509 憑證和自訂驗證類型。  
  
```  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>   
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>   
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [HOW TO：建立使用自訂憑證驗證程式的服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)