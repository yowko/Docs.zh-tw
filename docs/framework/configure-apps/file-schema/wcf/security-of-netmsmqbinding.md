---
title: "&lt;netMsmqBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;netMsmqBinding&gt; 的 &lt;security&gt;
定義 MSMQ 繫結的安全性設定。  它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。  
  
## 語法  
  
```  
  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|指定負責控制完整性、機密性和驗證的安全性類型。  有效值包括以下的值：<br /><br /> -   None：這會停用安全性。<br />-   Transport：由傳輸提供保護和驗證。  這會套用在兩個佇列管理員之間的訊息安全性。  應用程式和佇列管理員之間沒有提供安全性。  現有 Msmq 應用程式在功能上相當於這個安全性模式類型。<br />-   Message：指定端對端應用程式安全性。  在傳輸層沒有提供安全性。  這與其他標準繫結提供的安全性類似。<br />-   Both：在傳輸和 SOAP 傳訊層提供安全性。  這兩個層級需要相同的認證。<br /><br /> 預設值為 Transport。  此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<訊息\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|定義 SOAP 訊息安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|定義 MSMQ 傳輸的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|繫結|[\<netMsmqBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) 的繫結項目|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>   
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)   
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)