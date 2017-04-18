---
title: "自訂繫結的安全性功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# 自訂繫結的安全性功能
您可以使用一種系統提供的繫結來執行常見的安全性工作。不過，如果需要更多控制，您可以依照這些主題中的說明，使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立自訂繫結。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]自訂繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## 在本節中  
 [SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 說明自訂繫結的可能驗證模式。  
  
 [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 說明建立包含安全性項目之自訂繫結的基本步驟。  
  
 [HOW TO：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 說明如何建立指定之驗證模式的安全性項目。  
  
 [HOW TO：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 說明如何在建立聯合服務時停用安全工作階段。  
  
 [HOW TO：啟用訊息重新執行偵測](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 說明如何判斷何時會發生重新執行攻擊。  
  
 [HOW TO：建立支援的認證](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 說明如何為需要認證的服務提供支援認證。  
  
 [HOW TO：設定簽章確認](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 說明在數位簽署訊息時的簽章確認步驟。  
  
 [HOW TO：設定最大時鐘誤差](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 描述如何設定服務與用戶端之間的最大允許時間差異。  
  
 [HOW TO：停用數位簽章加密](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 說明如何從停用數位簽章加密來創造效能優勢。  
  
## 參考  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## 相關章節  
 [了解保護層級](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [確保服務與用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## 請參閱  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)   
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)