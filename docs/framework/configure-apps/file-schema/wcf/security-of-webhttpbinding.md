---
title: "&lt;webHttpBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;webHttpBinding&gt; 的 &lt;security&gt;
指定以 [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 設定之端點的安全性需求。  
  
## 語法  
  
```  
  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|模式|指定端點是否使用傳輸層級安全性或不使用安全性。  預設為 `None`。  此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。|  
  
## Mode 屬性  
  
|值|描述|  
|-------|--------|  
|無|停用安全性。|  
|Transport|系統會使用 HTTPS 來提供安全性。  而服務必須使用 SSL 憑證來設定。  HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。  用戶端驗證是透過 [\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md) 的 `ClientCredentialType` 屬性來控制。|  
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性，  但會提供 HTTP 架構的用戶端驗證。  請謹慎使用這個模式，  它應使用在以其他方式 \(如 IPSec\) 提供傳輸安全性，且 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 基礎結構只提供用戶端驗證的環境中。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|定義傳輸安全性設定。  這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|繫結項目，用於設定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web 服務的端點，這些服務則會回應 HTTP 要求，而不是 SOAP 訊息。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>   
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.WebHttpSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [選取認證類型](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)   
 [WCF Web HTTP 程式設計模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)