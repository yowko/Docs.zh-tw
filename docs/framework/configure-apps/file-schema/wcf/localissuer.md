---
title: "&lt;localIssuer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;localIssuer&gt;
指定要用來取得安全性權杖的本機簽發者位址和繫結。  
  
## 語法  
  
```  
  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|address|必要的字串。  指定本機簽發者的 URI。|  
|繫結|選擇性字串。  系統提供的繫結之一。  如需清單，請參閱 [系統提供的繫結](../../../../../docs/framework/wcf/system-provided-bindings.md)。|  
|bindingConfiguration|選擇性字串。  指定組態檔中的繫結組態。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<識別\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定本機簽發者的身分識別資訊。|  
|[\<頁首\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。  您可以使用 `add` 關鍵字將標頭加入這個集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|指定用來向服務驗證用戶端的自訂權杖。|  
  
## 備註  
 當取得某個安全性權杖服務 \(STS\) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。  當 <xref:System.ServiceModel.WSFederationHttpBinding> 未提供該安全性權杖服務的 URL，或是聯合繫結的簽發者位址為 http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous 或 `null` 時，用戶端的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 通道會使用 `address` 和 `binding` 指定的值與 STS 通訊，以取得已核發的權仗。  如需設定本機簽發者的詳細資訊，請參閱 [HOW TO：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## 範例  
 下列範例會設定 `localIssuer` 項目的 `address`、`binding` 和 `bindingConfiguration` 屬性。  
  
```  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [HOW TO：設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [HOW TO：建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)