---
title: "&lt;windowsStreamSecurity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;windowsStreamSecurity&gt;
指定自訂繫結的 Windows 資料流安全性設定。  
  
## 語法  
  
```  
  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|protectionLevel|定義訊息層級安全性。  簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。  加密會提供傳輸期間的資料層級隱私權。  有效值包括以下的值：<br /><br /> -   None：沒有任何保護。<br />-   Sign：簽署訊息。<br />-   EncryptAndSign：簽署和加密訊息。<br /><br /> 預設為 EncryptAndSign。<br /><br /> 此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 備註  
 TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。  具體來說，WCF 會提供安全性升級。  此傳輸安全性的組態是由此組態項目和 [\<SSL 資料流安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 所封裝，而此組態可進行設定並新增至自訂繫結。  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)