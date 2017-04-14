---
title: "&lt;serviceCredentials&gt; 的 &lt;peer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;serviceCredentials&gt; 的 &lt;peer&gt;
指定對等節點的目前認證。  
  
## 語法  
  
```  
  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|指定要用來簽署與加密對等服務之訊息的 X.509 憑證。  .|  
|[\<messageSenderAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|指定訊息寄件者的驗證選項。|  
|[\<peerAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|指定對等服務的驗證選項。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>   
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>   
 <xref:System.ServiceModel.Security.PeerCredential>   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/zh-tw/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/zh-tw/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [確保對等通道應用程式安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)