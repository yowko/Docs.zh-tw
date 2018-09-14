---
title: 雙向通訊
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519824"
---
# <a name="two-way-communication"></a>雙向通訊
這個範例會示範如何透過 MSMQ 來執行交易雙向佇列通訊。 這個範例會使用 `netMsmqBinding` 繫結。 在此範例中，服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此樣本根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 用戶端會將訊息傳送至佇列，而服務會從佇列接收訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 這個範例會示範使用佇列的雙向通訊。 用戶端會將採購單從交易範圍內傳送至佇列。 服務會接收訂單，處理訂單，然後從在交易範圍內的佇列，根據訂單狀態回呼 (Call Back) 用戶端。 為了促進雙向通訊，用戶端與服務都會使用佇列將採購單和訂單狀態加入佇列。  
  
 服務合約 `IOrderProcessor` 會定義適合與佇列一起使用的單向服務作業。 服務作業包含可用來傳送訂單狀態的回覆端點。 回覆端點是將訂單狀態傳回用戶端的佇列 URI。 訂單處理應用程式會實作這個合約。  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 用來傳送訂單狀態的回覆合約是由用戶端指定。 用戶端會實作訂單狀態合約。 服務會使用這個合約產生的 Proxy 將訂單狀態傳回用戶端。  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 服務作業會處理已送出的採購單。 <xref:System.ServiceModel.OperationBehaviorAttribute> 會套用至服務作業，以便指定自動登記在用來從佇列接收訊息的交易中，以及指定在服務作業完成時自動完成交易。 `Orders` 類別會封裝訂單處理功能。 在本例中，這個類別會將採購單新增至字典。 `Orders` 類別中的作業可以使用服務作業所登記的交易。  
  
 除了處理已送出的採購單，服務作業也會將訂單狀態回覆至用戶端。  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。 服務端點會定義在組態檔的 System.ServiceModel 區段中。  
  
> [!NOTE]
>  MSMQ 佇列名稱與端點位址會使用稍微不同的定址慣例。 MSMQ 佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。 Windows Communication Foundation (WCF) 端點位址會指定 net.msmq： 配置中，使用"localhost"代表本機電腦，並在其路徑中使用正斜線。 若要讀取裝載於遠端電腦的佇列，請將 "." 和 "localhost" 取代成遠端電腦名稱。  
  
 服務會自我裝載。 使用 MSMQ 傳輸時，必須事先建立使用的佇列。 這個動作可手動或透過程式碼完成。 在這個範例中，服務會檢查佇列是否存在，並在需要時建立佇列。 佇列名稱會從組態檔中讀取。 使用基底位址[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生服務 proxy。  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 用戶端會建立異動。 與佇列的通訊會發生在交易範圍內，這點會導致其被視為不可部分完成的原子單位 (Atomic Unit)，其中的訊息若不是全部成功，就是全部失敗。  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 用戶端程式碼會實作 `IOrderStatus` 合約以接收服務的訂單狀態。 在此範例中，它會印出訂單狀態。  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,   
                                                           status);  
    }  
}  
```

 訂單狀態佇列會建立在 `Main` 方法中。 用戶端組態會包含訂單狀態服務組態來裝載訂單狀態服務，如下列範例組態所示。  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service   
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
              binding="netMsmqBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
 服務會顯示採購單資訊，並表示它正在將訂單狀態傳送回訂單狀態佇列。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 用戶端會顯示服務所傳送的訂單狀態資訊。  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
    > [!NOTE]
    >  如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以配合用戶端節點。  
  
 根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。 有兩個 MSMQ 傳輸安全性相關屬性<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>並<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`根據預設，驗證模式設定為`Windows`和保護層級設定為`Sign`。 若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。 如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例  
  
1.  如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列範例組態所示：  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"   
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2.  關閉用戶端組態的安全性會產生下列訊息：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service   
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
                    binding="netMsmqBinding"   
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3.  這個範例的服務會在 `OrderProcessorService` 中建立繫結。 在繫結具現化後新增程式碼行，以便將安全性模式設定為 `None`。  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  請務必先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 或 `Message` 安全性設定為 `None`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a>另請參閱
