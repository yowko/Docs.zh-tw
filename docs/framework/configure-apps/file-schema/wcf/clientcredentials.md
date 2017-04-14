---
title: "&lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt;
指定用來對服務驗證用戶端的認證。  
  
## 語法  
  
```  
  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`supportInteractive`|布林值，指定互動式使用者是否可以在執行階段選取用戶端認證。  預設值是 `true`。|  
|`type`|字串，指定這個組態項目的型別。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|指定用來對服務驗證用戶端的憑證。  此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。|  
|[\<httpDigest\>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|指定用來對服務驗證用戶端的摘要。  此項目的型別為 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|指定用來對安全性權杖服務 \(STS\) 驗證用戶端的自訂權杖型別。  此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定目前的對等認證。  此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|指定用來對用戶端驗證服務的憑證，並提供設定憑證選項的結構。  當超出服務至用戶端的範圍時，就必須提供此憑證。  此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。|  
|[\<視窗\>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|指定 Windows 認證。  預設為目前執行緒的認證。  此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsClientElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## 備註  
 在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。  在用戶端必須以服務的憑證保護傳遞給服務的訊息時，這個組態區段也可以用來指定服務憑證。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)