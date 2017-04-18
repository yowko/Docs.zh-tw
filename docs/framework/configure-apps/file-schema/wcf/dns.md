---
title: "&lt;dns&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;dns&gt;
指定伺服器的預期身分識別。  如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。  如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。  
  
 如需設定項目值的詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## 語法  
  
```  
  
<dns value = "String" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|value|憑證的 DNS。  DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。  使用者可記住顯示名稱，如 [http:\/\/go.microsoft.com\/fwlink\/?prd\=10929](http://go.microsoft.com/fwlink/?prd=10929) 或 [http:\/\/go.microsoft.com\/fwlink\/?LinkID\=96165](http://go.microsoft.com/fwlink/?LinkID=96165)，比數字位址 \(如 207.46.131.137\) 簡單。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定要由用戶端驗證之服務的身分識別。|  
  
## 範例  
 下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。  
  
```  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.DnsEndpointIdentity>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)