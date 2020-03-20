---
title: MSMQ 4.0 中的有害訊息處理
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144236"
---
# <a name="poison-message-handling-in-msmq-40"></a>MSMQ 4.0 中的有害訊息處理
這個範例會示範如何在服務中執行有害訊息處理。 此示例基於[交易 MSMQ 綁定](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)示例。 這個範例會使用 `netMsmqBinding`。 這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。

 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。

 有害訊息是指會從佇列反覆讀取的訊息，此時讀取該訊息的服務無法處理訊息，因而終止訊息讀取時所位於的異動。 此時，服務會重試訊息。 如果訊息有問題，理論上這種情形會不斷發生。 僅當使用事務從佇列中讀取並調用服務操作時，才能發生這種情況。

 根據 MSMQ 的版本，NetMsmqBinding 支援有害訊息的有限到完整偵測。 訊息已偵測為有害之後，有多種方法可以處理此訊息。 同樣地，根據 MSMQ 的版本，NetMsmqBinding 會支援完整處理有害訊息的有限處理功能。

 此示例說明了 Windows Server 2003 和 Windows XP 平臺上提供的有限毒劑設施，以及 Windows Vista 上提供的完整毒物設施。 在這兩個示例中，目標是將有害訊息從佇列中移至另一個佇列。 然後，該佇列可以通過有害訊息服務提供服務。

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 有害訊息處理範例
 在 Windows Vista 中，MSMQ 提供了一個可用於存儲有害訊息的毒死子佇列工具。 此示例演示了使用 Windows Vista 處理有害訊息的最佳做法。

 Windows Vista 中的有害訊息檢測非常複雜。 有三個屬性能夠協助偵測。 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 是從佇列重新讀取指定訊息、並接著分派至應用程式以便進行處理的次數。 因為訊息無法分派至應用程式，或應用程式在服務作業中回復交易而使訊息放回佇列時，該訊息就會從佇列重新讀取。 <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> 是將訊息移至重試佇列的次數。 當達到 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 時，訊息就會移至重試佇列。 <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> 屬性是指時間延遲，在經過此段時間之後，訊息就會從重試佇列移回主要佇列。 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 會重設為 0。 這時訊息會再試一次。 如果讀取訊息的所有嘗試都失敗，該訊息就會被標記為有害。

 一旦訊息標記為有害，該訊息就會根據 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 列舉中的設定加以處理。 若要重新逐一查看可能的值：

- Fault (預設)：使接聽程式和服務主機發生錯誤。

- Drop：捨棄訊息。

- 移動：將消息移動到有害訊息子佇列。 此值僅在 Windows Vista 上可用。

- Reject：拒絕訊息，並將訊息傳回至傳送者之寄不出的信件佇列。 此值僅在 Windows Vista 上可用。

 此範例會示範對有害訊息使用 `Move` 處置。 `Move`使消息移動到有害子佇列。

 服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 服務作業會顯示訊息，指出正在處理訂單。 為了演示有害訊息功能，`SubmitPurchaseOrder`服務操作會引發一個異常，用於在隨機調用服務時回滾事務。 這樣會導致訊息必須放回佇列中。 最後，訊息會標示為有害。 配置設置為將毒消息移動到毒死子佇列。

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

 有害訊息佇列中的訊息是指定址到正在處理這些訊息之服務的訊息，這個服務與有害訊息服務端點可能不同。 因此，當毒消息服務從佇列中讀取消息時，WCF 通道層會發現終結點不匹配，並且不調度消息。 此時，該訊息是定址到訂單處理服務，但卻是由有害訊息服務接收。 即使訊息是定址到其他端點，若要繼續接收訊息，我們就必須新增 `ServiceBehavior`，以便篩選比對準則要比對訊息定址到的任何服務端點時的所在位址。 若要成功處理從有害訊息佇列中讀取的訊息，您就必須執行這項操作。

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

 與從訂單佇列讀取消息的訂單處理服務不同，毒消息服務從毒死子佇列中讀取消息。 毒佇列是主佇列的子佇列，名為"毒"，由 MSMQ 自動生成。 要訪問它，請提供主佇列名稱，後跟";" 和子佇列名稱（在本例中為 -"毒"，如以下示例配置所示）。

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

```console
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

```console
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

1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。

    1. 2012 年在視覺化工作室中打開伺服器管理員。

    2. 展開 **"功能"** 選項卡。

    3. 按右鍵 **"專用訊息佇列**"，然後選擇 **"新建**"**私用佇列**。

    4. 選中 **"事務"** 框。

    5. 輸入`ServiceModelSamplesTransacted`為新佇列的名稱。

3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

4. 要在單台電腦或跨電腦配置中運行示例，請更改佇列名稱以反映實際主機名稱而不是本地主機，並按照[運行 Windows 通信基礎示例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的說明進行操作。

 根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。 `MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。 根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。 若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。 如果您在不屬於網域的電腦上執行這個範例，就會收到下列錯誤：「使用者的內部訊息佇列憑證不存在」。

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

2. 在運行示例之前，請確保更改"毒郵件伺服器"、伺服器和用戶端上的配置。

    > [!NOTE]
    > 將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。  
  
3. 若要讓中繼資料交換正常運作，我們要向 http 繫結登錄 URL。 這時需要在更高權限的命令視窗中執行服務。 否則，您會收到異常，例如： `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
