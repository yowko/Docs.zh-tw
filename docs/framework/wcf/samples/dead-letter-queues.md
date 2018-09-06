---
title: 寄不出的信件佇列
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 4f30e9486c8798e3610e13e6abe1c2612c70b69f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43801881"
---
# <a name="dead-letter-queues"></a>寄不出的信件佇列
這個範例示範如何處理已傳遞失敗的訊息。 它根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例。 這個範例會使用 `netMsmqBinding` 繫結。 這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!NOTE]
>  這個範例會示範每個應用程式的「寄不出的信件」佇列，而此佇列只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中使用。 您可以修改此範例，以便在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上使用 MSMQ 3.0 的預設全系統佇列。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 因為佇列通訊會有一定的期間不活動，您可能需要在訊息上建立與某段存留時間值的關聯，以確保不會在過了這段時間，還將訊息傳遞到應用程式。 另有一些情況，應用程式必須獲知訊息是否傳遞失敗。 如果發生這些情況，像是訊息的存留時間已過，或是訊息傳遞失敗等，都會將訊息放在寄不出的信件佇列中。 進行傳送的應用程式就可以接著從寄不出的信件佇列讀取訊息，然後採取更正動作 (舉凡不做動作到修改傳遞失敗原因等)，再重新傳送訊息。  
  
 在 `NetMsmqBinding` 繫結中，會使用下列屬性來表示寄不出的信件佇列：  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> 屬性，用來表示用戶端所需之寄不出的信件佇列種類。 這個列舉具有下列值：  
  
-   `None`：沒有用戶端需要之寄不出的信件佇列。  
  
-   `System`：系統之寄不出的信件佇列，用來存放無法傳遞的訊息。 電腦上執行的所有應用程式會共用系統之寄不出的信件佇列。  
  
-   `Custom`：使用 <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 屬性所指定的自訂寄不出的信件佇列，用來存放無法傳遞的訊息。 這項功能只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。 當應用程式必須使用自己的寄不出的信件佇列，而不與執行於同一台電腦的其他應用程式共用時，會使用這項功能。  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 屬性，用來表示要當做寄不出的信件佇列使用的特定佇列。 這只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。  
  
 在這個範例中，用戶端會從交易範圍內傳送一批訊息至服務，並隨意為這些訊息指定很低的「存留時間」值 (約 2 秒)。 用戶端還會指定要使用的自訂寄不出的信件佇列，以便將過期的訊息加入。  
  
 用戶端應用程式可以讀取寄不出的信件佇列中的訊息，然後重新嘗試傳送訊息，或是修正導致原始訊息置入寄不出的信件佇列的錯誤，再傳送該訊息。 在範例中，用戶端會顯示錯誤訊息。  
  
 服務合約是 `IOrderProcessor`，如下列範例程式碼所示。  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 服務程式碼範例中的是屬於[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)。  
  
 與服務進行的通訊會在異動範圍內發生。 服務會讀取佇列中的訊息、執行作業，然後顯示作業的結果。 應用程式也會為寄不出的信件訊息建立寄不出的信件佇列。  

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration  
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];  
  
        // Create the transacted MSMQ queue for storing dead message if necessary.  
        if (!MessageQueue.Exists(deadLetterQueueName))  
            MessageQueue.Create(deadLetterQueueName, true);  
  
        // Create a proxy with given client endpoint configuration  
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
        // Create the purchase order  
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
  
        //Create a transaction scope.  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Make a queued call to submit the purchase order  
            client.SubmitPurchaseOrder(po);  
            // Complete the transaction.  
            scope.Complete();  
        }  
  
        client.Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 用戶端的組態會指定很短的期間讓訊息送達服務。 如果無法在指定期間內傳輸訊息，訊息就會過期，然後移入寄不出的信件佇列。  
  
> [!NOTE]
>  用戶端可能會在指定的時間內將訊息傳遞到服務佇列。 為確保您看得到寄不出的信件服務的實際執行過程，您必須先執行用戶端，再啟動服務。 此訊息會逾時，然後傳遞到寄不出的信件服務。  
  
 應用程式必須定義要當做寄不出的信件佇列使用的佇列。 如果未指定佇列，就會使用預設全系統交易式寄不出的信件佇列，將無法傳遞的訊息加入佇列。 在這個範例中，用戶端應用程式會指定它自己的應用程式寄不出的信件佇列。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->  
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>  
  </appSettings>  
  
  <system.serviceModel>  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                binding="netMsmqBinding"   
                bindingConfiguration="PerAppDLQBinding"   
                contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PerAppDLQBinding"  
                 deadLetterQueue="Custom"  
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"   
                 timeToLive="00:00:02"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 寄不出的信件訊息服務會從寄不出的信件佇列讀取訊息。 寄不出的信件訊息服務會實作 `IOrderProcessor` 合約。 然而，這個實作不是要用來處理訂單。 寄不出的信件訊息服務是用戶端服務，並沒有處理訂單的能力。  
  
> [!NOTE]
>  寄不出的信件佇列是用戶端佇列，而且是用戶端佇列管理員本機上的佇列。  
  
 寄不出的信件訊息服務實作會檢查訊息傳遞失敗的原因，然後採取更正措施。 訊息失敗的原因可以擷取自兩個列舉：<xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> 和 <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>。 您可以從 <xref:System.ServiceModel.Channels.MsmqMessageProperty> 擷取 <xref:System.ServiceModel.OperationContext>，如下列範例程式碼所示：  

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
    MsmqMessageProperty mqProp =   
                  OperationContext.Current.IncomingMessageProperties[  
                  MsmqMessageProperty.Name] as MsmqMessageProperty;  
    Console.WriteLine("Message Delivery Status: {0} ",   
                                                mqProp.DeliveryStatus);  
    Console.WriteLine("Message Delivery Failure: {0}",   
                                               mqProp.DeliveryFailure);  
    Console.WriteLine();  
    …  
}
```

 寄不出的信件佇列中的訊息是針對處理訊息之服務所發出的訊息。 因此，當無法投遞的信件訊息服務會從佇列讀取訊息，Windows Communication Foundation (WCF) 通道層端點中尋找不符合，從而不分派訊息。 在本例中，訊息是針對訂單處理服務發出的，但是會由寄不出的信件訊息服務接收。 為了接收針對不同端點發出的訊息，在 `ServiceBehavior` 中會指定用來比對所有位址的位址篩選條件。 若要順利處理從寄不出的信件佇列中讀取的訊息，就必須這麼做。  
  
 在這個範例中，如果失敗的原因是訊息逾時，寄不出的信件訊息服務將會重新傳送訊息。對於其他所有原因，則顯示傳遞失敗，如下列範例程式碼所示：  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]  
public class PurchaseOrderDLQService : IOrderProcessor  
{  
    OrderProcessorClient orderProcessorService;  
    public PurchaseOrderDLQService()  
    {  
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Submitting purchase order did not succeed ", po);  
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;  
  
        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);  
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);  
        Console.WriteLine();  
  
        // resend the message if timed out  
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||  
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)  
        {  
            // re-send  
            Console.WriteLine("Purchase order Time To Live expired");  
            Console.WriteLine("Trying to resend the message");  
  
            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue  
            orderProcessorService.SubmitPurchaseOrder(po);  
            Console.WriteLine("Purchase order resent");  
        }  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the PurchaseOrderDLQService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))  
        {  
            // Open the ServiceHostBase to create listeners and start listening for messages.  
            serviceHost.Open();  
  
            // The service can now be accessed.  
            Console.WriteLine("The dead letter service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.WriteLine();  
            Console.ReadLine();  
        }  
    }  
}   
```

 下列範例示範寄不出的信件訊息的組態：  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">  
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="DefaultBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                 binding="netMsmqBinding"   
                 bindingConfiguration="SystemDLQBinding"   
                 contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="DefaultBinding" />  
        <binding name="SystemDLQBinding"  
                 deadLetterQueue="System"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
 在執行的範例中，有 3 個可執行檔要執行，藉以觀察每個應用程式 (用戶端、服務和寄不出的信件服務) 運用寄不出的信件佇列的方式；每個應用程式都會從各自寄不出的信件佇列讀取訊息，然後重新傳送給服務。 這些都是會在主控台視窗中產生輸出的主控台應用程式。  
  
> [!NOTE]
>  因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。 您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。 您應該啟動服務再加以關閉，這樣就可以建立佇列。  
  
 執行用戶端時，用戶端會顯示訊息：  
  
```  
Press <ENTER> to terminate client.  
```  
  
 用戶端已嘗試傳送訊息，但是因為逾時期限很短，訊息已過期，且已加入至每個應用程式之寄不出的信件佇列中。  
  
 此時，請執行寄不出的信件服務，它會讀取訊息並顯示錯誤碼，然後將訊息重新傳回到服務。  
  
```  
The dead letter service is ready.  
Press <ENTER> to terminate service.  
  
Submitting purchase order did not succeed  
Message Delivery Status: InDoubt  
Message Delivery Failure: ReachQueueTimeout  
  
Purchase order Time To Live expired  
Trying to resend the message  
Purchase order resent  
```  
  
 服務會啟動，然後讀取重送的訊息，再加以處理。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。  
  
    2.  依序展開**功能** 索引標籤。  
  
    3.  以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。  
  
    4.  請檢查**Transactional**  方塊中。  
  
    5.  輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要執行本範例中單一或跨電腦組態變更佇列名稱，並以完整的電腦名稱取代 localhost，並依照[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>若要在加入至工作群組的電腦上執行範例  
  
1.  如果您的電腦不是網域的一部分，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態所示：  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     請透過設定端點的 `bindingConfiguration` 屬性，確定端點與繫結相關聯。  
  
2.  請務必先變更 DeadLetterService、伺服器和用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。  
  
## <a name="comments"></a>註解  
 根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。 `MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。 根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。 若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。 如果您在不屬於網域的電腦上執行這個範例，就會收到下列錯誤：「使用者的內部訊息佇列憑證不存在」。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a>另請參閱
