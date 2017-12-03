---
title: "中介層用戶端應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b73641fcbc881e57465f722d3a0f647938a5e12e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="middle-tier-client-applications"></a>中介層用戶端應用程式
本主題討論與使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 之中介層 (Middle Tier) 用戶端應用程式有關的各種特定問題。  
  
## <a name="increasing-middle-tier-client-performance"></a>提升中介層用戶端效能  
 由於 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 提供了豐富的功能集，與往常的通訊技術 (例如，使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 Web 服務) 相比，建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端執行個體的作業可能較為複雜。 例如，<xref:System.ServiceModel.ChannelFactory%601> 物件開啟時，它可以和服務建立安全工作階段，而這個程序通常會增加用戶端執行個體的啟動時間。 一般而言，這些附加功能對用戶端應用程式產生的影響不大，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端會進行數次呼叫，然後才關閉。  
  
 不過，由於中介層用戶端應用程式可以快速建立許多 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件，因此需要更高的初始化需求。 呼叫服務時，有兩種主要方式可以提高中介層應用程式的效能：  
  
-   快取 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件，然後盡可能在後續的呼叫中重複使用它。  
  
-   建立 <xref:System.ServiceModel.ChannelFactory%601> 物件，然後使用這個物件來為每一個呼叫建立新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道物件。  
  
 使用這些方式時要考慮的問題：  
  
-   如果服務正在使用工作階段維護用戶端的特定狀態，那麼就會因為服務的狀態與中介層用戶端的狀態相連結，而無法透過多用戶層 (Multiple-Client Tier) 要求來重複使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中介層用戶端。  
  
-   如果服務必須對個別用戶端進行驗證，您必須在中介層上為每個傳入要求建立新的用戶端，而不是重複使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中介層用戶端 (或 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道物件)，這是因為建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端 (或 <xref:System.ServiceModel.ChannelFactory%601>) 之後，就無法修改中介層的用戶端認證。  
  
-   當通道及其建立的用戶端為安全執行緒 (Thread-Safe) 時，它們可能不支援同時將一個以上的訊息寫入網路傳輸。 如果您正在傳送大型訊息，尤其是傳送資料流 (Streaming) 時，傳送作業可能會進入封鎖狀態而等候其他傳送作業完成。 這會產生兩種問題：無法並行存取，以及可能在控制流程返回重複使用通道的服務時發生死結 (Deadlock) 狀況 (亦即，共用用戶端呼叫某個服務，而這個服務的程式碼路徑又反過來回呼此共用用戶端)。 無論您重複使用什麼類型的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端都是如此。  
  
-   您必須處理已發生錯誤的通道，不論您是否共用該通道。 不過，在重複使用通道時，發生錯誤的通道可撤銷一個以上的暫止要求或傳送。  
  
 如需示範其最佳作法重複使用多個要求的用戶端的範例，請參閱[資料繫結的 ASP.NET 用戶端中](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)。  
  
 此外，您還可以為那些使用可透過 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化之資料型別的用戶端增進啟動效能。這些用戶端會在執行階段針對這些資料型別產生並編譯序列化程式碼，可能因此拖慢啟動效能。 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可以藉由從應用程式的編譯組件產生必要的序列化程式碼改善這些應用程式的啟動效能。 如需詳細資訊，請參閱[How to： 改善啟動時間的 WCF 用戶端應用程式使用 XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 用戶端存取服務](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
