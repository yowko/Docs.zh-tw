---
title: "擴充性簡介 | Microsoft Docs"
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
  - "擴充性 [WCF]"
  - "WCF [WCF], 擴充性"
  - "Windows Communication Foundation [WCF], 擴充性"
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 擴充性簡介
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式模型是設計用來解決任何分散式應用程式大部分的通訊要求，  但是一定有預設應用程式模型和系統提供的實作所不支援的情況。  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 擴充性模型是用來讓您能修改每個層級的系統行為，甚至到取代整個系統模型，所以可以支援自訂的情況。  本主題會概述各種擴充區域，並指向每個擴充區域的詳細資訊。  
  
## 要擴充的區域  
 您可以擴充：  
  
-   應用程式執行階段，  這會擴充應用程式的訊息分派和處理功能。  這個區域也包含擴充安全性系統、中繼資料系統、序列化系統，以及連接應用程式與基礎通道系統的繫結和繫結項目。  
  
-   通道和通道執行階段，  這會擴充在訊息層級上運作的系統，提供通訊協定、傳輸和編碼支援。  
  
-   主機執行階段，  這會擴充裝載應用程式定義域與通道和應用程式執行階段之間的關係。  
  
### 擴充應用程式執行階段  
 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式中，用於對應通道的訊息和用於應用程式本身的訊息之間有不同之處。  通道訊息支援某些與通道相關的功能，例如建立安全對話或建立可靠的工作階段。  這些訊息不適用於應用程式執行階段，在使用應用程式層之前，就會先處理訊息。  
  
 應用程式訊息包含您或您的客戶所建立，並且用於用戶端或服務作業的資料。  視您的需要而定，這些訊息適用於形式為訊息或物件的應用程式層級擴充系統。  
  
 所有訊息都會通過通道系統，但是只有應用程式訊息會從通道系統傳遞至應用程式。  若要建立新的通道層級功能，您必須擴充通道系統。  若要建立新的應用程式層級功能，您必須擴充服務或用戶端執行階段 \(分別是發送器和通道處理站\)。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]擴充應用程式執行階段的詳細資訊，請參閱 [擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)。  
  
#### 擴充安全性  
 若要建置自訂安全性機制，例如權杖和認證，您必須擴充安全性系統。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [擴充安全性](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### 擴充中繼資料  
 若要以不同於預設的方式公開中繼資料，您必須擴充中繼資料系統。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [擴充中繼資料系統](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### 擴充序列化  
 若要建置自訂編碼器、提供資料代理或其他涉及自訂傳輸資料的工作，您必須擴充序列化系統。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [擴充編碼器與序列化程式](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### 擴充繫結  
 若要將傳輸或通訊協定通道與應用程式層產生關聯，您必須擴充繫結系統。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [擴充繫結](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### 擴充通道系統  
 若要建立支援自訂傳輸或通訊協定功能的通道，請參閱[擴充通道層](../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
### 擴充服務裝載系統  
 若要修改服務範圍的應用程式模型，您必須擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=fullName> 類別。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 若要修改裝載應用程式定義域與服務主機之間的關係，您必須擴充 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=fullName> 類別。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [使用 ServiceHostFactory 擴充裝載](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## 請參閱  
 [延伸 WCF](../../../docs/framework/wcf/extending/extending-wcf.md)