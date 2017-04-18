---
title: "&lt;SSL 資料流安全性&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;SSL 資料流安全性&gt;
代表使用 SSL 資料流支援通道安全性的自訂繫結元素。  
  
## 語法  
  
```  
  
<sslStreamSecurity requireClientCertificate="Boolean"  
      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|requireClientCertificate|布林值，指定這個繫結是否需要用戶端憑證。  預設為 `false`。|  
|sslProtocols|SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。  預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)