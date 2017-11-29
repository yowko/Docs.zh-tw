---
title: "Windows Communication Foundation 至訊息佇列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6800db4e5f8dc1a0d571be3eed556503b907e16e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="a8cfb-102">Windows Communication Foundation 至訊息佇列</span><span class="sxs-lookup"><span data-stu-id="a8cfb-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="a8cfb-103">這個範例會示範 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式如何將訊息傳送至訊息佇列 (MSMQ) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-103">This sample demonstrates how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="a8cfb-104">這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="a8cfb-105">服務與用戶端不需要在相同時間執行。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="a8cfb-106">服務會接收佇列訊息，然後處理訂單。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="a8cfb-107">服務會建立交易式佇列，然後設定已接收訊息的訊息處理常式，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="a8cfb-108">當訊息是由佇列接收時，就會叫用訊息處理常式 `ProcessOrder`。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```  
  
 <span data-ttu-id="a8cfb-109">服務會從 MSMQ 訊息本文擷取 `ProcessOrder`，然後處理訂單。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="a8cfb-110">MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中，如下面的範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="a8cfb-111">佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="a8cfb-112">用戶端會建立採購單，然後在交易範圍內提交採購單，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="a8cfb-113">用戶端會依序使用自訂用戶端，將 MSMQ 訊息傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="a8cfb-114">由於接收和處理訊息的應用程式是 MSMQ 應用程式，而非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式，所以兩個應用程式之間沒有隱含的服務合約。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-114">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="a8cfb-115">因此，我們無法在這個案例中使用 Svcutil.exe 工具來建立 Proxy。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="a8cfb-116">對所有使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結傳送訊息的 `MsmqIntegration` 應用程式來說，自訂用戶端基本上都相同。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-116">The custom client is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="a8cfb-117">與其他用戶端不同的是，它並不包含服務作業的範圍，</span><span class="sxs-lookup"><span data-stu-id="a8cfb-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="a8cfb-118">而只是一項送出訊息的作業。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-118">It is a submit message operation only.</span></span>  
  
```  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 <span data-ttu-id="a8cfb-119">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a8cfb-120">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="a8cfb-121">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="a8cfb-122">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="a8cfb-123">例如，您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8cfb-124">這個範例需要安裝訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="a8cfb-125">請參閱安裝指示[訊息佇列](http://go.microsoft.com/fwlink/?LinkId=94968)。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-125">See the installation instructions in [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="a8cfb-126">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a8cfb-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8cfb-127">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8cfb-128">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="a8cfb-129">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="a8cfb-130">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="a8cfb-131">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="a8cfb-132">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="a8cfb-133">展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="a8cfb-134">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="a8cfb-135">請檢查**交易式**方塊。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="a8cfb-136">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="a8cfb-137">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="a8cfb-138">若要在單一電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a8cfb-139">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="a8cfb-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a8cfb-140">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="a8cfb-141">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="a8cfb-142">在 Client.exe.config 檔案中，變更用戶端端點位址以取代 "." 指定服務電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="a8cfb-143">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="a8cfb-144">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8cfb-145">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a8cfb-146">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8cfb-147">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8cfb-148">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a8cfb-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="a8cfb-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8cfb-149">See Also</span></span>  
 [<span data-ttu-id="a8cfb-150">如何： 與 WCF 端點交換訊息和訊息佇列應用程式</span><span class="sxs-lookup"><span data-stu-id="a8cfb-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="a8cfb-151">訊息佇列</span><span class="sxs-lookup"><span data-stu-id="a8cfb-151">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
