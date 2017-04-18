---
title: "&lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt;
指定安全對話服務的設定。  
  
## 語法  
  
```  
  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`securityStateEncoderType`|字串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 型別。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
  
## 備註  
 使用此組態項目指定安全性內容權杖 \(SCT\) Cookie 序列化的已知宣告型別清單，以及指定可編碼與確保 Cookie 資訊安全的編碼器。  如需 SCT 的詳細資訊，請參閱<xref:System.ServiceModel.Security.SecureConversationServiceCredential>。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>   
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>   
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>