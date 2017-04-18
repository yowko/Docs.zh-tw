---
title: "&lt;netPeerBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# &lt;netPeerBinding&gt; 的 &lt;security&gt;
定義 [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md) 的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。  
  
## 語法  
  
```  
  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|選擇項。  指定此繫結所設定之對等要使用的安全性類型。  預設值是 `Message`。  此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## mode 屬性  
  
|值|描述|  
|-------|--------|  
|訊息|SOAP 安全性提供驗證、完整性和機密性。|  
|無|停用安全性。|  
|Transport|系統會使用 HTTPS 來提供安全性。|  
|TransportWithMessageCredential|HTTPS 提供驗證和機密性。  SOAP 訊息提供豐富的認證類型。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。  此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義 [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md) 的所有繫結功能。|  
  
## 備註  
 安全性可以是訊息特定或傳輸特定。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>   
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.PeerSecuritySettings>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [選取認證類型](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)