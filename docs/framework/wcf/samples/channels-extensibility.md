---
title: "通道擴充性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 通道擴充性
本節包含示範自訂通道的範例。  
  
## 在本節中  
 [本機通道](../../../../docs/framework/wcf/samples/local-channel.md)  
 示範邏輯通道，也就是在相同的應用程式網域中，用於通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳輸通道。  
  
 [可靠的安全設定檔](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 示範如何撰寫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與可靠的安全設定檔 \(Reliable Secure Profile，RSP\)。  
  
 [自訂通道發送器](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。  
  
 [區塊處理通道](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 示範如何限制使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 緩衝大型訊息所使用的記憶體數量。  
  
 [HTTP 要求認可通道](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 示範變更單向訊息模式的層次通道。  
  
 [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 示範如何將自訂通訊協定通道建置成在工作階段管理使用 HTTP Cookie。  
  
 [自訂訊息攔截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。