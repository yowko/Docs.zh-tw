---
title: 作法：與 WCF 端點和訊息佇列應用程式交換訊息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 8f8baf345059c01b0fef3b61ef85556151269118
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246416"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="4c548-102">作法：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="4c548-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>

<span data-ttu-id="4c548-103">您可以使用 MSMQ 整合系結，將 MSMQ 訊息轉換為 WCF 訊息，以將現有訊息佇列 (MSMQ) 應用程式與 Windows Communication Foundation (WCF) 應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="4c548-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="4c548-104">這可讓您從 WCF 用戶端呼叫 MSMQ 接收者應用程式，以及從 MSMQ 傳送者應用程式呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4c548-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="4c548-105">在本節中，我們將說明如何使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) WCF 用戶端與使用 System. 訊息撰寫的 MSMQ 應用程式服務，以及 (2) msmq 應用程式用戶端和 WCF 服務之間的佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="4c548-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="4c548-106">如需示範如何從 WCF 用戶端呼叫 MSMQ 接收者應用程式的完整範例，請參閱 [Windows Communication Foundation 到訊息佇列](../samples/wcf-to-message-queuing.md) 範例。</span><span class="sxs-lookup"><span data-stu-id="4c548-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="4c548-107">如需示範如何從 MSMQ 用戶端呼叫 WCF 服務的完整範例，請參閱 [訊息佇列以 Windows Communication Foundation](../samples/message-queuing-to-wcf.md) 範例。</span><span class="sxs-lookup"><span data-stu-id="4c548-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="4c548-108">若要從 MSMQ 用戶端建立可接收訊息的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4c548-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="4c548-109">定義介面，以定義 WCF 服務的服務合約，此服務合約會接收來自 MSMQ 傳送者應用程式的佇列訊息，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4c548-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="4c548-110">實作介面並將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用至類別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4c548-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="4c548-111">建立會指定 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="4c548-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="4c548-112">產生可使用設定繫結的 <xref:System.ServiceModel.ServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="4c548-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="4c548-113">若要建立可將訊息傳送至 MSMQ 接收者應用程式的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="4c548-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="4c548-114">定義介面，以定義將佇列訊息傳送至 MSMQ 接收者的 WCF 用戶端服務合約，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4c548-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="4c548-115">定義 WCF 用戶端用來呼叫 MSMQ 接收器的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="4c548-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="4c548-116">建立會指定 MsmqIntegrationBinding 繫結使用的組態。</span><span class="sxs-lookup"><span data-stu-id="4c548-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="4c548-117">建立用戶端類別的執行個體，並呼叫訊息接收服務所定義的方法。</span><span class="sxs-lookup"><span data-stu-id="4c548-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4c548-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c548-118">See also</span></span>

- [<span data-ttu-id="4c548-119">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="4c548-119">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="4c548-120">作法：與 WCF 端點交換佇列訊息</span><span class="sxs-lookup"><span data-stu-id="4c548-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="4c548-121">Windows Communication Foundation 至訊息佇列</span><span class="sxs-lookup"><span data-stu-id="4c548-121">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="4c548-122">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="4c548-122">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="4c548-123">訊息佇列至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4c548-123">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="4c548-124">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="4c548-124">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
