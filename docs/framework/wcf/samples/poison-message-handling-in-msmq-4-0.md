---
title: MSMQ 4.0 中的有害訊息處理
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: d0ddab7832e308336d5bfb1c5f75fd13fe63fe72
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="e7214-102">MSMQ 4.0 中的有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="e7214-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="e7214-103">這個範例會示範如何在服務中執行有害訊息處理。</span><span class="sxs-lookup"><span data-stu-id="e7214-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="e7214-104">這個範例根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="e7214-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="e7214-105">這個範例會使用 `netMsmqBinding`。</span><span class="sxs-lookup"><span data-stu-id="e7214-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="e7214-106">這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="e7214-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="e7214-107">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="e7214-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="e7214-108">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="e7214-109">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-109">The service receives messages from the queue.</span></span> <span data-ttu-id="e7214-110">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="e7214-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="e7214-111">有害訊息是指會從佇列反覆讀取的訊息，此時讀取該訊息的服務無法處理訊息，因而終止訊息讀取時所位於的交易。</span><span class="sxs-lookup"><span data-stu-id="e7214-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="e7214-112">此時，服務會重試訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="e7214-113">如果訊息有問題，理論上這種情形會不斷發生。</span><span class="sxs-lookup"><span data-stu-id="e7214-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="e7214-114">請注意，只有當您使用交易來讀取佇列並叫用服務作業時，才會發生這個情況。</span><span class="sxs-lookup"><span data-stu-id="e7214-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>  
  
 <span data-ttu-id="e7214-115">根據 MSMQ 的版本，NetMsmqBinding 支援有害訊息的有限到完整偵測。</span><span class="sxs-lookup"><span data-stu-id="e7214-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="e7214-116">訊息已偵測為有害之後，有多種方法可以處理此訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="e7214-117">同樣地，根據 MSMQ 的版本，NetMsmqBinding 會支援完整處理有害訊息的有限處理功能。</span><span class="sxs-lookup"><span data-stu-id="e7214-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>  
  
 <span data-ttu-id="e7214-118">這個範例會示範 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 平台上提供的有限有害訊息處理功能，以及 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上提供的完整有害訊息處理功能。</span><span class="sxs-lookup"><span data-stu-id="e7214-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="e7214-119">這兩個範例的目標都是要將有害訊息從佇列移出至其他佇列，以便有害訊息服務可以接著處理這些有害訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>  
  
## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="e7214-120">MSMQ v4.0 有害訊息處理範例</span><span class="sxs-lookup"><span data-stu-id="e7214-120">MSMQ v4.0 Poison Handling Sample</span></span>  
 <span data-ttu-id="e7214-121">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，MSMQ 會提供能夠用來儲存有害訊息的有害訊息子佇列功能。</span><span class="sxs-lookup"><span data-stu-id="e7214-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="e7214-122">這個範例會示範使用 [!INCLUDE[wv](../../../../includes/wv-md.md)] 處理有害訊息的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="e7214-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="e7214-123">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，有害訊息偵測功能已經相當成熟。</span><span class="sxs-lookup"><span data-stu-id="e7214-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="e7214-124">有三個屬性能夠協助偵測。</span><span class="sxs-lookup"><span data-stu-id="e7214-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="e7214-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 是從佇列重新讀取指定訊息、並接著分派至應用程式以便進行處理的次數。</span><span class="sxs-lookup"><span data-stu-id="e7214-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="e7214-126">因為訊息無法分派至應用程式，或應用程式在服務作業中回復交易而使訊息放回佇列時，該訊息就會從佇列重新讀取。</span><span class="sxs-lookup"><span data-stu-id="e7214-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="e7214-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> 是將訊息移至重試佇列的次數。</span><span class="sxs-lookup"><span data-stu-id="e7214-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="e7214-128">當達到 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 時，訊息就會移至重試佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="e7214-129"><xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> 屬性是指時間延遲，在經過此段時間之後，訊息就會從重試佇列移回主要佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="e7214-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 會重設為 0。</span><span class="sxs-lookup"><span data-stu-id="e7214-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="e7214-131">這時訊息會再試一次。</span><span class="sxs-lookup"><span data-stu-id="e7214-131">The message is tried again.</span></span> <span data-ttu-id="e7214-132">如果讀取訊息的所有嘗試都失敗，該訊息就會被標記為有害。</span><span class="sxs-lookup"><span data-stu-id="e7214-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>  
  
 <span data-ttu-id="e7214-133">一旦訊息標記為有害，該訊息就會根據 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 列舉中的設定加以處理。</span><span class="sxs-lookup"><span data-stu-id="e7214-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="e7214-134">若要重新逐一查看可能的值：</span><span class="sxs-lookup"><span data-stu-id="e7214-134">To reiterate the possible values:</span></span>  
  
-   <span data-ttu-id="e7214-135">Fault (預設)：使接聽程式和服務主機發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7214-135">Fault (default): To fault the listener and also the service host.</span></span>  
  
-   <span data-ttu-id="e7214-136">Drop：捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-136">Drop: To drop the message.</span></span>  
  
-   <span data-ttu-id="e7214-137">Move：將訊息移至有害訊息子佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="e7214-138">這個值只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="e7214-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
-   <span data-ttu-id="e7214-139">Reject：拒絕訊息，並將訊息傳回至傳送者之寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="e7214-140">這個值只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="e7214-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="e7214-141">此範例會示範對有害訊息使用 `Move` 處置。</span><span class="sxs-lookup"><span data-stu-id="e7214-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="e7214-142">`Move` 會導致訊息移至有害子佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-142">`Move` causes the message to move to the poison sub-queue.</span></span>  
  
 <span data-ttu-id="e7214-143">服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="e7214-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="e7214-144">服務作業會顯示訊息，指出正在處理訂單。</span><span class="sxs-lookup"><span data-stu-id="e7214-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="e7214-145">為了示範有害訊息功能，`SubmitPurchaseOrder` 服務作業會擲回例外狀況，以復原在隨機叫用服務時的交易。</span><span class="sxs-lookup"><span data-stu-id="e7214-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="e7214-146">這樣會導致訊息必須放回佇列中。</span><span class="sxs-lookup"><span data-stu-id="e7214-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="e7214-147">最後，訊息會標示為有害。</span><span class="sxs-lookup"><span data-stu-id="e7214-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="e7214-148">組態會設定成將有害訊息移至有害訊息子佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    static Random r = new Random(137);  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
  
        int randomNumber = r.Next(10);  
  
        if (randomNumber % 2 == 0)  
        {  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
        else  
        {  
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);  
            Console.WriteLine();  
            throw new Exception("Cannot process purchase order: " + po.PONumber);  
        }  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted");  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration.  
        string queueName = ConfigurationManager.AppSettings["queueName"];  
  
        // Create the transacted MSMQ queue if necessary.  
        if (!System.Messaging.MessageQueue.Exists(queueName))  
            System.Messaging.MessageQueue.Create(queueName, true);  
  
        // Get the base address that is used to listen for WS-MetaDataExchange requests.  
        // This is useful to generate a proxy for the client.  
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        if(serviceHost.State != CommunicationState.Faulted) {  
            serviceHost.Close();  
        }  
  
    }  
}  
```

 <span data-ttu-id="e7214-149">服務組態包括下列有害訊息屬性：`receiveRetryCount`、`maxRetryCycles`、`retryCycleDelay` 和 `receiveErrorHandling`，如下列組態檔所示。</span><span class="sxs-lookup"><span data-stu-id="e7214-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />  
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>  
  </appSettings>  
  <system.serviceModel>  
    <services>  
      <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="PoisonBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PoisonBinding"   
                 receiveRetryCount="0"  
                 maxRetryCycles="1"  
                 retryCycleDelay="00:00:05"                        
                 receiveErrorHandling="Move">  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="e7214-150">處理有害訊息佇列中的訊息</span><span class="sxs-lookup"><span data-stu-id="e7214-150">Processing messages from the poison message queue</span></span>  
 <span data-ttu-id="e7214-151">有害訊息服務會讀取最終有害訊息佇列中的訊息，並處理這些訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>  
  
 <span data-ttu-id="e7214-152">有害訊息佇列中的訊息是指定址到正在處理這些訊息之服務的訊息，這個服務與有害訊息服務端點可能不同。</span><span class="sxs-lookup"><span data-stu-id="e7214-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="e7214-153">因此，當有害訊息服務從佇列讀取訊息，WCF 通道層會發覺端點中，而且不會分派訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="e7214-154">此時，該訊息是定址到訂單處理服務，但卻是由有害訊息服務接收。</span><span class="sxs-lookup"><span data-stu-id="e7214-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="e7214-155">即使訊息是定址到其他端點，若要繼續接收訊息，我們就必須新增 `ServiceBehavior`，以便篩選比對準則要比對訊息定址到的任何服務端點時的所在位址。</span><span class="sxs-lookup"><span data-stu-id="e7214-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="e7214-156">若要成功處理從有害訊息佇列中讀取的訊息，您就必須執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="e7214-156">This is required to successfully process messages that you read from the poison message queue.</span></span>  
  
 <span data-ttu-id="e7214-157">有害訊息服務實作本身與服務實作非常相似，</span><span class="sxs-lookup"><span data-stu-id="e7214-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="e7214-158">它會實作合約並處理訂單。</span><span class="sxs-lookup"><span data-stu-id="e7214-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="e7214-159">程式碼範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="e7214-159">The code example is as follows.</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted...exiting app");  
        Environment.Exit(1);  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The poison message service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHostBase to shutdown the service.  
        if(serviceHost.State != CommunicationState.Faulted)  
        {  
            serviceHost.Close();  
        }  
    }  
```

 <span data-ttu-id="e7214-160">與從訂單佇列中讀取訊息的訂單處理服務不同，有害訊息服務會從有害子佇列中讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="e7214-161">有害佇列是主要佇列的子佇列，名為 "poison" 且由 MSMQ 自動產生。</span><span class="sxs-lookup"><span data-stu-id="e7214-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="e7214-162">若要存取有害佇列，請提供後面加上 ";" 的主要佇列名稱和子佇列名稱 (在此範例中為 -"poison")，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="e7214-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7214-163">在 MSMQ v3.0 的範例中，有害佇列名稱不是子佇列，而是我們將訊息移至其中的佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >  
        </endpoint>  
      </service>  
    </services>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e7214-164">當您執行範例時，用戶端、服務和有害訊息服務活動都會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e7214-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="e7214-165">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="e7214-166">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務。</span><span class="sxs-lookup"><span data-stu-id="e7214-166">Press ENTER in each console window to shut down the services.</span></span>  
  
 <span data-ttu-id="e7214-167">服務會開始執行、處理訂單，並隨機終止處理。</span><span class="sxs-lookup"><span data-stu-id="e7214-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="e7214-168">如果訊息指出其已處理訂單，您就可以再次執行用戶端來傳送其他訊息，直到您清楚該服務已確實終止訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="e7214-169">根據設定的有害訊息設定，訊息會在移至最終有害佇列之前嘗試經過處理一次。</span><span class="sxs-lookup"><span data-stu-id="e7214-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
```  
  
 <span data-ttu-id="e7214-170">啟動有害訊息服務，即可從有害佇列讀取有害訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="e7214-171">在這個範例中，有害訊息服務會讀取並處理訊息。</span><span class="sxs-lookup"><span data-stu-id="e7214-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="e7214-172">您會發現已終止和已標記為有害的採購單會由有害訊息服務所讀取。</span><span class="sxs-lookup"><span data-stu-id="e7214-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e7214-173">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e7214-173">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e7214-174">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e7214-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e7214-175">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="e7214-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="e7214-176">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="e7214-177">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="e7214-178">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="e7214-178">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="e7214-179">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="e7214-179">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="e7214-180">展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e7214-180">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="e7214-181">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="e7214-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="e7214-182">請檢查**交易式**方塊。</span><span class="sxs-lookup"><span data-stu-id="e7214-182">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="e7214-183">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7214-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="e7214-184">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e7214-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e7214-185">若要在單一或跨電腦組態中執行範例時，變更 佇列名稱，以反映實際主機名稱，而不是 localhost，然後依照[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e7214-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="e7214-186">根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。</span><span class="sxs-lookup"><span data-stu-id="e7214-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="e7214-187">`MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。</span><span class="sxs-lookup"><span data-stu-id="e7214-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="e7214-188">根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="e7214-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="e7214-189">若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7214-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="e7214-190">如果您在不屬於網域的電腦上執行這個範例，就會收到下列錯誤：「使用者的內部訊息佇列憑證不存在」。</span><span class="sxs-lookup"><span data-stu-id="e7214-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="e7214-191">若要在加入至工作群組的電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="e7214-191">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="e7214-192">如果您的電腦不是網域的一部分，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="e7214-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="e7214-193">請透過設定端點的 bindingConfiguration 屬性，確定端點與繫結相關聯。</span><span class="sxs-lookup"><span data-stu-id="e7214-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>  
  
2.  <span data-ttu-id="e7214-194">請務必先變更 PoisonMessageServer、伺服器和用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="e7214-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7214-195">將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="e7214-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="e7214-196">若要讓中繼資料交換正常運作，我們要向 http 繫結登錄 URL。</span><span class="sxs-lookup"><span data-stu-id="e7214-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="e7214-197">這時需要在更高權限的命令視窗中執行服務。</span><span class="sxs-lookup"><span data-stu-id="e7214-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="e7214-198">否則，您如收到例外狀況： 未處理例外狀況： System.ServiceModel.AddressAccessDeniedException: HTTP 無法登錄 URL http://+:8000/ServiceModelSamples/service/。</span><span class="sxs-lookup"><span data-stu-id="e7214-198">Otherwise, you get an exception such as: Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/.</span></span> <span data-ttu-id="e7214-199">您的程序並沒有此命名空間的存取權限 (請參閱http://go.microsoft.com/fwlink/?LinkId=70353如需詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="e7214-199">Your process does not have access rights to this namespace (see http://go.microsoft.com/fwlink/?LinkId=70353 for details).</span></span> <span data-ttu-id="e7214-200">---> System.Net.HttpListenerException: 拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="e7214-200">---> System.Net.HttpListenerException: Access is denied.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7214-201">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e7214-201">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e7214-202">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e7214-202">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7214-203">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e7214-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7214-204">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e7214-204">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a><span data-ttu-id="e7214-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7214-205">See Also</span></span>
