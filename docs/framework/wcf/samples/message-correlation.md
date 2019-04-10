---
title: 訊息相互關聯
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: ed6fc8f5d16ae2d604cdbdf4659ecfaaa83bfa02
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333271"
---
# <a name="message-correlation"></a><span data-ttu-id="be3af-102">訊息相互關聯</span><span class="sxs-lookup"><span data-stu-id="be3af-102">Message Correlation</span></span>
<span data-ttu-id="be3af-103">此範例示範訊息佇列 (MSMQ) 應用程式如何將 MSMQ 訊息傳送至 Windows Communication Foundation (WCF) 服務，以及如何訊息可以相互關聯的要求/回應案例中的傳送者與接收者應用程式之間。</span><span class="sxs-lookup"><span data-stu-id="be3af-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="be3af-104">這個範例會使用 msmqIntegrationBinding 繫結。</span><span class="sxs-lookup"><span data-stu-id="be3af-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="be3af-105">本實例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="be3af-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="be3af-106">K</span><span class="sxs-lookup"><span data-stu-id="be3af-106">k</span></span>  
  
 <span data-ttu-id="be3af-107">這個服務會處理從傳送者接收的訊息，再將回應訊息傳回給傳送者。</span><span class="sxs-lookup"><span data-stu-id="be3af-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="be3af-108">傳送者會將收到的回應與它原先傳送的要求相互關聯。</span><span class="sxs-lookup"><span data-stu-id="be3af-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="be3af-109">訊息的 `MessageID` 和 `CorrelationID` 屬性是用來使要求與回應訊息產生相互關聯。</span><span class="sxs-lookup"><span data-stu-id="be3af-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="be3af-110">`IOrderProcessor` 服務合約會定義適合與佇列一起使用的單向服務作業。</span><span class="sxs-lookup"><span data-stu-id="be3af-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="be3af-111">MSMQ 訊息沒有 Action 標頭，所以不可能自動將不同 MSMQ 訊息對應到作業合約。</span><span class="sxs-lookup"><span data-stu-id="be3af-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="be3af-112">因此，這種情況下只能有一個作業合約。</span><span class="sxs-lookup"><span data-stu-id="be3af-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="be3af-113">如果您想要在服務中定義更多的作業合約，應用程式就必須提供資訊，說明 MSMQ 訊息中的哪個標頭 (例如，標籤或 correlationID) 可以用來決定分派哪個作業合約。</span><span class="sxs-lookup"><span data-stu-id="be3af-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> 
  
 <span data-ttu-id="be3af-114">MSMQ 訊息也不會包含有關作業合約的不同參數各自對應到哪個標頭的資訊。</span><span class="sxs-lookup"><span data-stu-id="be3af-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="be3af-115">因此，在作業合約中只能有一個參數。</span><span class="sxs-lookup"><span data-stu-id="be3af-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="be3af-116">參數的類型是<xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>，其中包含基礎 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="be3af-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="be3af-117">`MsmqMessage<T>` 類別中的型別 "T" 代表已序列化為 MSMQ 訊息本文的資料。</span><span class="sxs-lookup"><span data-stu-id="be3af-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="be3af-118">在這個範例中，`PurchaseOrder` 型別會序列化為 MSMQ 訊息本文。</span><span class="sxs-lookup"><span data-stu-id="be3af-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="be3af-119">服務作業會處理採購單，並在服務主控台視窗中顯示採購單內容及其狀態。</span><span class="sxs-lookup"><span data-stu-id="be3af-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="be3af-120"><xref:System.ServiceModel.OperationBehaviorAttribute> 將作業設定為先向佇列登記異動，然後在作業回傳時標記異動完成。</span><span class="sxs-lookup"><span data-stu-id="be3af-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="be3af-121">`PurchaseOrder` 包含必須由服務進行處理的採購單明細。</span><span class="sxs-lookup"><span data-stu-id="be3af-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="be3af-122">服務會使用自訂用戶端 `OrderResponseClient`，將 MSMQ 訊息傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="be3af-123">接收和處理訊息的應用程式是 MSMQ 應用程式並是 WCF 應用程式，因為沒有隱含的服務合約之間兩個應用程式。</span><span class="sxs-lookup"><span data-stu-id="be3af-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="be3af-124">因此，我們無法在這個案例中使用 Svcutil.exe 工具來建立 Proxy。</span><span class="sxs-lookup"><span data-stu-id="be3af-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="be3af-125">自訂 proxy 基本上是相同的所有 WCF 應用程式使用`msmqIntegrationBinding`繫結傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="be3af-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="be3af-126">與其他 Proxy 不同的是，它並不包含服務作業的範圍，</span><span class="sxs-lookup"><span data-stu-id="be3af-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="be3af-127">而只是一項送出訊息的作業。</span><span class="sxs-lookup"><span data-stu-id="be3af-127">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="be3af-128">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="be3af-128">The service is self hosted.</span></span> <span data-ttu-id="be3af-129">使用 MSMQ 整合傳輸時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="be3af-130">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="be3af-130">This can be done manually or through code.</span></span> <span data-ttu-id="be3af-131">在這個範例中，服務包含檢查佇列是否存在並在需要時建立佇列的 <xref:System.Messaging> 程式碼。</span><span class="sxs-lookup"><span data-stu-id="be3af-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="be3af-132">佇列名稱會從組態檔中讀取。</span><span class="sxs-lookup"><span data-stu-id="be3af-132">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
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

 <span data-ttu-id="be3af-133">傳送訂單要求的 MSMQ 佇列可以在組態檔的 appSettings 區段中指定。</span><span class="sxs-lookup"><span data-stu-id="be3af-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="be3af-134">用戶端和服務端點則是在組態檔的 system.serviceModel 區段中定義。</span><span class="sxs-lookup"><span data-stu-id="be3af-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="be3af-135">這兩個都會指定 `msmqIntegrationbinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="be3af-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="be3af-136">用戶端應用程式會使用 <xref:System.Messaging>，傳送永久性的交易式訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="be3af-137">訊息的本文會包含採購單。</span><span class="sxs-lookup"><span data-stu-id="be3af-137">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="be3af-138">接收訂單回應的 MSMQ 佇列是在組態檔的 appSettings 區段中指定，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="be3af-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="be3af-139">佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="be3af-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="be3af-140">WCF 端點位址會指定 msmq.formatname 配置，並使用"localhost"代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="be3af-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="be3af-141">根據 MSMQ 方針，正確的格式名稱應遵照 URI 中的 msmq.formatname。</span><span class="sxs-lookup"><span data-stu-id="be3af-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="be3af-142">用戶端應用程式會儲存其傳送至服務之訂單要求訊息的 `messageID`，並等候服務的回應。</span><span class="sxs-lookup"><span data-stu-id="be3af-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="be3af-143">一旦回應抵達佇列，用戶端就會使用訊息的 `correlationID` 屬性 (其中包含用戶端原先傳送至服務之訂單訊息的 `messageID`)，將此回應與它所傳送的訂單訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="be3af-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="be3af-144">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="be3af-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="be3af-145">您可以看到服務從用戶端接收訊息，再將回應傳送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="be3af-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="be3af-146">用戶端會顯示從服務收到的回應。</span><span class="sxs-lookup"><span data-stu-id="be3af-146">The client displays the response received from the service.</span></span> <span data-ttu-id="be3af-147">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="be3af-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="be3af-148">這個範例需要安裝訊息佇列 (MSMQ)。</span><span class="sxs-lookup"><span data-stu-id="be3af-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="be3af-149">請參閱「請參閱」一節中的 MSMQ 安裝指示。</span><span class="sxs-lookup"><span data-stu-id="be3af-149">See the MSMQ installation instructions in the See Also section.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="be3af-150">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="be3af-150">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="be3af-151">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="be3af-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="be3af-152">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="be3af-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="be3af-153">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="be3af-154">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="be3af-155">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="be3af-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="be3af-156">開啟 Visual Studio 2012 中的 伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="be3af-156">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="be3af-157">依序展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="be3af-157">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="be3af-158">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="be3af-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="be3af-159">請檢查**Transactional**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="be3af-159">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="be3af-160">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="be3af-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="be3af-161">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="be3af-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="be3af-162">若要在單一電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="be3af-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="be3af-163">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="be3af-163">To run the sample across computers</span></span>

1. <span data-ttu-id="be3af-164">將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="be3af-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="be3af-165">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="be3af-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="be3af-166">在 Client.exe.config 檔案中，變更 orderQueueName 以取代 "." 指定服務電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="be3af-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="be3af-167">在 Service.exe.config 檔案中，變更用戶端端點位址以取代 "." 指定用戶端電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="be3af-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="be3af-168">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="be3af-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="be3af-169">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="be3af-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="be3af-170">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="be3af-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="be3af-171">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="be3af-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be3af-172">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="be3af-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be3af-173">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="be3af-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="be3af-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be3af-174">See also</span></span>

- [<span data-ttu-id="be3af-175">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="be3af-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="be3af-176">訊息佇列</span><span class="sxs-lookup"><span data-stu-id="be3af-176">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
