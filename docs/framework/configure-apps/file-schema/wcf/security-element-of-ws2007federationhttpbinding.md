---
title: "&lt;ws2007FederationHttpBinding&gt; 的 &lt;security&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;ws2007FederationHttpBinding&gt; 的 &lt;security&gt; 項目
定義 [\<ws2007FederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) 項目的安全性設定。  
  
## 語法  
  
```  
  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`mode`|選擇項。  指定套用的安全性類型。  預設值是 `Message`。  此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。|  
  
## mode 屬性  
  
|值|描述|  
|-------|--------|  
|無|傳輸期間的 SOAP 訊息是不安全的。|  
|訊息|完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。  根據預設，本文會經過加密與簽署。  服務必須使用憑證來設定。  用戶端驗證係以安全性權杖服務對用戶端發行的權杖為基礎。|  
|TransportWithMessageCredential|完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。  服務必須使用憑證來設定。  用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<訊息\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|定義訊息層級安全性的設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義 [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) 的所有繫結功能。|  
  
## 請參閱  
 <xref:System.ServiceModel.WSFederationHttpSecurity>   
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>   
 [HOW TO：建立 WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [選取認證類型](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)