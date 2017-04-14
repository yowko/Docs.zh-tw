---
title: "&lt;scopedCertificates&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;scopedCertificates&gt; 項目
表示特定服務 \(範圍服務\) 為驗證所提供之 X.509 憑證的集合。  這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。  
  
## 語法  
  
```  
  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|將 X.509 憑證加入至範圍憑證的集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|指定對用戶端驗證服務時所使用的憑證。|  
  
## 備註  
 這個集合可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。  在用戶端可以與多重服務 \(終端服務以及中繼安全性權杖服務\) 進行通訊的已核發權杖情況中，這個屬性特別有用。  對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。  
  
 如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。  
  
 如需詳細資訊，請參閱 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)的＜範圍憑證＞一節。  
  
## 範例  
 下列範例指定用戶端以 HTTP 通訊協定與網域名稱為 http:\/\/www.contoso.com 的端點通訊時，使用的服務憑證。  
  
```  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>   
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)