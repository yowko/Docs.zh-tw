---
title: "HOW TO：與 WCF 端點交換佇列訊息"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6c50d9c6740b0c680e349a71bf4b3bdece2b34f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="eb4da-102">HOW TO：與 WCF 端點交換佇列訊息</span><span class="sxs-lookup"><span data-stu-id="eb4da-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="eb4da-103">佇列可確保用戶端與 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務之間發生可靠的傳訊，即使服務在通訊時無法使用也一樣。</span><span class="sxs-lookup"><span data-stu-id="eb4da-103">Queues ensure that reliable messaging can occur between a client and a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="eb4da-104">下列程序顯示如何在實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，使用標準佇列繫結確保在用戶端與服務間建立永久性通訊。</span><span class="sxs-lookup"><span data-stu-id="eb4da-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="eb4da-105">此章節解釋如何在 <xref:System.ServiceModel.NetMsmqBinding> 用戶端與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 處理佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="eb4da-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="eb4da-106">若要在 WCF 服務中使用佇列</span><span class="sxs-lookup"><span data-stu-id="eb4da-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="eb4da-107">使用以 <xref:System.ServiceModel.ServiceContractAttribute>標記的介面定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="eb4da-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="eb4da-108">在屬於服務合約部分的介面中標示作業為 <xref:System.ServiceModel.OperationContractAttribute> 並指定它們為單向，因為此方法不用傳回任何回應。</span><span class="sxs-lookup"><span data-stu-id="eb4da-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="eb4da-109">下列程式碼提供範例服務合約以及其作業定義。</span><span class="sxs-lookup"><span data-stu-id="eb4da-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="eb4da-110">當服務合約通過使用者定義型別，您必須為這些型別定義資料合約。</span><span class="sxs-lookup"><span data-stu-id="eb4da-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="eb4da-111">下列程式碼示範兩份資料合約：`PurchaseOrder` 和 `PurchaseOrderLineItem`。</span><span class="sxs-lookup"><span data-stu-id="eb4da-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="eb4da-112">這兩個型別定義了傳送至服務的資料 </span><span class="sxs-lookup"><span data-stu-id="eb4da-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="eb4da-113">(請注意，定義這類資料合約的類別也定義許多方法。</span><span class="sxs-lookup"><span data-stu-id="eb4da-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="eb4da-114">這些方法不被視為資料合約的部分。</span><span class="sxs-lookup"><span data-stu-id="eb4da-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="eb4da-115">只有以 `DataMember` 屬性宣告的成員才屬於資料合約的部分)。</span><span class="sxs-lookup"><span data-stu-id="eb4da-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="eb4da-116">實作在類別中之介面所定義的服務合約方法。</span><span class="sxs-lookup"><span data-stu-id="eb4da-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="eb4da-117">請注意，<xref:System.ServiceModel.OperationBehaviorAttribute> 放置在 `SubmitPurchaseOrder` 方法上。</span><span class="sxs-lookup"><span data-stu-id="eb4da-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="eb4da-118">其用意是指定必須在交易內呼叫此作業，而且交易會隨著方法完成而自動完成。</span><span class="sxs-lookup"><span data-stu-id="eb4da-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="eb4da-119">使用 <xref:System.Messaging> 來建立交易式佇列。</span><span class="sxs-lookup"><span data-stu-id="eb4da-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="eb4da-120">您可以選擇使用 Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) 建立佇列。</span><span class="sxs-lookup"><span data-stu-id="eb4da-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="eb4da-121">若是這樣，請確定您建立異動式佇列。</span><span class="sxs-lookup"><span data-stu-id="eb4da-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="eb4da-122">在組態中定義 <xref:System.ServiceModel.Description.ServiceEndpoint>，以指定服務位址，並使用標準 <xref:System.ServiceModel.NetMsmqBinding> 繫結。</span><span class="sxs-lookup"><span data-stu-id="eb4da-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="eb4da-123">使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]組態，請參閱[設定的 Windows Communication Foundation 應用程式](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)。</span><span class="sxs-lookup"><span data-stu-id="eb4da-123"> using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="eb4da-124">使用從佇列讀取訊息並加以處理的 `OrderProcessing` 建立 <xref:System.ServiceModel.ServiceHost> 服務的主機。</span><span class="sxs-lookup"><span data-stu-id="eb4da-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="eb4da-125">開啟服務主機來提供服務。</span><span class="sxs-lookup"><span data-stu-id="eb4da-125">Open the service host to make the service available.</span></span> <span data-ttu-id="eb4da-126">顯示一則訊息，指示使用者按任意鍵終止服務。</span><span class="sxs-lookup"><span data-stu-id="eb4da-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="eb4da-127">呼叫 `ReadLine` 以等待按鍵動作，隨後關閉服務。</span><span class="sxs-lookup"><span data-stu-id="eb4da-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="eb4da-128">若要建立佇列服務的用戶端</span><span class="sxs-lookup"><span data-stu-id="eb4da-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="eb4da-129">下列範例示範如何執行裝載應用程式，以及使用 Svcutil.exe 工具建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。</span><span class="sxs-lookup"><span data-stu-id="eb4da-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="eb4da-130">在組態中定義 <xref:System.ServiceModel.Description.ServiceEndpoint>，藉以指定位址並使用標準 <xref:System.ServiceModel.NetMsmqBinding> 繫結，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eb4da-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="eb4da-131">建立交易範圍以寫入交易式佇列、呼叫 `SubmitPurchaseOrder` 作業和關閉 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eb4da-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="eb4da-132">範例</span><span class="sxs-lookup"><span data-stu-id="eb4da-132">Example</span></span>  
 <span data-ttu-id="eb4da-133">以下內容顯示本範例所囊括的服務程式碼、裝載應用程式、App.config 檔案和用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb4da-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="eb4da-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb4da-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="eb4da-135">交易的 MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="eb4da-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="eb4da-136">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="eb4da-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="eb4da-137">如何： 與 WCF 端點交換訊息和訊息佇列應用程式</span><span class="sxs-lookup"><span data-stu-id="eb4da-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="eb4da-138">Windows Communication Foundation 至訊息佇列</span><span class="sxs-lookup"><span data-stu-id="eb4da-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="eb4da-139">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="eb4da-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="eb4da-140">訊息佇列整合繫結範例</span><span class="sxs-lookup"><span data-stu-id="eb4da-140">Message Queuing Integration Binding Samples</span></span>](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="eb4da-141">訊息佇列至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="eb4da-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="eb4da-142">透過訊息佇列的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="eb4da-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
