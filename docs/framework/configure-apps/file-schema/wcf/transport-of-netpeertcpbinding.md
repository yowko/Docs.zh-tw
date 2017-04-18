---
title: "&lt;netPeerTcpBinding&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;netPeerTcpBinding&gt; 的 &lt;transport&gt;
指定使用 [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)時的傳輸層級安全性設定。  
  
## 語法  
  
```  
  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
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
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|定義 [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)的安全性設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>   
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>   
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.PeerTransportSecuritySettings>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)