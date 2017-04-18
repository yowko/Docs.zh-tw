---
title: "&lt;wsDualHttpBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;wsDualHttpBinding&gt; 的 &lt;security&gt;
定義 [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)的安全性功能。  
  
## 語法  
  
```  
  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|-   選擇項。  指定套用的安全性類型。  預設值是 `Message`。  此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。|  
  
## Mode 屬性  
  
|值|描述|  
|-------|--------|  
|無|停用安全性。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<訊息\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|定義訊息層級安全性的設定。  此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義 [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) 的所有繫結功能。|  
  
## 備註  
 雙重繫結會向服務公開用戶端的 IP 位址，  用戶端應該使用安全性確保本身只連接其信任的服務。  
  
## 請參閱  
 <xref:System.ServiceModel.WSDualHttpSecurity>   
 <xref:System.ServiceModel.WsDualHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)