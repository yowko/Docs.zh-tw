---
title: "&lt;netTcpBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# &lt;netTcpBinding&gt; 的 &lt;security&gt;
定義繫結的安全性設定。  
  
## 語法  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|選擇項。  指定套用的安全性類型。  有效值如下所示。  預設值是 `Transport`。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## mode 屬性  
  
|值|描述|  
|-------|--------|  
|無|停用安全性。|  
|Transport|使用 TLS over TCP 或 SPNego 來提供傳輸安全性。  服務必須使用 SSL 憑證來設定。  可使用這個模式控制保護層級。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。  根據預設，SOAP 本文會經過加密與簽署。  這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。  每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
|TransportWithMessageCredential|傳輸安全性會與訊息安全性結合在一起。  傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。  SOAP 訊息安全性提供用戶端驗證。  根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<傳輸\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|定義傳輸的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。|  
|[\<訊息\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|定義訊息的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|繫結|[\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)的繫結項目。|  
  
## 備註  
 每個標準繫結提供了控制傳輸安全性需求的參數。  這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。  根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。  
  
 由 Windows Communication Foundation \(WCF\) 提供的系統提供繫結，是設計成符合某些最常見案例需求的一組繫結。  這些每個繫結都允許特定目標案例的安全性需求規格。  
  
 這個組態項目會提供 `netTcpBinding` 的安全性規格。  這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。  根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP \(供訊息傳遞使用\)、Windows 安全性 \(供訊息安全性與驗證使用\)、WS\-ReliableMessaging \(提升可靠性\) 以及二進位訊息編碼。  
  
## 請參閱  
 <xref:System.ServiceModel.NetTcpSecurity>   
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)