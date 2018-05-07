---
title: Windows Communication Foundation 至訊息佇列
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 83c16fc097cc6eca76578730bcad0491b648c5c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation 至訊息佇列
這個範例會示範 Windows Communication Foundation (WCF) 應用程式如何傳送訊息至訊息佇列 (MSMQ) 應用程式。 這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。 服務與用戶端不需要在相同時間執行。  
  
 服務會接收佇列訊息，然後處理訂單。 服務會建立交易式佇列，然後設定已接收訊息的訊息處理常式，如下列範例程式碼所示。  

```csharp
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

 當訊息是由佇列接收時，就會叫用訊息處理常式 `ProcessOrder`。  

```csharp
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

 服務會從 MSMQ 訊息本文擷取 `ProcessOrder`，然後處理訂單。  
  
 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中，如下面的範例組態所示。  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。  
  
 用戶端會建立採購單，然後在異動範圍內提交採購單，如下列範例程式碼所示。  

```csharp
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

 用戶端會依序使用自訂用戶端，將 MSMQ 訊息傳送至佇列。 由於接收和處理訊息的應用程式是 MSMQ 應用程式，而非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式，所以兩個應用程式之間沒有隱含的服務合約。 因此，我們無法在這個案例中使用 Svcutil.exe 工具來建立 Proxy。  
  
 對所有使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結傳送訊息的 `MsmqIntegration` 應用程式來說，自訂用戶端基本上都相同。 與其他用戶端不同的是，它並不包含服務作業的範圍， 而只是一項送出訊息的作業。  

```csharp
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

 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。 請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。 例如，您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。  
  
> [!NOTE]
>  這個範例需要安裝訊息佇列。 請參閱安裝指示[訊息佇列](http://go.microsoft.com/fwlink/?LinkId=94968)。  
  
### <a name="to-setup-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。  
  
    2.  展開**功能** 索引標籤。  
  
    3.  以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。  
  
    4.  請檢查**交易式**方塊。  
  
    5.  輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。  
  
2.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。  
  
3.  在 Client.exe.config 檔案中，變更用戶端端點位址以取代 "." 指定服務電腦名稱。  
  
4.  在服務電腦上，從命令提示字元啟動 Service.exe。  
  
5.  在用戶端電腦上，從命令提示字元啟動 Client.exe。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>另請參閱  
 [如何：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [訊息佇列](http://go.microsoft.com/fwlink/?LinkId=94968)
