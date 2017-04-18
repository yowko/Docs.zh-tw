---
title: "&lt;userPrincipalName&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;userPrincipalName&gt;
指定要由用戶端驗證之服務的使用者主要名稱 \(UPN\)。  
  
 如需設定 UPN 的詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## 語法  
  
```  
  
<userPrincipalName value = "String" />  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|value|使用者帳戶名稱 \(有時稱為使用者登入名稱\) 和識別使用者帳戶所在網域的網域名稱。  這是登入 Windows 網域時的標準用法。  格式為：someone@example.com \(如同電子郵件地址\)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## 備註  
 使用這個身分識別連接至端點的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端會在對端點進行 SSPI 驗證時使用 UPN。  
  
## 範例  
 下列組態程式碼會指定要由用戶端驗證之服務的 UPN。  
  
```  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.UpnEndpointIdentity>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)