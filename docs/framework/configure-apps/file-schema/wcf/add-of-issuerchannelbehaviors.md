---
title: "&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;
新增與 STS 通訊時要使用的端點行為。  
  
> [!NOTE]
>  如果有任何端點行為包含 [\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 項目，則會擲回例外狀況。  
  
## 語法  
  
```  
  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|issuerAddress|要與其進行通訊之安全性權杖簽發者的 URI。|  
|behaviorConfiguration|相同組態檔中定義之端點行為的名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|包含要在與指定安全性權杖服務通訊時使用的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端端點行為集合。|  
  
## 備註  
 `issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。  `behaviorConfiguration` 會指向端點行為，而應用程式會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 建立的通道中使用該行為取得 Security Token Service 發出的權杖。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>   
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [HOW TO：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)