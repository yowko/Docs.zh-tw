---
title: MSMQ 4.0 中的有害訊息處理
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 88ce22c9376313db26a5cbe377bdc8aaee83c118
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965563"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0 中的有害訊息處理
這個範例會示範如何在服務中執行有害訊息處理。 這個範例是以交易式[MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)系結範例為基礎。 這個範例會使用 `netMsmqBinding`。 這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。

 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。

 有害訊息是指會從佇列反覆讀取的訊息，此時讀取該訊息的服務無法處理訊息，因而終止訊息讀取時所位於的異動。 此時，服務會重試訊息。 如果訊息有問題，理論上這種情形會不斷發生。 請注意，只有當您使用交易來讀取佇列並叫用服務作業時，才會發生這個情況。

 根據 MSMQ 的版本，NetMsmqBinding 支援有害訊息的有限到完整偵測。 訊息已偵測為有害之後，有多種方法可以處理此訊息。 同樣地，根據 MSMQ 的版本，NetMsmqBinding 會支援完整處理有害訊息的有限處理功能。

 這個範例會示範 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 平台上提供的有限有害訊息處理功能，以及 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上提供的完整有害訊息處理功能。 這兩個範例的目標都是要將有害訊息從佇列移出至其他佇列，以便有害訊息服務可以接著處理這些有害訊息。

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 有害訊息處理範例
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，MSMQ 會提供能夠用來儲存有害訊息的有害訊息子佇列功能。 這個範例會示範使用 [!INCLUDE[wv](../../../../includes/wv-md.md)] 處理有害訊息的最佳作法。

 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，有害訊息偵測功能已經相當成熟。 有三個屬性能夠協助偵測。 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 是從佇列重新讀取指定訊息、並接著分派至應用程式以便進行處理的次數。 因為訊息無法分派至應用程式，或應用程式在服務作業中回復交易而使訊息放回佇列時，該訊息就會從佇列重新讀取。 <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> 是將訊息移至重試佇列的次數。 當達到 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 時，訊息就會移至重試佇列。 <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> 屬性是指時間延遲，在經過此段時間之後，訊息就會從重試佇列移回主要佇列。 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 會重設為 0。 這時訊息會再試一次。 如果讀取訊息的所有嘗試都失敗，該訊息就會被標記為有害。

 一旦訊息標記為有害，該訊息就會根據 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 列舉中的設定加以處理。 若要重新逐一查看可能的值：

- 錯誤 (預設值):表示錯誤接聽程式和服務主機。

- 下拉式以捨棄訊息。

- 進入將訊息移至有害訊息子佇列。 這個值只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。

- 否決若要拒絕訊息, 請將訊息傳回給寄件者的寄不出的信件佇列。 這個值只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。

 此範例會示範對有害訊息使用 `Move` 處置。 `Move` 會導致訊息移至有害子佇列。

 服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 服務作業會顯示訊息，指出正在處理訂單。 為了示範有害訊息功能，`SubmitPurchaseOrder` 服務作業會擲回例外狀況，以復原在隨機叫用服務時的異動。 這樣會導致訊息必須放回佇列中。 最後，訊息會標示為有害。 組態會設定成將有害訊息移至有害訊息子佇列。

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

 服務組態包括下列有害訊息屬性：`receiveRetryCount`、`maxRetryCycles`、`retryCycleDelay` 和 `receiveErrorHandling`，如下列組態檔所示。

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

## <a name="processing-messages-from-the-poison-message-queue"></a>處理有害訊息佇列中的訊息
 有害訊息服務會讀取最終有害訊息佇列中的訊息，並處理這些訊息。

 有害訊息佇列中的訊息是指定址到正在處理這些訊息之服務的訊息，這個服務與有害訊息服務端點可能不同。 因此, 當有害訊息服務從佇列讀取訊息時, WCF 通道層會尋找端點不相符的情況, 而且不會分派訊息。 此時，該訊息是定址到訂單處理服務，但卻是由有害訊息服務接收。 即使訊息是定址到其他端點，若要繼續接收訊息，我們就必須新增 `ServiceBehavior`，以便篩選比對準則要比對訊息定址到的任何服務端點時的所在位址。 若要成功處理從有害訊息佇列中讀取的訊息，您就必須執行這項操作。

 有害訊息服務實作本身與服務實作非常相似， 它會實作合約並處理訂單。 程式碼範例如下所示。

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

 與從訂單佇列中讀取訊息的訂單處理服務不同，有害訊息服務會從有害子佇列中讀取訊息。 有害佇列是主要佇列的子佇列，名為 "poison" 且由 MSMQ 自動產生。 若要存取有害佇列，請提供後面加上 ";" 的主要佇列名稱和子佇列名稱 (在此範例中為 -"poison")，如下列範例組態所示。

> [!NOTE]
> 在 MSMQ v3.0 的範例中，有害佇列名稱不是子佇列，而是我們將訊息移至其中的佇列。

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

 當您執行範例時，用戶端、服務和有害訊息服務活動都會顯示在主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務。

 服務會開始執行、處理訂單，並隨機終止處理。 如果訊息指出其已處理訂單，您就可以再次執行用戶端來傳送其他訊息，直到您清楚該服務已確實終止訊息。 根據設定的有害訊息設定，訊息會在移至最終有害佇列之前嘗試經過處理一次。

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

 啟動有害訊息服務，即可從有害佇列讀取有害訊息。 在這個範例中，有害訊息服務會讀取並處理訊息。 您會發現已終止和已標記為有害的採購單會由有害訊息服務所讀取。

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

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。

    1. 在 Visual Studio 2012 中開啟伺服器管理員。

    2. 展開 [**功能**] 索引標籤。

    3. 以滑鼠右鍵按一下 [**私人訊息佇列**], 然後選取 [**新增**]、[**私用佇列**]。

    4. 選取 [**交易**式] 方塊。

    5. 輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。

3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

4. 若要在單一或跨電腦設定中執行範例, 請變更佇列名稱以反映實際主機名稱, 而不是 localhost, 並遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。

 根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。 `MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。 根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。 若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。 如果您在不屬於網域的電腦上執行此範例, 則會收到下列錯誤:「使用者的內部訊息佇列憑證不存在」。

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>若要在加入至工作群組的電腦上執行範例

1. 如果您的電腦不是網域的一部分，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態所示：

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     請透過設定端點的 bindingConfiguration 屬性，確定端點與繫結相關聯。

2. 請務必先變更 PoisonMessageServer、伺服器和用戶端上的組態，再執行範例。

    > [!NOTE]
    >  將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。  
  
3. 若要讓中繼資料交換正常運作，我們要向 http 繫結登錄 URL。 這時需要在更高權限的命令視窗中執行服務。 否則, 您會收到如下的例外狀況`Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`:。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
