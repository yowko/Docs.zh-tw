---
title: Windows Communication Foundation 中的佇列
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: d1fee4fdde18563ec6ccce4f0675d8581184be08
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596730"
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="049c1-102">Windows Communication Foundation 中的佇列</span><span class="sxs-lookup"><span data-stu-id="049c1-102">Queues in Windows Communication Foundation</span></span>
<span data-ttu-id="049c1-103">本節中的主題將討論佇列的 Windows Communication Foundation （WCF）支援。</span><span class="sxs-lookup"><span data-stu-id="049c1-103">The topics in this section discuss Windows Communication Foundation (WCF) support for queues.</span></span> <span data-ttu-id="049c1-104">WCF 藉由利用 Microsoft Message Queuing （先前稱為 MSMQ）做為傳輸來提供佇列的支援，並啟用下列案例：</span><span class="sxs-lookup"><span data-stu-id="049c1-104">WCF provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
- <span data-ttu-id="049c1-105">鬆散結合的應用程式。</span><span class="sxs-lookup"><span data-stu-id="049c1-105">Loosely coupled applications.</span></span> <span data-ttu-id="049c1-106">傳送應用程式可以傳送訊息至佇列，不需要知道接收應用程式是否可以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="049c1-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="049c1-107">佇列以不依靠接收應用程式可以多快處理訊息的速率，提供允許傳送應用程式傳送訊息至佇列的獨立處理。</span><span class="sxs-lookup"><span data-stu-id="049c1-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="049c1-108">傳送訊息至未與訊息處理緊密結合的佇列時，整體系統可用性會增加。</span><span class="sxs-lookup"><span data-stu-id="049c1-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
- <span data-ttu-id="049c1-109">隔離失敗。</span><span class="sxs-lookup"><span data-stu-id="049c1-109">Failure isolation.</span></span> <span data-ttu-id="049c1-110">應用程式傳送或接收訊息至佇列可能失敗，但不會互相影響。</span><span class="sxs-lookup"><span data-stu-id="049c1-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="049c1-111">例如，如果接收應用程式失敗，傳送應用程式可以繼續傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="049c1-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="049c1-112">當接收者再次接收時，可以處理來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="049c1-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="049c1-113">隔離失敗會增加整體系統的可靠性與可用性。</span><span class="sxs-lookup"><span data-stu-id="049c1-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
- <span data-ttu-id="049c1-114">負載平衡。</span><span class="sxs-lookup"><span data-stu-id="049c1-114">Load leveling.</span></span> <span data-ttu-id="049c1-115">傳送應用程式可能會利用訊息讓接收應用程式爆滿。</span><span class="sxs-lookup"><span data-stu-id="049c1-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="049c1-116">佇列可以管理不相符的訊息產生與消耗率，因此接收者不會爆滿。</span><span class="sxs-lookup"><span data-stu-id="049c1-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
- <span data-ttu-id="049c1-117">中斷操作。</span><span class="sxs-lookup"><span data-stu-id="049c1-117">Disconnected operations.</span></span> <span data-ttu-id="049c1-118">當透過高延遲網路或可用性有限的網路進行通訊時 (例如使用行動裝置)，傳送、接收和處理操作可能中斷。</span><span class="sxs-lookup"><span data-stu-id="049c1-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="049c1-119">佇列能夠使這些操作繼續進行，即使已經與端點中斷連線也是一樣。</span><span class="sxs-lookup"><span data-stu-id="049c1-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="049c1-120">重新建立連線後，佇列會將訊息轉送至接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="049c1-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="049c1-121">若要使用 WCF 應用程式中的佇列功能，您可以使用其中一個標準系結，或者如果其中一個標準系結無法滿足您的需求，您可以建立自訂系結。</span><span class="sxs-lookup"><span data-stu-id="049c1-121">To use the queues feature in a WCF application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> <span data-ttu-id="049c1-122">如需相關標準系結和如何選擇的詳細資訊，請參閱[如何：使用 WCF 端點和訊息佇列應用程式交換訊息](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="049c1-122">For more information about relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> <span data-ttu-id="049c1-123">如需建立自訂繫結的詳細資訊，請參閱[自訂繫結](../extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="049c1-123">For more information about creating custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="049c1-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="049c1-124">In This Section</span></span>  
 [<span data-ttu-id="049c1-125">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="049c1-125">Queues Overview</span></span>](queues-overview.md)  
 <span data-ttu-id="049c1-126">訊息佇列概念的概觀。</span><span class="sxs-lookup"><span data-stu-id="049c1-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="049c1-127">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="049c1-127">Queuing in WCF</span></span>](queuing-in-wcf.md)  
 <span data-ttu-id="049c1-128">WCF 佇列支援的總覽。</span><span class="sxs-lookup"><span data-stu-id="049c1-128">An overview of WCF queue support.</span></span>  
  
 [<span data-ttu-id="049c1-129">HOW TO：與 WCF 端點交換佇列訊息</span><span class="sxs-lookup"><span data-stu-id="049c1-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="049c1-130">說明如何使用類別在 <xref:System.ServiceModel.NetMsmqBinding> wcf 用戶端和 wcf 服務之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="049c1-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a WCF client and WCF service.</span></span>  
  
 [<span data-ttu-id="049c1-131">如何：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="049c1-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="049c1-132">說明如何使用在 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> WCF 和訊息佇列應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="049c1-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between WCF and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="049c1-133">在工作階段中群組佇列訊息</span><span class="sxs-lookup"><span data-stu-id="049c1-133">Grouping Queued Messages in a Session</span></span>](grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="049c1-134">說明如何將佇列中的訊息分組，以協助單一接收應用程式處理相關訊息。</span><span class="sxs-lookup"><span data-stu-id="049c1-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="049c1-135">批次處理異動中的訊息</span><span class="sxs-lookup"><span data-stu-id="049c1-135">Batching Messages in a Transaction</span></span>](batching-messages-in-a-transaction.md)  
 <span data-ttu-id="049c1-136">說明如何批次處理交易中的訊息。</span><span class="sxs-lookup"><span data-stu-id="049c1-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="049c1-137">使用無效信件佇列來處理訊息傳輸失敗</span><span class="sxs-lookup"><span data-stu-id="049c1-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="049c1-138">說明如何使用寄不出的信件佇列處理訊息傳送和傳遞失敗，以及如何處理來自寄不出的信件佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="049c1-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="049c1-139">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="049c1-139">Poison Message Handling</span></span>](poison-message-handling.md)  
 <span data-ttu-id="049c1-140">說明如何處理有害訊息 (超過傳送到接收應用程式的最大嘗試傳遞次數的訊息)。</span><span class="sxs-lookup"><span data-stu-id="049c1-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="049c1-141">Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異</span><span class="sxs-lookup"><span data-stu-id="049c1-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="049c1-142">摘要說明 Windows Vista、Windows Server 2003 和 Windows XP 之間 WCF 佇列功能的差異。</span><span class="sxs-lookup"><span data-stu-id="049c1-142">Summarizes the differences in the WCF queues feature between Windows Vista, Windows Server 2003, and Windows XP.</span></span>  
  
 [<span data-ttu-id="049c1-143">使用傳輸安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="049c1-143">Securing Messages Using Transport Security</span></span>](securing-messages-using-transport-security.md)  
 <span data-ttu-id="049c1-144">描述如何使用傳輸安全性來保護佇列訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="049c1-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="049c1-145">使用訊息安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="049c1-145">Securing Messages Using Message Security</span></span>](securing-messages-using-message-security.md)  
 <span data-ttu-id="049c1-146">描述如何使用訊息安全性來保護佇列訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="049c1-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="049c1-147">為佇列訊息進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="049c1-147">Troubleshooting Queued Messaging</span></span>](troubleshooting-queued-messaging.md)  
 <span data-ttu-id="049c1-148">說明如何疑難排解常見的佇列問題。</span><span class="sxs-lookup"><span data-stu-id="049c1-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="049c1-149">佇列通訊的最佳做法</span><span class="sxs-lookup"><span data-stu-id="049c1-149">Best Practices for Queued Communication</span></span>](best-practices-for-queued-communication.md)  
 <span data-ttu-id="049c1-150">說明使用 WCF 佇列通訊的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="049c1-150">Explains best practices for using WCF queued communication.</span></span>  
