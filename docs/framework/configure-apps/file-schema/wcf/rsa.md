---
title: "&lt;rsa&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;rsa&gt;
使用這個身分識別連接至端點的安全 WCF 用戶端，將確認伺服器提供的宣告是否包含用來建構這個身分識別之 RSA 公開金鑰的宣告。  
  
## 語法  
  
```  
  
<rsa value = "String" />  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|value|選擇性字串。  在用戶端上要比對的 RSA 公開金鑰值。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## 備註  
 RSA 檢查可讓您根據其 RSA 金鑰或所產生之您自己的 RSA 金鑰值，特別將驗證限制為單一憑證。  如此，若 RSA 金鑰值變更了，特定 RSA 金鑰隨即達成更嚴格的驗證，但該服務便無法和現有用戶端運作。  
  
 如需使用身分識別對用戶端服務進行驗證的詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## 範例  
 下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的公開金鑰值。  
  
```  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.RsaEndpointIdentity>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)