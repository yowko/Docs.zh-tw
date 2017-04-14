---
title: "變動性佇列通訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# 變動性佇列通訊
這個範例會示範如何透過訊息佇列 \(MSMQ\) 傳輸來執行變動性佇列通訊。這個範例會使用 <xref:System.ServiceModel.NetMsmqBinding>。這個案例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在佇列通訊中，用戶端會使用佇列與服務通訊。更精確地說，用戶端會傳送訊息至佇列。服務會接收來自佇列的訊息。因此，服務與用戶端不需同時執行，就能使用佇列通訊。  
  
 當您傳送不具保證的訊息時，MSMQ 只能盡量將訊息傳遞出去，這與 MSMQ 保證傳遞訊息的「正好一次」保證不同，或者如果無法傳遞，則會讓您知道訊息無法傳遞。  
  
 在特定案例中，當及時傳遞比遺失訊息更重要時，您可能想要透過佇列傳送不具保證的變動性訊息。如果佇列管理員毀損，變動性訊息不會存留。因此，如果佇列管理員毀損，用於儲存變動性訊息的非交易式佇列會存留，但訊息本身無法存留，因為訊息並未儲存在磁碟中。  
  
> [!NOTE]
>  您無法使用 MSMQ 在交易的範圍內傳送不具保證的變動性訊息。此外，您必須建立非交易式佇列，才能傳送變動性訊息。  
  
 此範例中的服務合約為 `IStockTicker`，這個合約會定義最適合與佇列一起使用的單向服務。  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
  
```  
  
 服務作業會顯示股票行情即時看板符號和價格，如下列範例程式碼所示：  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
  
```  
  
 服務會自我裝載。使用 MSMQ 傳輸時，必須事先建立使用的佇列。這個動作可手動或透過程式碼完成。在此範例中，服務包含可用來檢查佇列是否存在，並在需要時建立佇列的程式碼。佇列名稱會從組態檔中讀取。基底位址會由[ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 用來產生服務的 Proxy。  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
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
  
 MSMQ 佇列名稱是在組態檔的 appSettings 區段中指定。服務的端點是定義在組態檔的 system.serviceModel 區段中，並且會指定 `netMsmqBinding` 繫結。  
  
> [!NOTE]
>  當使用 <xref:System.Messaging> 來建立佇列時，佇列名稱使用點 \(.\) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 端點位址會指定 net.msmq: 配置、使用 "localhost" 代表本機電腦，並在其路徑中使用正斜線。  
  
 訊息的保證和持久性或變動性也是在組態中指定。  
  
```  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
          </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
  
```  
  
 由於此範例使用非交易式的佇列來傳送佇列訊息，因此無法將交易訊息傳送至佇列。  
  
```  
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
  
```  
  
 當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。您可以查看來自用戶端的服務接收訊息。在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
 根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。MSMQ 傳輸安全性有兩個相關的屬性，即 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> 和 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` 。根據預設，驗證模式會設定為 `Windows`，而保護層級會設定為 `Sign`。若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。  
  
### 若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例  
  
1.  如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態程式碼所示：  
  
    ```  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
  
    ```  
  
2.  請務必先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## 請參閱