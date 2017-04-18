---
title: "確保服務與用戶端的安全 | Microsoft Docs"
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
  - "訊息安全性 [WCF]"
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# 確保服務與用戶端的安全
本節所涵蓋的資訊將著重於 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的程式設計安全性。  一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。  這些技術涵蓋了大多數案例中適用於最多使用者的安全性需求，如[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)所示。  如果您使用的案例需要更多功能，請先參閱[自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)，如果這裡找不到解決方案，請再參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。  如果正在建立使用各種宣告的系統 \(或與該系統進行互動\)，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)中的各主題。  
  
## 在本節中  
 [WCF 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 用於確保訊息安全的程式設計模型概觀。  
  
 [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 如何透過傳輸層確保訊息安全的概觀。  
  
 [訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 摘要出在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中使用訊息層級安全性的原因。  
  
 [安全工作階段](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 確保 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段安全時，需要的考量事項討論。  
  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 使用 X.509 憑證時，所需之部分常見工作的說明。  
  
## 參考  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## 相關章節  
 [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## 請參閱  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Windows Server App Fabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)