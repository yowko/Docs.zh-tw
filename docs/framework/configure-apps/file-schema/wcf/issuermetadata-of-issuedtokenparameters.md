---
title: "&lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt;
## 語法  
  
```  
  
<issuerMetaData address=String"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|address|必要項。  指定端點位址的字串。  位址必須是絕對 URI。  預設值為空字串。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<頁首\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|位址標頭的集合。|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|指定在聯合安全性案例中核發之安全性權杖的參數。|  
  
## 請參閱  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [自訂繫結的安全性功能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [自訂繫結安全性](../../../../../docs/framework/wcf/samples/custom-binding-security.md)