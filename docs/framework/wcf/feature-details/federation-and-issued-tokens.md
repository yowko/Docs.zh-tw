---
title: "聯合與發行的權杖 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "聯合 [WCF], 發行的權杖"
  - "發行的權杖 [WCF]"
  - "WCF, 聯合"
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 聯合與發行的權杖
有了 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，您就可以建立與服務進行安全通訊的用戶端，其中實作了 WS\-Federation 和 WS\-Trust 規格。這些規格使用 XML、SOAP 和 Web 服務描述語言 \(WSDL\)，提供跨不同信任領域的驗證和授權。  
  
## 在本節中  
 [聯合](../../../../docs/framework/wcf/feature-details/federation.md)  
 提供聯合的概觀。  
  
 [聯合與信任](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 列出建立聯合服務或用戶端時應注意的設計問題。  
  
 [HOW TO：建立聯合用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 說明以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 建立聯合用戶端的基本概念。  
  
 [HOW TO：設定聯合服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 說明建立聯盟服務的步驟。  
  
 [HOW TO：建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 說明如何設定使用 `WSFederationHttpBinding` 的用戶端和服務。  
  
 [HOW TO：建立安全性權杖服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 說明建立安全性權杖服務的步驟。  
  
 [安全性判斷提示標記語言 \(SAML\) 權杖與宣告](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 說明 Security Assertions Markup Language \(SAML\) 權杖，這是一個可擴充，並且可讓您建立豐富之宣告類型的權杖。  
  
 [HOW TO：設定本機簽發者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 說明如何建立安全性權杖的本機簽發者。  
  
 [HOW TO：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 說明如何停用 `WSFederationHttpBinding` 上的安全工作階段。在建立要求每個用戶端都使用一個工作階段的 Web 伺服陣列時，必須停用安全工作階段。  
  
## 參考  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## 請參閱  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)   
 [自訂權杖](../../../../docs/framework/wcf/extending/custom-tokens.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)