---
title: 在工作階段中群組佇列訊息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 62aa269d138d436824d3c825de9f722490d3b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491897"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="e1bc2-102">在工作階段中群組佇列訊息</span><span class="sxs-lookup"><span data-stu-id="e1bc2-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="e1bc2-103">Windows Communication Foundation (WCF) 提供可讓您將一組一起進行處理的相關訊息的單一接收應用程式的工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="e1bc2-104">本身是工作階段一部分的訊息，也必須是屬於相同的異動。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="e1bc2-105">由於所有訊息都屬於相同的異動，所以如果有任何一個訊息無法進行處理，就會回復整個工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="e1bc2-106">工作階段對於寄不出的信件佇列與有害佇列，會採取類似行為。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="e1bc2-107">針對工作階段在佇列繫結上設定的存留時間 (TTL) 屬性會完整地套用到工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="e1bc2-108">如果工作階段中只有部分訊息在 TTL 到期之前傳送出去，則整個工作階段將置於寄不出的信件佇列中。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="e1bc2-109">同樣地，當工作階段中的訊息無法從應用程式佇列傳送到應用程式的話，則整個工作階段將置於有害佇列 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="e1bc2-110">訊息群組範例</span><span class="sxs-lookup"><span data-stu-id="e1bc2-110">Message Grouping Example</span></span>  
 <span data-ttu-id="e1bc2-111">其中一個範例是很有幫助群組訊息時，實作訂單處理應用程式做為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="e1bc2-112">例如，用戶端將訂單提交給包含一些項目的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="e1bc2-113">接著，用戶端針對每個項目向服務進行呼叫，以便分別傳送每個訊息。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="e1bc2-114">情況可能變成：伺服器 A 收到第一個項目，而伺服器 B 則收到第二個項目。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="e1bc2-115">每次新增一個項目時，負責處理該項目的伺服器就必須找到適當的順序，並將該項目附加上去，如此一來就會變得很沒效率。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="e1bc2-116">就算只有一部伺服器在處理所有要求，效率仍舊可能不彰，因為伺服器必須追蹤目前正在處理的所有訂單，並判斷新增的項目歸屬哪個訂單。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="e1bc2-117">將單一訂單上的所有要求加以群組可大幅簡化此類應用程式的實作。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="e1bc2-118">用戶端應用程式將單一訂單的所有項目傳送到工作階段，這樣一來，當服務處理訂單時，就會立即處理整個工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="e1bc2-119">程序</span><span class="sxs-lookup"><span data-stu-id="e1bc2-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="e1bc2-120">若要設定服務合約使用工作階段</span><span class="sxs-lookup"><span data-stu-id="e1bc2-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="e1bc2-121">定義需要工作階段的服務合約。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="e1bc2-122">若要這麼做，請使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性並指定：</span><span class="sxs-lookup"><span data-stu-id="e1bc2-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="e1bc2-123">將合約中的作業標示為單向，因為這些方法無法傳回任何東西。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="e1bc2-124">若要這麼做，請使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性並指定：</span><span class="sxs-lookup"><span data-stu-id="e1bc2-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="e1bc2-125">實作服務合約並指定 `InstanceContextMode` 的 `PerSession`。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="e1bc2-126">這樣只會針對每個工作階段產生服務一次。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="e1bc2-127">每個服務作業都需要一筆交易。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="e1bc2-128">請使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來加以指定。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="e1bc2-129">完成交易的作業應該同時將 `TransactionAutoComplete` 設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="e1bc2-130">設定使用系統提供之 `NetMsmqBinding` 繫結的端點。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="e1bc2-131">使用 <xref:System.Messaging> 來建立交易式佇列。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="e1bc2-132">您也可以使用訊息佇列 (MSMQ) 或 MMC 來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="e1bc2-133">如果您要這麼做，請建立交易式佇列。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="e1bc2-134">請使用 <xref:System.ServiceModel.ServiceHost> 來建立服務的服務主機。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="e1bc2-135">開啟服務主機來提供服務。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="e1bc2-136">關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="e1bc2-137">若要設定用戶端</span><span class="sxs-lookup"><span data-stu-id="e1bc2-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="e1bc2-138">建立異動範圍以寫入異動式佇列。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="e1bc2-139">建立 WCF 用戶端會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="e1bc2-140">下訂單。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="e1bc2-141">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1bc2-142">範例</span><span class="sxs-lookup"><span data-stu-id="e1bc2-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e1bc2-143">描述</span><span class="sxs-lookup"><span data-stu-id="e1bc2-143">Description</span></span>  
 <span data-ttu-id="e1bc2-144">下列範例提供 `IProcessOrder` 服務以及使用此服務之用戶端的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="e1bc2-145">它會顯示 WCF 提供的群組行為所使用的佇列工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1bc2-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="e1bc2-146">服務的程式碼</span><span class="sxs-lookup"><span data-stu-id="e1bc2-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="e1bc2-147">用戶端的程式碼</span><span class="sxs-lookup"><span data-stu-id="e1bc2-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="e1bc2-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1bc2-148">See Also</span></span>  
 [<span data-ttu-id="e1bc2-149">工作階段和佇列</span><span class="sxs-lookup"><span data-stu-id="e1bc2-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="e1bc2-150">佇列概觀</span><span class="sxs-lookup"><span data-stu-id="e1bc2-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
