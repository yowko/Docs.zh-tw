---
title: "擴充安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [WCF], 擴充"
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# 擴充安全性
若要建立新的宣告類型和自訂權杖，您可以擴充 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的安全性基礎結構。本章節中的主題會示範如何做到這點。  
  
## 在本節中  
 [Security Architecture](http://msdn.microsoft.com/zh-tw/16593476-d36a-408d-808c-ae6fd483e28f)  
 逐步解說 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性系統的基礎結構。  
  
 [自訂認證與認證驗證](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 說明如何在驗證自訂認證時使用身分識別模型。  
  
 [自訂權杖](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 通常從安全性權杖服務 \(STS\) 發行的權杖是 SAML 權杖。本主題會說明如何建立自訂權杖類型。  
  
 [自訂授權](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 說明如何實作自訂授權。  
  
 [覆寫服務的身分識別以進行驗證](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 說明如何覆寫服務的身分識別來進行驗證。  
  
 [HOW TO：建立自訂用戶端身分識別驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 示範如何驗證自訂端點身分識別。  
  
 [HOW TO：使用個別 X.509 憑證簽署與加密](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 訊息通常會以單一憑證來簽署和加密。本主題會說明如何能在必要時使用兩份憑證。  
  
 [HOW TO：變更 X.509 憑證私密金鑰的密碼編譯提供者](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 說明如何變更用來提供 X.509 憑證之私密金鑰的密碼編譯提供者，以及如何將該提供者整合到 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 架構中。  
  
## 參考  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## 相關章節  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## 請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)