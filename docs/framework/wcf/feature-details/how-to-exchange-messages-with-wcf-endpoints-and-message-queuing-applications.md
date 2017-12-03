---
title: "HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b18dab37a18723671cebf51c3cc943b907b38a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息
您可以使用 MSMQ 整合繫結來轉換傳入與傳出 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的 MSMQ 訊息，藉此將現有的訊息佇列 (MSMQ) 應用程式與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 進行整合。 這樣一來，您就可以從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端對 MSMQ 接收者應用程式進行呼叫，並從 MSMQ 傳送者應用程式對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務進行呼叫。  
  
 在本章節中，我們將說明如何在 (1) <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 用戶端與使用 System.Messaging 撰寫而成的 MSMQ 應用程式服務之間，以及 (2) MSMQ 應用程式用戶端與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間，使用已佇列通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
 如需完整範例，示範如何呼叫 MSMQ 接收者應用程式從[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端，請參閱[Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)範例。  
  
 如需完整範例，示範如何呼叫[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]從 MSMQ 用戶端服務，請參閱[Message Queuing，將 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)範例。  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>若要從 MSMQ 用戶端建立可接收訊息的 WCF 服務  
  
1.  定義可定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 (用來接收來自 MSMQ 傳送者應用程式的佇列訊息) 之服務合約的介面，如下列範例程式碼所示。  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  實作介面並將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用至類別，如下列範例程式碼所示。  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  建立會指定 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 的組態檔。  
  
  
  
4.  產生可使用設定繫結的 <xref:System.ServiceModel.ServiceHost> 物件。  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>若要建立可將訊息傳送至 MSMQ 接收者應用程式的 WCF 用戶端  
  
1.  定義可定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端 (用來將佇列訊息傳送至 MSMQ 接收者) 之服務合約的介面，如下列範例程式碼所示。  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端將用來呼叫 MSMQ 接收者的用戶端類別。  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  建立會指定 MsmqIntegrationBinding 繫結使用的組態。  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  建立用戶端類別的執行個體，並呼叫訊息接收服務所定義的方法。  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>另請參閱  
 [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [如何： Exchange 佇列與 WCF 端點的訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [安裝訊息佇列 (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [訊息佇列至 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [透過訊息佇列的訊息安全性](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
