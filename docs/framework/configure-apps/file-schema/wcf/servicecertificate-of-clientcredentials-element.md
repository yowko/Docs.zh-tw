---
title: "&lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目
指定對用戶端驗證服務時所使用的憑證。  
  
## 語法  
  
```  
  
<serviceCertificate />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<defaultCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。|  
|[\<scopedCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|表示特定服務 \(範圍服務\) 為驗證所提供之 X.509 憑證的集合。  這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。|  
|[\<驗證\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|為用戶端使用的服務憑證指定驗證行為。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用戶端用來對服務驗證本身的認證。|  
  
## 備註  
 這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。  它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。  
  
 `serviceCertificate` 項目的屬性與 [\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) 的屬性相同。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>   
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)