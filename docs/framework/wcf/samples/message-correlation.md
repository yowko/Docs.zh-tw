---
title: 訊息相互關聯
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: f60d34ba7348b75f10be326319738fd1555d42df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520655"
---
# <a name="message-correlation"></a>訊息相互關聯
此範例示範訊息佇列 (MSMQ) 應用程式如何將 MSMQ 訊息傳送至 Windows Communication Foundation (WCF) 服務，以及如何訊息可以相互關聯的要求/回應案例中的傳送者與接收者應用程式之間。 這個範例會使用 msmqIntegrationBinding 繫結。 本實例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。 K  
  
 這個服務會處理從傳送者接收的訊息，再將回應訊息傳回給傳送者。 傳送者會將收到的回應與它原先傳送的要求相互關聯。 訊息的 `MessageID` 和 `CorrelationID` 屬性是用來使要求與回應訊息產生相互關聯。  
  
 `IOrderProcessor` 服務合約會定義適合與佇列一起使用的單向服務作業。 MSMQ 訊息沒有 Action 標頭，所以不可能自動將不同 MSMQ 訊息對應到作業合約。 因此，這種情況下只能有一個作業合約。 如果您想要在服務中定義更多的作業合約，應用程式就必須提供資訊，說明 MSMQ 訊息中的哪個標頭 (例如，標籤或 correlationID) 可以用來決定分派哪個作業合約。 
  
 MSMQ 訊息也不會包含有關作業合約的不同參數各自對應到哪個標頭的資訊。 因此，在作業合約中只能有一個參數。 參數的類型是<xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>，其中包含基礎 MSMQ 訊息。 `MsmqMessage<T>` 類別中的型別 "T" 代表已序列化為 MSMQ 訊息本文的資料。 在這個範例中，`PurchaseOrder` 型別會序列化為 MSMQ 訊息本文。  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 服務作業會處理採購單，並在服務主控台視窗中顯示採購單內容及其狀態。 <xref:System.ServiceModel.OperationBehaviorAttribute> 將作業設定為先向佇列登記交易，然後在作業回傳時標記交易完成。 `PurchaseOrder` 包含必須由服務進行處理的採購單明細。

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

 服務會使用自訂用戶端 `OrderResponseClient`，將 MSMQ 訊息傳送至佇列。 接收和處理訊息的應用程式是 MSMQ 應用程式並是 WCF 應用程式，因為沒有隱含的服務合約之間兩個應用程式。 因此，我們無法在這個案例中使用 Svcutil.exe 工具來建立 Proxy。

 自訂 proxy 基本上是相同的所有 WCF 應用程式使用`msmqIntegrationBinding`繫結傳送訊息。 與其他 Proxy 不同的是，它並不包含服務作業的範圍， 而只是一項送出訊息的作業。

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

 服務會自我裝載。 使用 MSMQ 整合傳輸時，必須事先建立使用的佇列。 這個動作可手動或透過程式碼完成。 在這個範例中，服務包含檢查佇列是否存在並在需要時建立佇列的 <xref:System.Messaging> 程式碼。 佇列名稱會從組態檔中讀取。

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

 傳送訂單要求的 MSMQ 佇列可以在組態檔的 appSettings 區段中指定。 用戶端和服務端點則是在組態檔的 system.serviceModel 區段中定義。 這兩個都會指定 `msmqIntegrationbinding` 繫結。

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

 用戶端應用程式會使用 <xref:System.Messaging>，傳送永久性的交易式訊息至佇列。 訊息的本文會包含採購單。

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

 接收訂單回應的 MSMQ 佇列是在組態檔的 appSettings 區段中指定，如下列範例組態所示。

> [!NOTE]
>  佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。 WCF 端點位址會指定 msmq.formatname 配置，並使用"localhost"代表本機電腦。 根據 MSMQ 方針，正確的格式名稱應遵照 URI 中的 msmq.formatname。

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 用戶端應用程式會儲存其傳送至服務之訂單要求訊息的 `messageID`，並等候服務的回應。 一旦回應抵達佇列，用戶端就會使用訊息的 `correlationID` 屬性 (其中包含用戶端原先傳送至服務之訂單訊息的 `messageID`)，將此回應與它所傳送的訂單訊息相互關聯。

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

 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以看到服務從用戶端接收訊息，再將回應傳送給用戶端。 用戶端會顯示從服務收到的回應。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。

> [!NOTE]
>  這個範例需要安裝訊息佇列 (MSMQ)。 請參閱「請參閱」一節中的 MSMQ 安裝指示。

### <a name="to-setup-build-and-run-the-sample"></a>若要設定、建置及執行範例

1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2.  如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。

    1.  開啟 Visual Studio 2012 中的 伺服器管理員。

    2.  依序展開**功能** 索引標籤。

    3.  以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。

    4.  請檢查**Transactional**  方塊中。

    5.  輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。

3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

4.  若要在單一電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。

### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例

1.  將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。

2.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。

3.  在 Client.exe.config 檔案中，變更 orderQueueName 以取代 "." 指定服務電腦名稱。

4.  在 Service.exe.config 檔案中，變更用戶端端點位址以取代 "." 指定用戶端電腦名稱。

5.  在服務電腦上，從命令提示字元啟動 Service.exe。

6.  在用戶端電腦上，從命令提示字元啟動 Client.exe。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>另請參閱
- [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [訊息佇列](https://go.microsoft.com/fwlink/?LinkId=94968)
