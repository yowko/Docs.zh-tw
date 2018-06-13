---
title: 自訂 Demux
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: e88672f152b87740feef1345b3eac213916a1527
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805560"
---
# <a name="custom-demux"></a><span data-ttu-id="c5956-102">自訂 Demux</span><span class="sxs-lookup"><span data-stu-id="c5956-102">Custom Demux</span></span>
<span data-ttu-id="c5956-103">這個範例會示範如何 MSMQ 訊息標頭會對應至不同的服務作業，讓 Windows Communication Foundation (WCF) 服務使用<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>不限於使用一項服務作業中所示[訊息佇列至 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)和[Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)範例。</span><span class="sxs-lookup"><span data-stu-id="c5956-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that Windows Communication Foundation (WCF) services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="c5956-104">這個範例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="c5956-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="c5956-105">服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="c5956-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 <span data-ttu-id="c5956-106">MSMQ 訊息沒有 Action 標頭。</span><span class="sxs-lookup"><span data-stu-id="c5956-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="c5956-107">無法將不同的 MSMQ 訊息自動對應至作業合約。</span><span class="sxs-lookup"><span data-stu-id="c5956-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="c5956-108">因此，這時只能有一個作業合約。</span><span class="sxs-lookup"><span data-stu-id="c5956-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="c5956-109">為了克服這項限制，服務會實作 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> 介面的 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 方法。</span><span class="sxs-lookup"><span data-stu-id="c5956-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="c5956-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> 方法能夠讓服務將指定的訊息標頭對應至特定服務作業。</span><span class="sxs-lookup"><span data-stu-id="c5956-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="c5956-111">在這個範例中，訊息的標籤標頭會對應至服務作業。</span><span class="sxs-lookup"><span data-stu-id="c5956-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="c5956-112">作業合約的 `Name` 參數會判定必須將指定訊息標籤分派到其中的服務作業。</span><span class="sxs-lookup"><span data-stu-id="c5956-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="c5956-113">例如，如果訊息的標籤標頭包含 "SubmitPurchaseOrder"，就會叫用 "SubmitPurchaseOrder" 服務作業。</span><span class="sxs-lookup"><span data-stu-id="c5956-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 <span data-ttu-id="c5956-114">服務必須實作 <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> 介面的 <xref:System.ServiceModel.Description.IContractBehavior> 方法，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c5956-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="c5956-115">這會將自訂 `OperationSelector` 套用至服務架構分派執行階段。</span><span class="sxs-lookup"><span data-stu-id="c5956-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 <span data-ttu-id="c5956-116">在執行至 OperationSelector 之前，訊息必須通過發送器的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>。</span><span class="sxs-lookup"><span data-stu-id="c5956-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="c5956-117">根據預設，如果在服務實作之任何合約上都找不到訊息的動作，該訊息就會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="c5956-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="c5956-118">為了避免這項檢查，我們會實作名為 <xref:System.ServiceModel.Description.IEndpointBehavior> 的 `MatchAllFilterBehavior`，此行為會藉由套用 `ContractFilter` 讓任何訊息通過 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，如下列所示。</span><span class="sxs-lookup"><span data-stu-id="c5956-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 <span data-ttu-id="c5956-119">當服務接收到訊息時，便會使用該標籤標頭提供的資訊分派適當的服務作業。</span><span class="sxs-lookup"><span data-stu-id="c5956-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="c5956-120">訊息本文會還原序列化為 `PurchaseOrder` 物件，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c5956-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 <span data-ttu-id="c5956-121">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="c5956-121">The service is self-hosted.</span></span> <span data-ttu-id="c5956-122">使用 MSMQ 時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="c5956-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="c5956-123">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="c5956-123">This can be done manually or through code.</span></span> <span data-ttu-id="c5956-124">在這個範例中，該服務包含的程式碼會檢查佇列的存在，並在佇列不存在時建立佇列。</span><span class="sxs-lookup"><span data-stu-id="c5956-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="c5956-125">佇列名稱會從組態檔中讀取。</span><span class="sxs-lookup"><span data-stu-id="c5956-125">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```

 <span data-ttu-id="c5956-126">MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。</span><span class="sxs-lookup"><span data-stu-id="c5956-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5956-127">佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c5956-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="c5956-128">WCF 端點位址會指定 msmq.formatname 配置，並使用 localhost 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c5956-128">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="c5956-129">在配置後面的是根據 MSMQ 格式名稱定址方針而正確格式化的佇列位址。</span><span class="sxs-lookup"><span data-stu-id="c5956-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="c5956-130">這個範例需要安裝[訊息佇列](http://go.microsoft.com/fwlink/?LinkId=95143)。</span><span class="sxs-lookup"><span data-stu-id="c5956-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="c5956-131">啟動服務，並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="c5956-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="c5956-132">下列輸出會顯示在用戶端上。</span><span class="sxs-lookup"><span data-stu-id="c5956-132">The following output is seen on the client.</span></span>  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c5956-133">下列輸出一定會出現在服務上。</span><span class="sxs-lookup"><span data-stu-id="c5956-133">The following output must be seen on the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c5956-134">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c5956-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c5956-135">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c5956-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c5956-136">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="c5956-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c5956-137">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="c5956-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c5956-138">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="c5956-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c5956-139">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="c5956-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="c5956-140">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="c5956-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="c5956-141">展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c5956-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="c5956-142">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="c5956-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="c5956-143">請檢查**交易式**方塊。</span><span class="sxs-lookup"><span data-stu-id="c5956-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="c5956-144">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5956-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="c5956-145">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="c5956-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c5956-146">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c5956-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c5956-147">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="c5956-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="c5956-148">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="c5956-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="c5956-149">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="c5956-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="c5956-150">在 Client.exe.config 檔案中，變更 orderQueueName 以取代 "." 指定服務電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c5956-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="c5956-151">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="c5956-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="c5956-152">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="c5956-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5956-153">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c5956-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c5956-154">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c5956-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5956-155">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="c5956-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5956-156">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c5956-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="c5956-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5956-157">See Also</span></span>  
 [<span data-ttu-id="c5956-158">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="c5956-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="c5956-159">訊息佇列</span><span class="sxs-lookup"><span data-stu-id="c5956-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)
