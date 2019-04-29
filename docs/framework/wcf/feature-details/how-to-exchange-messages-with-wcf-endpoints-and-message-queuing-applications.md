---
title: HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772940"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="bbe55-102">HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="bbe55-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="bbe55-103">您可以整合現有的 Message Queuing (MSMQ) 應用程式與 Windows Communication Foundation (WCF) 應用程式，使用 MSMQ 整合繫結，將 MSMQ 訊息，與 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="bbe55-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="bbe55-104">這可讓您呼叫 MSMQ 接收者應用程式，從 WCF 用戶端，以及從 MSMQ 傳送者應用程式呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="bbe55-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="bbe55-105">在本節中，我們會說明如何使用<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>（1） 的 WCF 用戶端與使用 System.Messaging 和 （2) MSMQ 應用程式用戶端和 WCF 服務撰寫的 MSMQ 應用程式服務之間的佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="bbe55-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="bbe55-106">如需示範如何從 WCF 用戶端呼叫 MSMQ 接收者應用程式的完整範例，請參閱 < [Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)範例。</span><span class="sxs-lookup"><span data-stu-id="bbe55-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="bbe55-107">如需示範如何從 MSMQ 用戶端呼叫 WCF 服務的完整範例，請參閱 <<c0> [ 訊息佇列至 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)範例。</span><span class="sxs-lookup"><span data-stu-id="bbe55-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="bbe55-108">若要從 MSMQ 用戶端建立可接收訊息的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="bbe55-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="bbe55-109">定義這個介面會定義服務合約的 WCF 服務，接收來自 MSMQ 傳送者應用程式中，已排入佇列的訊息，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bbe55-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="bbe55-110">實作介面並將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用至類別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bbe55-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="bbe55-111">建立會指定 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="bbe55-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="bbe55-112">產生可使用設定繫結的 <xref:System.ServiceModel.ServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="bbe55-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="bbe55-113">若要建立可將訊息傳送至 MSMQ 接收者應用程式的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="bbe55-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="bbe55-114">定義這個介面會定義服務合約的 WCF 用戶端傳送佇列訊息至 MSMQ 接收者，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bbe55-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="bbe55-115">定義 WCF 用戶端會使用來呼叫 MSMQ 接收者的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="bbe55-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="bbe55-116">建立會指定 MsmqIntegrationBinding 繫結使用的組態。</span><span class="sxs-lookup"><span data-stu-id="bbe55-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="bbe55-117">建立用戶端類別的執行個體，並呼叫訊息接收服務所定義的方法。</span><span class="sxs-lookup"><span data-stu-id="bbe55-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bbe55-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbe55-118">See also</span></span>

- [<span data-ttu-id="bbe55-119">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="bbe55-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [<span data-ttu-id="bbe55-120">如何：與 WCF 端點交換佇列訊息</span><span class="sxs-lookup"><span data-stu-id="bbe55-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="bbe55-121">Windows Communication Foundation 至訊息佇列</span><span class="sxs-lookup"><span data-stu-id="bbe55-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="bbe55-122">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="bbe55-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="bbe55-123">訊息佇列至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bbe55-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="bbe55-124">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="bbe55-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
