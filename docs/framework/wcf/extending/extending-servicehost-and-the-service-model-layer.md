---
title: "擴充 ServiceHost 與服務模型層 | Microsoft Docs"
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
  - "擴充服務模型 [WCF]"
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 擴充 ServiceHost 與服務模型層
服務模型層負責從基礎通道提取傳入訊息，將訊息轉譯成應用程式程式碼中的方法叫用，然後將結果傳回給呼叫者。服務模型擴充功能會修改或實作涉及用戶端或發送器功能、自訂行為、訊息與參數攔截與其他擴充性功能的執行或通訊行為與功能。  
  
## 在本節中  
 [擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)  
 說明可攔截與修改用戶端執行階段的介面，以及您可在用戶端應用程式中插入自訂擴充功能的類別。例如，您可以執行自訂用戶端訊息記錄，以及執行自訂訊息序列化等等。  
  
 [擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 說明可攔截與修改服務執行階段的介面，以及您可在服務應用程式中插入自訂擴充功能的類別。例如，您可執行自訂服務記錄、服務端訊息驗證，以及自訂分派等等。  
  
 [可延伸物件](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 描述 5 項可擴充物件以及 <xref:System.ServiceModel.IExtensibleObject%601> 模式。可延伸物件模式是用於以新功能延伸現有的執行階段類別，或將新狀態新增至物件。附加至其中一個可延伸物件的擴充功能會在處理程序中的各種不同階段啟用行為，以存取附加至它們可存取之一般可延伸物件的共用狀態與功能。  
  
 [使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 若要變更在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段的設定值或插入擴充功能，請使用 \[行為\]。WCF 包括控制節流、執行個體以及其他許多服務與作業方面的系統實作行為。此章節說明如何建立您自己的自訂行為，以及如何讓它們供程式設計以及使用組態檔時使用。  
  
 [使用 ServiceHostFactory 擴充裝載](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 說明如何擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=fullName>, <xref:System.ServiceModel.ServiceHost?displayProperty=fullName>，以及使用 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=fullName> 類別自訂主機環境。  
  
## 參考  
  
## 相關章節