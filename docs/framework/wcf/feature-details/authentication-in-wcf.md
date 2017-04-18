---
title: "WCF 的驗證 | Microsoft Docs"
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
  - "驗證 [WCF]"
  - "安全性 [WCF], 驗證"
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WCF 的驗證
下列主題說明 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中提供驗證的各種不同機制，例如，Windows 驗證、X.509 憑證以及使用者名稱與密碼。  
  
## 在本節中  
 [HOW TO：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱\/密碼組合之資料庫，以及供授權的使用者角色。這個主題會說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何能使用相同的資料庫對使用者驗證與授權。  
  
 [HOW TO：使用自訂使用者名稱與密碼驗證程式](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 示範如何整合自訂使用者名稱與密碼驗證程式。  
  
 [服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 作為額外的保護，用戶端可指定預期的服務「*識別*」\(identity\) 以驗證服務。若預期識別與服務傳回的識別不符，則驗證失敗。  
  
 [安全性交涉與逾時](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 屬性。  
  
 [偵錯 Windows 驗證錯誤](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 焦點放在使用 Windows 驗證時，經常遇見的問題。  
  
## 參考  
 <xref:System.ServiceModel>  
  
## 相關章節  
 [常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## 請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)