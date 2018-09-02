---
title: 訊息佇列至 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 983fd2ef7338e24c67e3556849e73c2feaf97a60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423370"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="a0c8c-102">訊息佇列至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a0c8c-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="a0c8c-103">此範例示範訊息佇列 (MSMQ) 應用程式如何將 MSMQ 訊息傳送至 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a0c8c-104">這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="a0c8c-105">服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="a0c8c-106">MSMQ 訊息沒有 Action 標頭，所以不可能自動將不同 MSMQ 訊息對應到作業合約。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="a0c8c-107">因此，這時只能有一個作業合約。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="a0c8c-108">如果您想要為服務定義一個以上的作業合約，應用程式就必須提供資訊，說明 MSMQ 訊息中的哪個標頭 (例如，標籤或 correlationID) 可以用來決定分派哪個作業合約。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="a0c8c-109">這示範於[自訂 Demux](../../../../docs/framework/wcf/samples/custom-demux.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="a0c8c-110">MSMQ 訊息不會包含有關作業合約的不同參數各自對應到哪個標頭的資訊。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="a0c8c-111">參數的型別是 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`)，其中包含基礎 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="a0c8c-112"><xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) 類別中的型別 "T" 代表已序列化為 MSMQ 訊息本文的資料。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="a0c8c-113">在這個範例中，`PurchaseOrder` 型別會序列化為 MSMQ 訊息本文。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="a0c8c-114">下列範例程式碼會示範訂單處理服務的服務合約。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-114">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 <span data-ttu-id="a0c8c-115">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-115">The service is self hosted.</span></span> <span data-ttu-id="a0c8c-116">使用 MSMQ 時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="a0c8c-117">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-117">This can be done manually or through code.</span></span> <span data-ttu-id="a0c8c-118">在這個範例中，服務會檢查佇列的存在，並在需要時建立佇列。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="a0c8c-119">佇列名稱會從組態檔中讀取。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-119">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```

 <span data-ttu-id="a0c8c-120">服務會建立並開啟 <xref:System.ServiceModel.ServiceHost> 的 `OrderProcessorService`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="a0c8c-121">MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中，如下面的範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c8c-122">佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="a0c8c-123">WCF 端點位址會指定 msmq.formatname 配置，並使用 localhost 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="a0c8c-124">每個 MSMQ 格式名稱定址方針的佇列位址會遵循 msmq.formatname 配置。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="a0c8c-125">用戶端應用程式是使用 <xref:System.Messaging.MessageQueue.Send%2A> 方法將永久和交易訊息傳送至佇列的 MSMQ 應用程式，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  

```csharp
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
// Create the purchase order.  
PurchaseOrder po = new PurchaseOrder();  
po.CustomerId = "somecustomer.com";  
po.PONumber = Guid.NewGuid().ToString();  
  
PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
lineItem1.ProductId = "Blue Widget";  
lineItem1.Quantity = 54;  
lineItem1.UnitCost = 29.99F;  
  
PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
lineItem2.ProductId = "Red Widget";  
lineItem2.Quantity = 890;  
lineItem2.UnitCost = 45.89F;  
  
po.orderLineItems = new PurchaseOrderLineItem[2];  
po.orderLineItems[0] = lineItem1;  
po.orderLineItems[1] = lineItem2;  
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="a0c8c-126">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a0c8c-127">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="a0c8c-128">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="a0c8c-129">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="a0c8c-130">例如，您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="a0c8c-131">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a0c8c-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a0c8c-132">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a0c8c-133">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="a0c8c-134">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="a0c8c-135">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="a0c8c-136">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="a0c8c-137">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="a0c8c-138">依序展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="a0c8c-139">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="a0c8c-140">請檢查**Transactional**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="a0c8c-141">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="a0c8c-142">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="a0c8c-143">若要在單一電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a0c8c-144">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="a0c8c-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a0c8c-145">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="a0c8c-146">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="a0c8c-147">在 Client.exe.config 檔案中，變更 orderQueueName 以取代 "." 指定服務電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="a0c8c-148">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="a0c8c-149">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0c8c-150">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a0c8c-151">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0c8c-152">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0c8c-153">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a0c8c-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="a0c8c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c8c-154">See Also</span></span>  
 [<span data-ttu-id="a0c8c-155">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="a0c8c-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="a0c8c-156">如何：與 WCF 端點和訊息佇列應用程式交換訊息</span><span class="sxs-lookup"><span data-stu-id="a0c8c-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="a0c8c-157">訊息佇列</span><span class="sxs-lookup"><span data-stu-id="a0c8c-157">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
