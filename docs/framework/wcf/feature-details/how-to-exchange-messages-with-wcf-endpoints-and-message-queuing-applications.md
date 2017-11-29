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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d09b8e662b2876fa5d5c5246ea7e7a4998cde9ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="d493c-102">HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="d493c-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="d493c-103">您可以使用 MSMQ 整合繫結來轉換傳入與傳出 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的 MSMQ 訊息，藉此將現有的訊息佇列 (MSMQ) 應用程式與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 進行整合。</span><span class="sxs-lookup"><span data-stu-id="d493c-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="d493c-104">這樣一來，您就可以從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端對 MSMQ 接收者應用程式進行呼叫，並從 MSMQ 傳送者應用程式對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="d493c-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="d493c-105">在本章節中，我們將說明如何在 (1) <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 用戶端與使用 System.Messaging 撰寫而成的 MSMQ 應用程式服務之間，以及 (2) MSMQ 應用程式用戶端與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間，使用已佇列通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d493c-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="d493c-106">如需完整範例，示範如何呼叫 MSMQ 接收者應用程式從[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端，請參閱[Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d493c-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="d493c-107">如需完整範例，示範如何呼叫[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]從 MSMQ 用戶端服務，請參閱[Message Queuing，將 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d493c-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="d493c-108">若要從 MSMQ 用戶端建立可接收訊息的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="d493c-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="d493c-109">定義可定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 (用來接收來自 MSMQ 傳送者應用程式的佇列訊息) 之服務合約的介面，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d493c-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="d493c-110">實作介面並將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用至類別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d493c-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="d493c-111">建立會指定 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="d493c-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="d493c-112">產生可使用設定繫結的 <xref:System.ServiceModel.ServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="d493c-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="d493c-113">若要建立可將訊息傳送至 MSMQ 接收者應用程式的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="d493c-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="d493c-114">定義可定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端 (用來將佇列訊息傳送至 MSMQ 接收者) 之服務合約的介面，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d493c-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="d493c-115">定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端將用來呼叫 MSMQ 接收者的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="d493c-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="d493c-116">建立會指定 MsmqIntegrationBinding 繫結使用的組態。</span><span class="sxs-lookup"><span data-stu-id="d493c-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="d493c-117">建立用戶端類別的執行個體，並呼叫訊息接收服務所定義的方法。</span><span class="sxs-lookup"><span data-stu-id="d493c-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d493c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d493c-118">See Also</span></span>  
 [<span data-ttu-id="d493c-119">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="d493c-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="d493c-120">如何： Exchange 佇列與 WCF 端點的訊息</span><span class="sxs-lookup"><span data-stu-id="d493c-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="d493c-121">Windows Communication Foundation 至訊息佇列</span><span class="sxs-lookup"><span data-stu-id="d493c-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="d493c-122">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="d493c-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="d493c-123">訊息佇列至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d493c-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="d493c-124">透過訊息佇列的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="d493c-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
