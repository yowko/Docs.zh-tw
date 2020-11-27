---
title: 擴充性簡介
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 8f4cc490df49a91e448c02fef370ce828536f907
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262719"
---
# <a name="introduction-to-extensibility"></a>擴充性簡介

Windows Communication Foundation (WCF) 應用程式模型是設計用來解決任何分散式應用程式的通訊需求的較大部分。 但是一定有預設應用程式模型和系統提供的實作所不支援的情況。 WCF 擴充性模型的目的是要讓您在每個層級修改系統行為，甚至是取代整個應用程式模型，藉此支援自訂案例。 本主題會概述各種擴充區域，並指向每個擴充區域的詳細資訊。  
  
## <a name="areas-to-extend"></a>要擴充的區域  

 您可以擴充：  
  
- 應用程式執行階段， 這會擴充應用程式的訊息分派和處理功能。 這個區域也包含擴充安全性系統、中繼資料系統、序列化系統，以及連接應用程式與基礎通道系統的繫結和繫結項目。  
  
- 通道和通道執行階段， 這會擴充在訊息層級上運作的系統，提供通訊協定、傳輸和編碼支援。  
  
- 主機執行階段， 這會擴充裝載應用程式定義域與通道和應用程式執行階段之間的關係。  
  
### <a name="extending-the-application-runtime"></a>擴充應用程式執行階段  

 在 WCF 應用程式中，以相對應通道的訊息，以及以應用程式本身為目標的訊息，兩者之間會有差異。 通道訊息支援某些與通道相關的功能，例如建立安全對話或建立可靠的工作階段。 這些訊息不適用於應用程式執行階段，在使用應用程式層之前，就會先處理訊息。  
  
 應用程式訊息包含您或您的客戶所建立，並且用於用戶端或服務作業的資料。 視您的需要而定，這些訊息適用於形式為訊息或物件的應用程式層級擴充系統。  
  
 所有訊息都會通過通道系統，但是只有應用程式訊息會從通道系統傳遞至應用程式。 若要建立新的通道層級功能，您必須擴充通道系統。 若要建立新的應用程式層級功能，您必須擴充服務或用戶端執行階段 (分別是發送器和通道處理站)。 如需擴充應用程式執行時間的詳細資訊，請參閱 [擴充 ServiceHost 和服務模型層](./extending/extending-servicehost-and-the-service-model-layer.md)。  
  
#### <a name="extending-security"></a>擴充安全性  

 若要建置自訂安全性機制，例如權杖和認證，您必須擴充安全性系統。 如需詳細資訊，請參閱 [擴充安全性](./extending/extending-security.md)。  
  
#### <a name="extending-metadata"></a>擴充中繼資料  

 若要以不同於預設的方式公開中繼資料，您必須擴充中繼資料系統。 如需詳細資訊，請參閱 [擴充中繼資料系統](./extending/extending-the-metadata-system.md)。  
  
#### <a name="extending-serialization"></a>擴充序列化  

 若要建置自訂編碼器、提供資料代理或其他涉及自訂傳輸資料的工作，您必須擴充序列化系統。 如需詳細資訊，請參閱 [擴充編碼器和](./extending/extending-encoders-and-serializers.md)序列化程式。  
  
#### <a name="extending-bindings"></a>擴充繫結  

 若要將傳輸或通訊協定通道與應用程式層產生關聯，您必須擴充繫結系統。 如需詳細資訊，請參閱 [擴充](./extending/extending-bindings.md)系結。  
  
### <a name="extending-the-channel-system"></a>擴充通道系統  

 若要建立支援自訂傳輸或通訊協定功能的通道，請參閱 [擴充通道層](./extending/extending-the-channel-layer.md)。  
  
### <a name="extending-the-service-hosting-system"></a>擴充服務裝載系統  

 若要修改服務範圍的應用程式模型，您必須擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 類別。 如需詳細資訊，請參閱 [擴充 ServiceHost 和服務模型層](./extending/extending-servicehost-and-the-service-model-layer.md)。  
  
 若要修改裝載應用程式定義域與服務主機之間的關係，您必須擴充 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> 類別。 如需詳細資訊，請參閱 [使用 ServiceHostFactory 擴充裝載](./extending/extending-hosting-using-servicehostfactory.md)。  
  
## <a name="see-also"></a>另請參閱

- [延伸 WCF](./extending/index.md)
