---
title: "&lt;servicePrincipalName&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;servicePrincipalName&gt;
由其服務原則名稱 \(SPN\) 指定的服務身分識別。  
  
 如需設定 SPN 的詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## 語法  
  
```  
  
<servicePrincipalName value = "String" />  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|value|用戶端用來唯一識別服務執行個體的名稱。  若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。  若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## 備註  
 使用這個身分識別連接至端點的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端會在對端點進行 SSPI 驗證時使用 SPN。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.SpnEndpointIdentity>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)