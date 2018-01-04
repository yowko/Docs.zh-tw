---
title: "Windows Communication Foundation 中的佇列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c87e384b3186a1dd4b53ba6c21d92bf4d0e6a8c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="bfd54-102">Windows Communication Foundation 中的佇列</span><span class="sxs-lookup"><span data-stu-id="bfd54-102">Queues in Windows Communication Foundation</span></span>
<span data-ttu-id="bfd54-103">本節中的主題討論 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 對佇列的支援。</span><span class="sxs-lookup"><span data-stu-id="bfd54-103">The topics in this section discuss [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for queues.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bfd54-104"> 利用 Microsoft Message Queuing (舊稱 MSMQ) 做為傳輸，以支援佇列功能，並且可以完成下列案例：</span><span class="sxs-lookup"><span data-stu-id="bfd54-104"> provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="bfd54-105">鬆散結合的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfd54-105">Loosely coupled applications.</span></span> <span data-ttu-id="bfd54-106">傳送應用程式可以傳送訊息至佇列，不需要知道接收應用程式是否可以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd54-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="bfd54-107">佇列以不依靠接收應用程式可以多快處理訊息的速率，提供允許傳送應用程式傳送訊息至佇列的獨立處理。</span><span class="sxs-lookup"><span data-stu-id="bfd54-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="bfd54-108">傳送訊息至未與訊息處理緊密結合的佇列時，整體系統可用性會增加。</span><span class="sxs-lookup"><span data-stu-id="bfd54-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
-   <span data-ttu-id="bfd54-109">隔離失敗。</span><span class="sxs-lookup"><span data-stu-id="bfd54-109">Failure isolation.</span></span> <span data-ttu-id="bfd54-110">應用程式傳送或接收訊息至佇列可能失敗，但不會互相影響。</span><span class="sxs-lookup"><span data-stu-id="bfd54-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="bfd54-111">例如，如果接收應用程式失敗，傳送應用程式可以繼續傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="bfd54-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="bfd54-112">當接收者再次接收時，可以處理來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd54-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="bfd54-113">隔離失敗會增加整體系統的可靠性與可用性。</span><span class="sxs-lookup"><span data-stu-id="bfd54-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
-   <span data-ttu-id="bfd54-114">負載平衡。</span><span class="sxs-lookup"><span data-stu-id="bfd54-114">Load leveling.</span></span> <span data-ttu-id="bfd54-115">傳送應用程式可能會利用訊息讓接收應用程式爆滿。</span><span class="sxs-lookup"><span data-stu-id="bfd54-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="bfd54-116">佇列可以管理不相符的訊息產生與消耗率，因此接收者不會爆滿。</span><span class="sxs-lookup"><span data-stu-id="bfd54-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
-   <span data-ttu-id="bfd54-117">中斷操作。</span><span class="sxs-lookup"><span data-stu-id="bfd54-117">Disconnected operations.</span></span> <span data-ttu-id="bfd54-118">當透過高延遲網路或可用性有限的網路進行通訊時 (例如使用行動裝置)，傳送、接收和處理操作可能中斷。</span><span class="sxs-lookup"><span data-stu-id="bfd54-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="bfd54-119">佇列能夠使這些操作繼續進行，即使已經與端點中斷連線也是一樣。</span><span class="sxs-lookup"><span data-stu-id="bfd54-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="bfd54-120">重新建立連線後，佇列會將訊息轉送至接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfd54-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="bfd54-121">若要使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中的佇列功能，您可以使用其中一個標準繫結，或者如果其中一個標準繫結無法滿足您的需求時，您可以建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="bfd54-121">To use the queues feature in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bfd54-122">相關的標準繫結，以及如何選擇一個，請參閱[How to： 與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd54-122"> relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bfd54-123">建立自訂繫結，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd54-123"> creating custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfd54-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="bfd54-124">In This Section</span></span>  
 [<span data-ttu-id="bfd54-125">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="bfd54-125">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 <span data-ttu-id="bfd54-126">訊息佇列概念的概觀。</span><span class="sxs-lookup"><span data-stu-id="bfd54-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="bfd54-127">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="bfd54-127">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 <span data-ttu-id="bfd54-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 佇列支援的概觀。</span><span class="sxs-lookup"><span data-stu-id="bfd54-128">An overview of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queue support.</span></span>  
  
 [<span data-ttu-id="bfd54-129">如何：與 WCF 端點交換佇列訊息</span><span class="sxs-lookup"><span data-stu-id="bfd54-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="bfd54-130">說明如何使用 <xref:System.ServiceModel.NetMsmqBinding> 類別在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間通訊。</span><span class="sxs-lookup"><span data-stu-id="bfd54-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="bfd54-131">如何：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="bfd54-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="bfd54-132">說明如何使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和訊息佇列應用程式之間通訊。</span><span class="sxs-lookup"><span data-stu-id="bfd54-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="bfd54-133">在工作階段中群組佇列訊息</span><span class="sxs-lookup"><span data-stu-id="bfd54-133">Grouping Queued Messages in a Session</span></span>](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="bfd54-134">說明如何將佇列中的訊息分組，以協助單一接收應用程式處理相關訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd54-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="bfd54-135">批次處理異動中的訊息</span><span class="sxs-lookup"><span data-stu-id="bfd54-135">Batching Messages in a Transaction</span></span>](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 <span data-ttu-id="bfd54-136">說明如何批次處理異動中的訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd54-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="bfd54-137">使用無效信件佇列來處理訊息傳輸失敗</span><span class="sxs-lookup"><span data-stu-id="bfd54-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="bfd54-138">說明如何使用寄不出的信件佇列處理訊息傳送和傳遞失敗，以及如何處理來自寄不出的信件佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd54-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="bfd54-139">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="bfd54-139">Poison Message Handling</span></span>](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 <span data-ttu-id="bfd54-140">說明如何處理有害訊息 (超過傳送到接收應用程式的最大嘗試傳遞次數的訊息)。</span><span class="sxs-lookup"><span data-stu-id="bfd54-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="bfd54-141">Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異</span><span class="sxs-lookup"><span data-stu-id="bfd54-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="bfd54-142">摘要說明在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、[!INCLUDE[wv](../../../../includes/wv-md.md)] 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 之間 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 佇列的差異。</span><span class="sxs-lookup"><span data-stu-id="bfd54-142">Summarizes the differences in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queues feature between [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 [<span data-ttu-id="bfd54-143">使用傳輸安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="bfd54-143">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 <span data-ttu-id="bfd54-144">描述如何使用傳輸安全性來保護佇列訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="bfd54-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="bfd54-145">使用訊息安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="bfd54-145">Securing Messages Using Message Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 <span data-ttu-id="bfd54-146">描述如何使用訊息安全性來保護佇列訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="bfd54-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="bfd54-147">為佇列訊息進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="bfd54-147">Troubleshooting Queued Messaging</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 <span data-ttu-id="bfd54-148">說明如何疑難排解常見的佇列問題。</span><span class="sxs-lookup"><span data-stu-id="bfd54-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="bfd54-149">佇列通訊的最佳做法</span><span class="sxs-lookup"><span data-stu-id="bfd54-149">Best Practices for Queued Communication</span></span>](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 <span data-ttu-id="bfd54-150">說明使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 佇列通訊的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="bfd54-150">Explains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queued communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd54-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd54-151">See Also</span></span>  
 [<span data-ttu-id="bfd54-152">訊息佇列</span><span class="sxs-lookup"><span data-stu-id="bfd54-152">Message Queuing</span></span>](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)
