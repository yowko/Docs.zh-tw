---
title: "&lt;ws2007HttpBinding&gt; 的 &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;ws2007HttpBinding&gt; 的 &lt;security&gt;
代表搭配 [\<ws2007HttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) 項目使用的安全性設定。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`mode`|-   選擇項。  指定套用的安全性類型。  預設為 `Message`。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## Mode 屬性  
  
|值|描述|  
|-------|--------|  
|`None`|停用安全性。|  
|`Transport`|系統會使用 HTTPS 來提供安全性。  而服務必須使用安全通訊端層 \(SSL\) 憑證來設定。  HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。  用戶端驗證是透過 [\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) 項目的 `ClientCredentials` 屬性來控制。|  
|`Message`|系統會使用 SOAP 訊息安全性來提供安全性。  根據預設，SOAP 本文會經過加密與簽署。  這個模式透過 <xref:System.ServiceModel.Security.SecurityMessageProperty> 提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。  每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
|`TransportWithMessageCredential`|在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。  根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|定義傳輸安全性設定。  這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。  當模式設定為 Transport，才會套用這些設定。|  
|[\<訊息\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|定義訊息的安全性設定。  這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。  當模式設定為 Transport，就不會套用這些設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<ws2007HttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|HTTP 傳輸應用程式的安全繫結。|  
  
## 備註  
 這個項目主要是用來與實作 WS\-\* 規格的服務進行交互操作。  此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 \(SSL\)。  
  
## 請參閱  
 <xref:System.ServiceModel.WSHttpSecurity>   
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)