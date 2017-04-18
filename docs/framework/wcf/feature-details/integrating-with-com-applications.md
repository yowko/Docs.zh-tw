---
title: "整合 COM 應用程式 | Microsoft Docs"
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
  - "COM [WCF]"
  - "COM [WCF], Windows Communication Foundation 整合"
  - "WCF, COM 整合"
  - "WCF, 重複使用程式碼"
  - "Windows Communication Foundation, COM 整合"
  - "Windows Communication Foundation, 重複使用程式碼"
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 整合 COM 應用程式
可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker，將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務直接整合至現有的程式碼。  服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C\+\+ 6.0。  
  
## 在本節中  
 [整合 COM 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 提供整合處理序主要部分的概觀。  
  
 [HOW TO：註冊和設定服務 Moniker](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 若要在 COM 應用程式內使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker，請以 COM 登錄必要的屬性類型，並以必要的繫結組態設定 COM 應用程式和 Moniker。  
  
 [HOW TO：使用 Windows Communication Foundation 服務 Moniker 且不註冊](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 說明如何取得格式為 Web Services Definition Language \(WSDL\) 文件的合約定義，或如何從 WS\-MetadataExchange 端點取得該定義。  
  
 [HOW TO：使用服務 Moniker 搭配 WSDL 合約](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 描述如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。  
  
 [HOW TO：使用服務 Moniker 搭配中繼資料交換合約](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 描述如何使用指定 Mex 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。  
  
 [HOW TO：指定通道安全性認證](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 支援 `IChannelCredentials` 介面，這個介面提供一系列的替代方法以指定通道認證。  
  
## 參考  
 <xref:System.ServiceModel>  
  
## 請參閱  
 [整合 COM\+ 應用程式](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)