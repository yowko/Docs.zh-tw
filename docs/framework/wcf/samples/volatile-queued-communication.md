---
title: 變動性佇列通訊
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: c6b72503cb90108e3ecc9a384cb8d7ad326a7c9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548296"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="06fad-102">變動性佇列通訊</span><span class="sxs-lookup"><span data-stu-id="06fad-102">Volatile Queued Communication</span></span>
<span data-ttu-id="06fad-103">這個範例會示範如何透過訊息佇列 (MSMQ) 傳輸來執行變動性佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="06fad-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="06fad-104">這個範例會使用 <xref:System.ServiceModel.NetMsmqBinding>。</span><span class="sxs-lookup"><span data-stu-id="06fad-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="06fad-105">這個案例中的服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="06fad-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06fad-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="06fad-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="06fad-107">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="06fad-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="06fad-108">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="06fad-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="06fad-109">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-109">The service receives messages from the queue.</span></span> <span data-ttu-id="06fad-110">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="06fad-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="06fad-111">當您傳送不具保證的訊息時，MSMQ 只能盡量將訊息傳遞出去，這與 MSMQ 保證傳遞訊息的「正好一次」保證不同，或者如果無法傳遞，則會讓您知道訊息無法傳遞。</span><span class="sxs-lookup"><span data-stu-id="06fad-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>  
  
 <span data-ttu-id="06fad-112">在特定案例中，當及時傳遞比遺失訊息更重要時，您可能想要透過佇列傳送不具保證的變動性訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="06fad-113">如果佇列管理員毀損，變動性訊息不會存留。</span><span class="sxs-lookup"><span data-stu-id="06fad-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="06fad-114">因此，如果佇列管理員毀損，用於儲存變動性訊息的非交易式佇列會存留，但訊息本身無法存留，因為訊息並未儲存在磁碟中。</span><span class="sxs-lookup"><span data-stu-id="06fad-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06fad-115">您無法使用 MSMQ 在交易的範圍內傳送不具保證的變動性訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="06fad-116">此外，您必須建立非異動式佇列，才能傳送變動性訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-116">You also must create a non-transactional queue to send volatile messages.</span></span>  
  
 <span data-ttu-id="06fad-117">此範例中的服務合約為 `IStockTicker`，這個合約會定義最適合與佇列一起使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="06fad-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```

 <span data-ttu-id="06fad-118">服務作業會顯示股票行情即時看板符號和價格，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="06fad-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>  
  
```csharp
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 <span data-ttu-id="06fad-119">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="06fad-119">The service is self hosted.</span></span> <span data-ttu-id="06fad-120">使用 MSMQ 傳輸時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="06fad-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="06fad-121">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="06fad-121">This can be done manually or through code.</span></span> <span data-ttu-id="06fad-122">在此範例中，服務包含可用來檢查佇列是否存在，並在需要時建立佇列的程式碼。</span><span class="sxs-lookup"><span data-stu-id="06fad-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="06fad-123">佇列名稱會從組態檔中讀取。</span><span class="sxs-lookup"><span data-stu-id="06fad-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="06fad-124">使用基底位址[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生服務 proxy。</span><span class="sxs-lookup"><span data-stu-id="06fad-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>  

```csharp
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

 <span data-ttu-id="06fad-125">MSMQ 佇列名稱是在組態檔的 appSettings 區段中指定。</span><span class="sxs-lookup"><span data-stu-id="06fad-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="06fad-126">服務的端點是定義在組態檔的 system.serviceModel 區段中，並且會指定 `netMsmqBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="06fad-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06fad-127">當使用 <xref:System.Messaging> 來建立佇列時，佇列名稱使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="06fad-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="06fad-128">Windows Communication Foundation (WCF) 端點位址會指定 net.msmq： 配置、 使用"localhost"代表本機電腦，並在其路徑中的正斜線。</span><span class="sxs-lookup"><span data-stu-id="06fad-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>  
  
 <span data-ttu-id="06fad-129">訊息的保證和持久性或變動性也是在組態中指定。</span><span class="sxs-lookup"><span data-stu-id="06fad-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>  
  
```xml  
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
  
 <span data-ttu-id="06fad-130">由於此範例使用非異動式的佇列來傳送佇列訊息，因此無法將異動訊息傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="06fad-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>  

```csharp
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

 <span data-ttu-id="06fad-131">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="06fad-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="06fad-132">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="06fad-133">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="06fad-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="06fad-134">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="06fad-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="06fad-135">您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="06fad-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06fad-136">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="06fad-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06fad-137">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="06fad-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06fad-138">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="06fad-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="06fad-139">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="06fad-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="06fad-140">根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。</span><span class="sxs-lookup"><span data-stu-id="06fad-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="06fad-141">有兩個相關的屬性，為 MSMQ 傳輸安全性，<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>並<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`根據預設，驗證模式設定為`Windows`和保護層級設定為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="06fad-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="06fad-142">若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。</span><span class="sxs-lookup"><span data-stu-id="06fad-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="06fad-143">如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="06fad-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="06fad-144">若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例</span><span class="sxs-lookup"><span data-stu-id="06fad-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="06fad-145">如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="06fad-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>  
  
    ```xml  
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
  
2.  <span data-ttu-id="06fad-146">請務必先變更伺服器與用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="06fad-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06fad-147">將 `security mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="06fad-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06fad-148">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="06fad-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="06fad-149">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="06fad-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06fad-150">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="06fad-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06fad-151">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="06fad-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a><span data-ttu-id="06fad-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06fad-152">See also</span></span>
