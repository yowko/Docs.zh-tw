---
title: 工作階段和佇列
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: ee360f7a95529142437764a74c9f6261221af8b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sessions-and-queues"></a>工作階段和佇列
這個範例示範如何透過訊息佇列 (MSMQ) 傳輸，傳送和接收佇列通訊中的一組相關訊息。 這個範例會使用 `netMsmqBinding` 繫結。 這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 有時，用戶端會傳送一組在群組中彼此有關聯的訊息。 當訊息必須一併處理或依照指定的順序處理時，可以使用佇列將它們集合成為群組，以便單一接收應用程式進行處理。 如果伺服器群組上有數個接收應用程式，而且必須確保同一群組的訊息是由相同接收應用程式所處理時，這種做法尤其重要。 佇列工作階段提供的機制是用來傳送和接收一組必須全部一次處理完成的相關訊息。 但是佇列工作階段中必須有異動，您才會看到這種模式。  
  
 在範例中，用戶端會傳送一些訊息給服務做為單一異動範圍內工作階段的一部分。  
  
 服務合約為 `IOrderTaker`，這會定義適合與佇列搭配使用的單向服務。 在下列範例程式碼中示範用於合約的 <xref:System.ServiceModel.SessionMode> 將會顯示該訊息是工作階段的一部分。  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 服務會定義服務作業，但定義的方式只是讓第一項作業登記在異動中，而不自動完成異動。 後續的作業也會登記在相同的異動中，但是不自動完成。 只有工作階段中的最後一項作業，才會自動完成交易。 因此，服務合約中的數個作業引動過程都會使用同一個異動。 如果有任何作業擲回例外狀況，交易就會復原，並將工作階段重新放回佇列中。 要等到最後一項作業完成，交易才會獲得認可。 服務會使用 `PerSession` 做為 <xref:System.ServiceModel.InstanceContextMode>，以便在同一個服務執行個體上接收工作階段中的所有訊息。  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 服務會自我裝載。 使用 MSMQ 傳輸時，必須事先建立使用的佇列。 這個動作可手動或透過程式碼完成。 在這個範例中，服務包含檢查佇列是否存在並在需要時建立佇列的 <xref:System.Messaging> 程式碼。 您可以使用 <xref:System.Configuration.ConfigurationManager.AppSettings%2A> 類別，從組態檔中讀取佇列名稱。  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。 服務的端點是定義在組態檔的 system.serviceModel 區段中，並且會指定 `netMsmqBinding` 繫結。  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 用戶端會建立一個異動範圍。 工作階段中的所有訊息都會傳送到該交易範圍內的佇列，形成不可部分完成的原子單位 (Atomic Unit)，其中的訊息若不是全部成功，就是全部失敗。 藉由呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 來認可交易。  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
>  您對工作階段中的所有訊息只能使用單一異動，而且必須在認可異動之前傳送工作階段中的所有訊息。 關閉用戶端就會關閉工作階段。 因此，必須在交易完成之前先關閉用戶端，才能將工作階段中的所有訊息傳送至佇列。  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。 請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。 您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。  
  
 在用戶端上：  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 在服務上：  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C#、 c + + 或 Visual BASIC.NET 版本，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
 根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。 有兩個 MSMQ 傳輸安全性相關屬性的那就是，<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>和<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`驗證模式設定為依預設，`Windows`和保護層級設為`Sign`。 若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。 如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例  
  
1.  如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列範例組態所示。  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  請務必先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將安全性模式設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。  
  
## <a name="see-also"></a>另請參閱
