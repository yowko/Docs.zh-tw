---
title: "交易 MSMQ 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd656bed608811a5a04a47849bf915f708a62a9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-msmq-binding"></a>交易 MSMQ 繫結
這個範例會示範如何使用訊息佇列 (MSMQ) 執行交易佇列通訊。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。 更精確地說，用戶端會傳送訊息至佇列。 服務會接收來自佇列的訊息。 因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 當交易是用於傳送與接收訊息時，實際上會出現兩個不同的交易。 當用戶端在交易範圍內傳送訊息時，對用戶端與用戶端佇列管理員來說，交易屬於本機範圍。 當服務在交易範圍內接收訊息時，對服務與接收佇列管理員來說，交易屬於本機範圍。 您一定要記住，用戶端與服務並未參與相同的交易，而是在配合佇列執行其作業時 (例如傳送與接收) 使用不同的交易。  
  
 在這個範例中，用戶端會從交易範圍內將訊息批次傳送至服務。 接著，服務會在所定義的交易範圍內接收傳送至佇列的訊息。  
  
 服務合約是 `IOrderProcessor`，如下列範例程式碼所示。 介面會定義適合與佇列搭配使用的單向服務。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 服務行為會定義 `TransactionScopeRequired` 已設為 `true` 的作業行為， 這樣會確定此方法存取的任何資源管理員都使用從佇列擷取訊息時所使用的相同交易範圍。 這種行為也會確保當方法擲回例外狀況時，訊息會傳回至佇列。 如果未設定這個作業行為，已佇列通道所建立的交易就會從佇列讀取訊息、並且在分派前就自動進行認可，因此，如果此作業失敗，訊息就會遺失。 最常見的案例，就是登記於用來從佇列讀取訊息之交易的服務作業，如下列程式碼所示範。  
  
```  
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```  
  
 服務會自我裝載。 使用 MSMQ 傳輸時，必須事先建立使用的佇列。 這個動作可手動或透過程式碼完成。 在這個範例中，該服務包含的程式碼會檢查佇列的存在，並在佇列不存在時建立佇列。 佇列名稱會從組態檔中讀取。 基底地址由[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)以產生 proxy 服務。  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
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
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中，如下面的範例組態所示。  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  使用 <xref:System.Messaging> 來建立佇列時，佇列會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 端點會使用包含 net.msmq 配置的佇列位址、使用 "localhost" 代表本機電腦，並在其路徑中使用正斜線。  
  
 用戶端會建立一個交易範圍。 與佇列的通訊會發生在交易範圍內，導致其被視為原子單位 (Atomic Unit)，其中會將所有訊息都傳送至佇列，或是不傳送任何訊息至佇列。 呼叫交易範圍上的 <xref:System.Transactions.TransactionScope.Complete%2A>，即可認可交易。  
  
```  
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 若要檢查交易是否正常運作，請將交易範例標記為註解來修改用戶端 (如下列範例程式碼所示方式)，並重建方案，然後執行用戶端。  
  
```  
//scope.Complete();  
```  
  
 因為交易尚未完成，所以這些訊息不會傳送至佇列。  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。 您可以查看來自用戶端的服務接收訊息。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。 請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。 您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果服務優先執行，它就會檢查以確定佇列存在。 如果佇列不存在，服務將建立一個佇列。 您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。 請依照下列步驟，在 Windows 2008 中建立佇列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。  
  
    2.  展開**功能** 索引標籤。  
  
    3.  以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。  
  
    4.  請檢查**交易式**方塊。  
  
    5.  輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
 根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。 MSMQ 傳輸安全性有兩個相關屬性：<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> 和 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>。 根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。 若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。 如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例  
  
1.  如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列的範例組態程式碼所示。  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  請務必先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security``mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>另請參閱
