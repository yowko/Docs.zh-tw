---
title: "&lt;scopedCertificates&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;scopedCertificates&gt; 的 &lt;add&gt; 項目
將 X.509 憑證加入至範圍憑證的集合。  
  
## 語法  
  
```  
  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|targetUri|字串。  指定與憑證相關聯的服務之 URI。|  
|findValue|字串。  要搜尋的值。|  
|x509FindType|列舉。  要搜尋的其中一個憑證欄位。|  
|storeLocation|列舉。  搜尋兩個存放位置中的一個。|  
|storeName|列舉。  搜尋的其中一個系統存放區。|  
  
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
|[\<scopedCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|表示特定服務 \(範圍服務\) 為驗證所提供之 X.509 憑證的集合。|  
  
## 備註  
 這個項目可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。  在用戶端可以與多重服務 \(終端服務以及中繼安全性權杖服務\) 進行通訊的已核發權杖情況中，這個屬性特別有用。  對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。  
  
 如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。  
  
 如需詳細資訊，請參閱 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)的＜範圍憑證＞一節。  
  
## 範例  
 下列範例會將 X.509 憑證新增至集合。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>   
 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)