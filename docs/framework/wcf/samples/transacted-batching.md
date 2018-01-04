---
title: "交易的批次處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87d8e3e09618b214dcafb7afd82970dde54fc4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-batching"></a><span data-ttu-id="41b11-102">交易的批次處理</span><span class="sxs-lookup"><span data-stu-id="41b11-102">Transacted Batching</span></span>
<span data-ttu-id="41b11-103">這個範例會示範如何使用訊息佇列 (MSMQ) 批次處理交易讀取作業。</span><span class="sxs-lookup"><span data-stu-id="41b11-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="41b11-104">「交易的批次處理」是效能最佳化功能，可用於佇列通訊中的交易讀取作業。</span><span class="sxs-lookup"><span data-stu-id="41b11-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41b11-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="41b11-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="41b11-106">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="41b11-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="41b11-107">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="41b11-108">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-108">The service receives messages from the queue.</span></span> <span data-ttu-id="41b11-109">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="41b11-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="41b11-110">這個範例會示範交易的批次處理。</span><span class="sxs-lookup"><span data-stu-id="41b11-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="41b11-111">交易的批次處理是一種行為，可在佇列中讀取許多訊息並進行處理時，使用單一的交易即可。</span><span class="sxs-lookup"><span data-stu-id="41b11-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41b11-112">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="41b11-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="41b11-113">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="41b11-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="41b11-114">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="41b11-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="41b11-115">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="41b11-116">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="41b11-117">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="41b11-118">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="41b11-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="41b11-119">展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="41b11-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="41b11-120">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="41b11-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="41b11-121">請檢查**交易式**方塊。</span><span class="sxs-lookup"><span data-stu-id="41b11-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="41b11-122">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="41b11-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41b11-123">在這個範例中，用戶端會在批次中傳送數百則訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="41b11-124">服務應用程式通常需要一些時間來處理這些訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="41b11-125">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="41b11-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="41b11-126">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="41b11-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="41b11-127">若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例</span><span class="sxs-lookup"><span data-stu-id="41b11-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="41b11-128">根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。</span><span class="sxs-lookup"><span data-stu-id="41b11-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="41b11-129">有兩個相關的屬性，為 MSMQ 傳輸安全性，<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>和<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`驗證模式設定為依預設，`Windows`和保護層級設為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="41b11-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="41b11-130">若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。</span><span class="sxs-lookup"><span data-stu-id="41b11-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="41b11-131">如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="41b11-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="41b11-132">如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="41b11-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="41b11-133">請務必先變更伺服器與用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="41b11-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41b11-134">將 `security``mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="41b11-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="41b11-135">若要在遠端電腦上執行資料庫，請變更連接字串以指向資料庫所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="41b11-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b11-136">需求</span><span class="sxs-lookup"><span data-stu-id="41b11-136">Requirements</span></span>  
 <span data-ttu-id="41b11-137">若要執行此範例，必須已安裝 MSMQ，而且需要 SQL 或 SQL Express。</span><span class="sxs-lookup"><span data-stu-id="41b11-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="41b11-138">示範</span><span class="sxs-lookup"><span data-stu-id="41b11-138">Demonstrates</span></span>  
 <span data-ttu-id="41b11-139">範例會示範交易的批次處理行為。</span><span class="sxs-lookup"><span data-stu-id="41b11-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="41b11-140">交易的批次處理是與 MSMQ 佇列傳輸一起提供的效能最佳化功能。</span><span class="sxs-lookup"><span data-stu-id="41b11-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="41b11-141">當您使用交易來傳送及接收訊息時，實際上有兩個不同的交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="41b11-142">當用戶端在交易範圍內傳送訊息時，對用戶端與用戶端佇列管理員來說，交易屬於本機範圍。</span><span class="sxs-lookup"><span data-stu-id="41b11-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="41b11-143">當服務在交易範圍內接收訊息時，對服務與接收佇列管理員來說，交易屬於本機範圍。</span><span class="sxs-lookup"><span data-stu-id="41b11-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="41b11-144">最重要的是了解用戶端與服務並未參與相同的交易；而是當使用佇列執行其作業 (例如傳送與接收) 時會使用不同的交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="41b11-145">在範例中，將針對執行多個服務作業使用單一交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="41b11-146">這項功能只會當做效能最佳化功能使用，而且不會影響應用程式的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="41b11-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="41b11-147">範例根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="41b11-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="41b11-148">註解</span><span class="sxs-lookup"><span data-stu-id="41b11-148">Comments</span></span>  
 <span data-ttu-id="41b11-149">在這個範例中，用戶端會從交易範圍內將訊息批次傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="41b11-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="41b11-150">若要顯示效能最佳化，可以傳送大量的訊息。在這個例子中，最多可以傳送 2500 則訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="41b11-151">接著，服務會在所定義的交易範圍內接收傳送至佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="41b11-152">沒有使用批次作業時，每次叫用服務作業就會產生 2500 筆交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="41b11-153">這樣就會影響系統的效能。</span><span class="sxs-lookup"><span data-stu-id="41b11-153">This impacts performance of the system.</span></span> <span data-ttu-id="41b11-154">由於在 MSMQ 佇列和 `Orders` 資料庫中牽涉到兩個資源管理員，因此這類交易就可說是 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="41b11-155">使用較少量的交易，確定訊息批次作業和服務作業叫用都是在單一交易上進行，即可最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="41b11-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="41b11-156">您可透過下列方式使用批次作業功能：</span><span class="sxs-lookup"><span data-stu-id="41b11-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="41b11-157">在組態中指定交易的批次處理行為。</span><span class="sxs-lookup"><span data-stu-id="41b11-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="41b11-158">指定批次大小，這是使用單一交易要讀取的訊息數。</span><span class="sxs-lookup"><span data-stu-id="41b11-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="41b11-159">指定要同時執行的批次作業數上限。</span><span class="sxs-lookup"><span data-stu-id="41b11-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="41b11-160">在此範例中，藉由降低交易數以確定認可交易之前會在單一交易上叫用 100 個服務作業，就可看到效能增益。</span><span class="sxs-lookup"><span data-stu-id="41b11-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="41b11-161">服務行為會定義 `TransactionScopeRequired` 已設為 `true` 的作業行為，</span><span class="sxs-lookup"><span data-stu-id="41b11-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="41b11-162">這樣會確定此方法存取的任何資源管理員都使用從佇列擷取訊息時所使用的相同交易範圍。</span><span class="sxs-lookup"><span data-stu-id="41b11-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="41b11-163">在此範例中，會使用基本資料庫來存放訊息中所含的訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="41b11-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="41b11-164">交易範圍也會保證在方法擲回例外狀況時，訊息仍會傳回佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="41b11-165">如果沒有設定這個作業行為，佇列通道就會建立交易，在分派訊息之前讀取佇列中的訊息並自動認可，因此若作業失敗，訊息就會遺失。</span><span class="sxs-lookup"><span data-stu-id="41b11-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="41b11-166">最常見的案例是服務作業登記在用來從佇列讀取訊息的交易中，如同下列程式碼所示範。</span><span class="sxs-lookup"><span data-stu-id="41b11-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="41b11-167">請注意，`ReleaseServiceInstanceOnTransactionComplete` 設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="41b11-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="41b11-168">這是批次作業的重要需求。</span><span class="sxs-lookup"><span data-stu-id="41b11-168">This is an important requirement for batching.</span></span> <span data-ttu-id="41b11-169">`ReleaseServiceInstanceOnTransactionComplete` 上的 `ServiceBehaviorAttribute` 屬性會指出完成交易之後，服務執行個體應該執行的動作。</span><span class="sxs-lookup"><span data-stu-id="41b11-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="41b11-170">根據預設，完成交易時會釋放服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="41b11-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="41b11-171">批次作業的核心觀念在於使用單一交易，就可讀取及分派佇列中的許多訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="41b11-172">因此，釋放服務執行個體就會永久停止完成交易，而不再使用批次作業。</span><span class="sxs-lookup"><span data-stu-id="41b11-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="41b11-173">如果這個屬性設定為 `true`，而且交易的批次處理行為已新增至端點，批次作業驗證行為就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41b11-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="41b11-174">`Orders` 類別會封裝訂單處理。</span><span class="sxs-lookup"><span data-stu-id="41b11-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="41b11-175">在此範例中，會使用訂單資訊更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="41b11-175">In the sample, it updates the database with purchase order information.</span></span>  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 <span data-ttu-id="41b11-176">會在服務應用程式組態中，指定批次作業行為與其組態。</span><span class="sxs-lookup"><span data-stu-id="41b11-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="41b11-177">批次大小對系統而言是一種提示。</span><span class="sxs-lookup"><span data-stu-id="41b11-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="41b11-178">例如，如果將批次大小指定為 20，則會使用單一交易讀取及分派 20 則訊息，然後認可交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="41b11-179">但在一些情況下，可能會在達到批次大小之前，交易就已認可批次。</span><span class="sxs-lookup"><span data-stu-id="41b11-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="41b11-180">與每個交易相關聯的項目為逾時，會在建立交易時立即開始計時。</span><span class="sxs-lookup"><span data-stu-id="41b11-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="41b11-181">此逾時到期時，就會中止交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="41b11-182">也可能在達到批次大小之前，此逾時就已到期。</span><span class="sxs-lookup"><span data-stu-id="41b11-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="41b11-183">為了避免由於中止而重新執行批次，`TransactedBatchingBehavior` 會查看還剩多少時間可以執行交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="41b11-184">如果已使用 80% 的交易逾時，就會認可交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="41b11-185">如果佇列中沒有其他訊息，則不會等待到達批次大小，<xref:System.ServiceModel.Description.TransactedBatchingBehavior> 就會認可交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="41b11-186">批次的大小是由您的應用程式所決定。</span><span class="sxs-lookup"><span data-stu-id="41b11-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="41b11-187">如果批次大小太小，可能不會得到希望的效能。</span><span class="sxs-lookup"><span data-stu-id="41b11-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="41b11-188">另一方面，如果批次大小太大，可能使效能下降。</span><span class="sxs-lookup"><span data-stu-id="41b11-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="41b11-189">例如，交易可以存留較久的時間並在資料庫上持有鎖定，或者應用程式變成鎖死，因而導致回復批次並重做工作。</span><span class="sxs-lookup"><span data-stu-id="41b11-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="41b11-190">用戶端會建立一個交易範圍。</span><span class="sxs-lookup"><span data-stu-id="41b11-190">The client creates a transaction scope.</span></span> <span data-ttu-id="41b11-191">與佇列的通訊會發生在交易範圍內，導致其被視為原子單位 (Atomic Unit)，其中會將所有訊息都傳送至佇列，或是不傳送任何訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="41b11-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="41b11-192">呼叫交易範圍上的 <xref:System.Transactions.TransactionScope.Complete%2A>，即可認可交易。</span><span class="sxs-lookup"><span data-stu-id="41b11-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="41b11-193">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="41b11-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="41b11-194">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="41b11-195">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="41b11-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="41b11-196">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="41b11-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="41b11-197">您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="41b11-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="41b11-198">以批次讀取訊息及處理訊息時，您會看到可以捲動的輸出。</span><span class="sxs-lookup"><span data-stu-id="41b11-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="41b11-199">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="41b11-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="41b11-200">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="41b11-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="41b11-201">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="41b11-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41b11-202">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="41b11-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="41b11-203">請參閱</span><span class="sxs-lookup"><span data-stu-id="41b11-203">See Also</span></span>
