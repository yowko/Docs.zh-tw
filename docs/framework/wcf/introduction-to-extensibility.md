---
title: "擴充性簡介"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3f045fd35ef57be51c10d7948275899c1ae4f01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-extensibility"></a>擴充性簡介
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式模型是設計用來解決任何分散式應用程式大部分的通訊要求， 但是一定有預設應用程式模型和系統提供的實作所不支援的情況。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 擴充性模型是用來讓您能修改每個層級的系統行為，甚至到取代整個系統模型，所以可以支援自訂的情況。 本主題會概述各種擴充區域，並指向每個擴充區域的詳細資訊。  
  
## <a name="areas-to-extend"></a>要擴充的區域  
 您可以擴充：  
  
-   應用程式執行階段， 這會擴充應用程式的訊息分派和處理功能。 這個區域也包含擴充安全性系統、中繼資料系統、序列化系統，以及連接應用程式與基礎通道系統的繫結和繫結項目。  
  
-   通道和通道執行階段， 這會擴充在訊息層級上運作的系統，提供通訊協定、傳輸和編碼支援。  
  
-   主機執行階段， 這會擴充裝載應用程式定義域與通道和應用程式執行階段之間的關係。  
  
### <a name="extending-the-application-runtime"></a>擴充應用程式執行階段  
 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式中，用於對應通道的訊息和用於應用程式本身的訊息之間有不同之處。 通道訊息支援某些與通道相關的功能，例如建立安全對話或建立可靠的工作階段。 這些訊息不適用於應用程式執行階段，在使用應用程式層之前，就會先處理訊息。  
  
 應用程式訊息包含您或您的客戶所建立，並且用於用戶端或服務作業的資料。 視您的需要而定，這些訊息適用於形式為訊息或物件的應用程式層級擴充系統。  
  
 所有訊息都會通過通道系統，但是只有應用程式訊息會從通道系統傳遞至應用程式。 若要建立新的通道層級功能，您必須擴充通道系統。 若要建立新的應用程式層級功能，您必須擴充服務或用戶端執行階段 (分別是發送器和通道處理站)。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]擴充應用程式執行階段，請參閱[擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)。  
  
#### <a name="extending-security"></a>擴充安全性  
 若要建置自訂安全性機制，例如權杖和認證，您必須擴充安全性系統。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][擴充安全性](../../../docs/framework/wcf/extending/extending-security.md)。  
  
#### <a name="extending-metadata"></a>擴充中繼資料  
 若要以不同於預設的方式公開中繼資料，您必須擴充中繼資料系統。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][擴充中繼資料系統](../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。  
  
#### <a name="extending-serialization"></a>擴充序列化  
 若要建置自訂編碼器、提供資料代理或其他涉及自訂傳輸資料的工作，您必須擴充序列化系統。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][擴充編碼器與序列化程式](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)。  
  
#### <a name="extending-bindings"></a>擴充繫結  
 若要將傳輸或通訊協定通道與應用程式層產生關聯，您必須擴充繫結系統。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][擴充繫結](../../../docs/framework/wcf/extending/extending-bindings.md)。  
  
### <a name="extending-the-channel-system"></a>擴充通道系統  
 若要建立通道支援自訂傳輸或通訊協定功能，請參閱[擴充通道層](../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
### <a name="extending-the-service-hosting-system"></a>擴充服務裝載系統  
 若要修改服務範圍的應用程式模型，您必須擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 類別。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][擴充 ServiceHost 與服務模型層](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)。  
  
 若要修改裝載應用程式定義域與服務主機之間的關係，您必須擴充 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> 類別。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][使用 ServiceHostFactory 擴充裝載](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)。  
  
## <a name="see-also"></a>請參閱  
 [擴充 WCF](../../../docs/framework/wcf/extending/extending-wcf.md)
