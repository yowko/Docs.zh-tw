---
title: "交易的批次處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc04f0ce1d303a32cbf2232c76bfc4ef1143c9ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-batching"></a>交易的批次處理
這個範例會示範如何使用訊息佇列 (MSMQ) 批次處理交易讀取作業。 「交易的批次處理」是效能最佳化功能，可用於佇列通訊中的交易讀取作業。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 這個範例會示範交易的批次處理。 交易的批次處理是一種行為，可在佇列中讀取許多訊息並進行處理時，使用單一的交易即可。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。  
  
    2.  展開**功能** 索引標籤。  
  
    3.  以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。  
  
    4.  請檢查**交易式**方塊。  
  
    5.  輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。  
  
    > [!NOTE]
    >  在這個範例中，用戶端會在批次中傳送數百則訊息。 服務應用程式通常需要一些時間來處理這些訊息。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例  
  
1.  根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。 有兩個相關的屬性，為 MSMQ 傳輸安全性，<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>和<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`驗證模式設定為依預設，`Windows`和保護層級設為`Sign`。 若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。 如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。  
  
2.  如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列範例組態所示：  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
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
  
    </system.serviceModel>  
    ```  
  
3.  請務必先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security``mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。  
  
4.  若要在遠端電腦上執行資料庫，請變更連接字串以指向資料庫所在的電腦。  
  
## <a name="requirements"></a>需求  
 若要執行此範例，必須已安裝 MSMQ，而且需要 SQL 或 SQL Express。  
  
## <a name="demonstrates"></a>示範  
 範例會示範交易的批次處理行為。 交易的批次處理是與 MSMQ 佇列傳輸一起提供的效能最佳化功能。  
  
 當您使用交易來傳送及接收訊息時，實際上有兩個不同的交易。 當用戶端在交易範圍內傳送訊息時，對用戶端與用戶端佇列管理員來說，交易屬於本機範圍。 當服務在交易範圍內接收訊息時，對服務與接收佇列管理員來說，交易屬於本機範圍。 最重要的是了解用戶端與服務並未參與相同的交易；而是當使用佇列執行其作業 (例如傳送與接收) 時會使用不同的交易。  
  
 在範例中，將針對執行多個服務作業使用單一交易。 這項功能只會當做效能最佳化功能使用，而且不會影響應用程式的語意 (Semantics)。 範例根據[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)。  
  
## <a name="comments"></a>註解  
 在這個範例中，用戶端會從交易範圍內將訊息批次傳送至服務。 若要顯示效能最佳化，可以傳送大量的訊息。在這個例子中，最多可以傳送 2500 則訊息。  
  
 接著，服務會在所定義的交易範圍內接收傳送至佇列的訊息。 沒有使用批次作業時，每次叫用服務作業就會產生 2500 筆交易。 這樣就會影響系統的效能。 由於在 MSMQ 佇列和 `Orders` 資料庫中牽涉到兩個資源管理員，因此這類交易就可說是 DTC 交易。 使用較少量的交易，確定訊息批次作業和服務作業叫用都是在單一交易上進行，即可最佳化效能。  
  
 您可透過下列方式使用批次作業功能：  
  
-   在組態中指定交易的批次處理行為。  
  
-   指定批次大小，這是使用單一交易要讀取的訊息數。  
  
-   指定要同時執行的批次作業數上限。  
  
 在此範例中，藉由降低交易數以確定認可交易之前會在單一交易上叫用 100 個服務作業，就可看到效能增益。  
  
 服務行為會定義 `TransactionScopeRequired` 已設為 `true` 的作業行為， 這樣會確定此方法存取的任何資源管理員都使用從佇列擷取訊息時所使用的相同交易範圍。 在此範例中，會使用基本資料庫來存放訊息中所含的訂單資訊。 交易範圍也會保證在方法擲回例外狀況時，訊息仍會傳回佇列。 如果沒有設定這個作業行為，佇列通道就會建立交易，在分派訊息之前讀取佇列中的訊息並自動認可，因此若作業失敗，訊息就會遺失。 最常見的案例是服務作業登記在用來從佇列讀取訊息的交易中，如同下列程式碼所示範。  
  
 請注意，`ReleaseServiceInstanceOnTransactionComplete` 設定為 `false`。 這是批次作業的重要需求。 `ReleaseServiceInstanceOnTransactionComplete` 上的 `ServiceBehaviorAttribute` 屬性會指出完成交易之後，服務執行個體應該執行的動作。 根據預設，完成交易時會釋放服務執行個體。 批次作業的核心觀念在於使用單一交易，就可讀取及分派佇列中的許多訊息。 因此，釋放服務執行個體就會永久停止完成交易，而不再使用批次作業。 如果這個屬性設定為 `true`，而且交易的批次處理行為已新增至端點，批次作業驗證行為就會擲回例外狀況。  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 `Orders` 類別會封裝訂單處理。 在此範例中，會使用訂單資訊更新資料庫。  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 會在服務應用程式組態中，指定批次作業行為與其組態。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  批次大小對系統而言是一種提示。 例如，如果將批次大小指定為 20，則會使用單一交易讀取及分派 20 則訊息，然後認可交易。 但在一些情況下，可能會在達到批次大小之前，交易就已認可批次。  
>   
>  與每個交易相關聯的項目為逾時，會在建立交易時立即開始計時。 此逾時到期時，就會中止交易。 也可能在達到批次大小之前，此逾時就已到期。 為了避免由於中止而重新執行批次，`TransactedBatchingBehavior` 會查看還剩多少時間可以執行交易。 如果已使用 80% 的交易逾時，就會認可交易。  
>   
>  如果佇列中沒有其他訊息，則不會等待到達批次大小，<xref:System.ServiceModel.Description.TransactedBatchingBehavior> 就會認可交易。  
>   
>  批次的大小是由您的應用程式所決定。 如果批次大小太小，可能不會得到希望的效能。 另一方面，如果批次大小太大，可能使效能下降。 例如，交易可以存留較久的時間並在資料庫上持有鎖定，或者應用程式變成鎖死，因而導致回復批次並重做工作。  
  
 用戶端會建立一個交易範圍。 與佇列的通訊會發生在交易範圍內，導致其被視為原子單位 (Atomic Unit)，其中會將所有訊息都傳送至佇列，或是不傳送任何訊息至佇列。 呼叫交易範圍上的 <xref:System.Transactions.TransactionScope.Complete%2A>，即可認可交易。  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
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
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。 請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。 您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。 以批次讀取訊息及處理訊息時，您會看到可以捲動的輸出。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>另請參閱
