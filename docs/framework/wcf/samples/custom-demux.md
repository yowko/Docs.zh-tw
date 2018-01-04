---
title: "自訂 Demux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 540469571f06f9c2ab38f9754a40aae5a3c3b267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-demux"></a>自訂 Demux
這個範例會示範 MSMQ 訊息標頭如何對應至不同的服務作業以便[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]服務使用<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>不限於使用一項服務作業中所示[訊息佇列Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)和[Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)範例。  
  
 這個範例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。  
  
 服務合約為 `IOrderProcessor`，這會定義適合與佇列搭配使用的單向服務。  
  
```  
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```  
  
 MSMQ 訊息沒有 Action 標頭。 無法將不同的 MSMQ 訊息自動對應至作業合約。 因此，這時只能有一個作業合約。 為了克服這項限制，服務會實作 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> 介面的 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 方法。 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> 方法能夠讓服務將指定的訊息標頭對應至特定服務作業。 在這個範例中，訊息的標籤標頭會對應至服務作業。 作業合約的 `Name` 參數會判定必須將指定訊息標籤分派到其中的服務作業。 例如，如果訊息的標籤標頭包含 "SubmitPurchaseOrder"，就會叫用 "SubmitPurchaseOrder" 服務作業。  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 服務必須實作 <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> 介面的 <xref:System.ServiceModel.Description.IContractBehavior> 方法，如下列範例程式碼所示。 這會將自訂 `OperationSelector` 套用至服務架構分派執行階段。  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 在執行至 OperationSelector 之前，訊息必須通過發送器的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>。 根據預設，如果在服務實作之任何合約上都找不到訊息的動作，該訊息就會遭到拒絕。 為了避免這項檢查，我們會實作名為 <xref:System.ServiceModel.Description.IEndpointBehavior> 的 `MatchAllFilterBehavior`，此行為會藉由套用 `ContractFilter` 讓任何訊息通過 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，如下列所示。  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 當服務接收到訊息時，便會使用該標籤標頭提供的資訊分派適當的服務作業。 訊息本文會還原序列化為 `PurchaseOrder` 物件，如下列範例程式碼所示。  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 服務會自我裝載。 使用 MSMQ 時，必須事先建立使用的佇列。 這個動作可手動或透過程式碼完成。 在這個範例中，該服務包含的程式碼會檢查佇列的存在，並在佇列不存在時建立佇列。 佇列名稱會從組態檔中讀取。  
  
```  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
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
  
 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。  
  
> [!NOTE]
>  佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點位址會指定 msmq.formatname 配置，並使用 localhost 表示本機電腦。 在配置後面的是根據 MSMQ 格式名稱定址方針而正確格式化的佇列位址。  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  這個範例需要安裝[訊息佇列](http://go.microsoft.com/fwlink/?LinkId=95143)。  
  
 啟動服務，並執行用戶端。  
  
 下列輸出會顯示在用戶端上。  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 下列輸出一定會出現在服務上。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
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
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務電腦中。  
  
2.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。  
  
3.  在 Client.exe.config 檔案中，變更 orderQueueName 以取代 "." 指定服務電腦名稱。  
  
4.  在服務電腦上，從命令提示字元啟動 Service.exe。  
  
5.  在用戶端電腦上，從命令提示字元啟動 Client.exe。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>請參閱  
 [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [訊息佇列](http://go.microsoft.com/fwlink/?LinkId=95143)
