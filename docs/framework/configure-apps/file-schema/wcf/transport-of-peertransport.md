---
title: "&lt;peerTransport&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;peerTransport&gt; 的 &lt;transport&gt;
指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。  
  
## 語法  
  
```  
  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|credentialType|選擇項。  指定認證的類型，用於驗證對等傳輸所傳送的訊息。  此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。|  
  
## credentialType 屬性  
  
|值|描述|  
|-------|--------|  
|憑證|對等通道傳輸的驗證作業需要 X509 憑證。|  
|密碼|對等通道傳輸的驗證作業需要正確的密碼。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|定義對等傳輸的安全性設定。|  
  
## 備註  
 這個項目只有在 [\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) 的模式屬性設為 `Transport` 或 `TransportWithMessageCredential` 時才會設定。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>   
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>   
 <xref:System.ServiceModel.PeerTransportSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [傳輸安全性](../../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)