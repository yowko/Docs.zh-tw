---
title: "&lt;clientCredentials&gt; 的 &lt;peer&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;clientCredentials&gt; 的 &lt;peer&gt; 項目
指定驗證對等用戶端時所使用的認證。  
  
## 語法  
  
```  
  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。  .|  
|[\<peerAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|指定對等用戶端的驗證選項。|  
|[\<messageSenderAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|指定訊息寄件者的驗證選項。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## 備註  
 這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。  如需詳細資訊，請參閱[Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)與[確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>   
 <xref:System.ServiceModel.Security.PeerCredential>   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)