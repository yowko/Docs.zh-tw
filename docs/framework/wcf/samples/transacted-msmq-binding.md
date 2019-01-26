---
title: 交易 MSMQ 繫結
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 9574320478741f71c7c98d7e21a24c80a31b72a2
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066047"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="ac913-102">交易 MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="ac913-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="ac913-103">這個範例會示範如何使用訊息佇列 (MSMQ) 執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="ac913-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
>  <span data-ttu-id="ac913-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ac913-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="ac913-105">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="ac913-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ac913-106">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="ac913-107">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac913-107">The service receives messages from the queue.</span></span> <span data-ttu-id="ac913-108">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="ac913-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="ac913-109">當交易是用於傳送與接收訊息時，實際上會出現兩個不同的交易。</span><span class="sxs-lookup"><span data-stu-id="ac913-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="ac913-110">當用戶端在異動範圍內傳送訊息時，對用戶端與用戶端佇列管理員來說，異動屬於本機範圍。</span><span class="sxs-lookup"><span data-stu-id="ac913-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="ac913-111">當服務在交易範圍內接收訊息時，對服務與接收佇列管理員來說，交易屬於本機範圍。</span><span class="sxs-lookup"><span data-stu-id="ac913-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="ac913-112">您一定要記住，用戶端與服務並未參與相同的異動，而是在配合佇列執行其作業時 (例如傳送與接收) 使用不同的異動。</span><span class="sxs-lookup"><span data-stu-id="ac913-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

 <span data-ttu-id="ac913-113">在這個範例中，用戶端會從交易範圍內將訊息批次傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="ac913-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="ac913-114">接著，服務會在所定義的交易範圍內接收傳送至佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac913-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

 <span data-ttu-id="ac913-115">服務合約是 `IOrderProcessor`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ac913-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="ac913-116">介面會定義適合與佇列搭配使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="ac913-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="ac913-117">服務行為會定義 `TransactionScopeRequired` 已設為 `true` 的作業行為，</span><span class="sxs-lookup"><span data-stu-id="ac913-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="ac913-118">這樣會確定此方法存取的任何資源管理員都使用從佇列擷取訊息時所使用的相同異動範圍。</span><span class="sxs-lookup"><span data-stu-id="ac913-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="ac913-119">這種行為也會確保當方法擲回例外狀況時，訊息會傳回至佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="ac913-120">如果未設定這個作業行為，已佇列通道所建立的交易就會從佇列讀取訊息、並且在分派前就自動進行認可，因此，如果此作業失敗，訊息就會遺失。</span><span class="sxs-lookup"><span data-stu-id="ac913-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="ac913-121">最常見的案例，就是登記於用來從佇列讀取訊息之異動的服務作業，如下列程式碼所示範。</span><span class="sxs-lookup"><span data-stu-id="ac913-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
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

 <span data-ttu-id="ac913-122">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="ac913-122">The service is self hosted.</span></span> <span data-ttu-id="ac913-123">使用 MSMQ 傳輸時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="ac913-124">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="ac913-124">This can be done manually or through code.</span></span> <span data-ttu-id="ac913-125">在這個範例中，該服務包含的程式碼會檢查佇列的存在，並在佇列不存在時建立佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="ac913-126">佇列名稱會從組態檔中讀取。</span><span class="sxs-lookup"><span data-stu-id="ac913-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="ac913-127">使用基底位址[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生服務 proxy。</span><span class="sxs-lookup"><span data-stu-id="ac913-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
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

 <span data-ttu-id="ac913-128">MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中，如下面的範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="ac913-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
>  <span data-ttu-id="ac913-129">使用 <xref:System.Messaging> 來建立佇列時，佇列會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ac913-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="ac913-130">Windows Communication Foundation (WCF) 端點會使用包含 net.msmq 配置的佇列位址、 使用"localhost"代表本機電腦，並在其路徑中使用正斜線。</span><span class="sxs-lookup"><span data-stu-id="ac913-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

 <span data-ttu-id="ac913-131">用戶端會建立一個異動範圍。</span><span class="sxs-lookup"><span data-stu-id="ac913-131">The client creates a transaction scope.</span></span> <span data-ttu-id="ac913-132">與佇列的通訊會發生在交易範圍內，導致其被視為原子單位 (Atomic Unit)，其中會將所有訊息都傳送至佇列，或是不傳送任何訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="ac913-133">呼叫交易範圍上的 <xref:System.Transactions.TransactionScope.Complete%2A>，即可認可交易。</span><span class="sxs-lookup"><span data-stu-id="ac913-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
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

 <span data-ttu-id="ac913-134">若要檢查交易是否正常運作，請將交易範例標記為註解來修改用戶端 (如下列範例程式碼所示方式)，並重建方案，然後執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="ac913-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

 <span data-ttu-id="ac913-135">因為交易尚未完成，所以這些訊息不會傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

 <span data-ttu-id="ac913-136">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ac913-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ac913-137">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ac913-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ac913-138">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="ac913-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="ac913-139">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="ac913-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="ac913-140">您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="ac913-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac913-141">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ac913-141">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="ac913-142">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ac913-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="ac913-143">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="ac913-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="ac913-144">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="ac913-145">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="ac913-146">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="ac913-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="ac913-147">開啟 Visual Studio 2012 中的 伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="ac913-147">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="ac913-148">依序展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac913-148">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="ac913-149">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="ac913-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="ac913-150">請檢查**Transactional**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="ac913-150">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="ac913-151">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac913-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="ac913-152">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ac913-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4.  <span data-ttu-id="ac913-153">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ac913-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="ac913-154">根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。</span><span class="sxs-lookup"><span data-stu-id="ac913-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="ac913-155">MSMQ 傳輸安全性有兩個相關屬性：<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> 和 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac913-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="ac913-156">根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="ac913-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="ac913-157">若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。</span><span class="sxs-lookup"><span data-stu-id="ac913-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="ac913-158">如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac913-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="ac913-159">若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例</span><span class="sxs-lookup"><span data-stu-id="ac913-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1.  <span data-ttu-id="ac913-160">如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列的範例組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ac913-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

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

2.  <span data-ttu-id="ac913-161">請務必先變更伺服器與用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="ac913-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ac913-162">將 `security mode` 設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="ac913-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ac913-163">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ac913-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ac913-164">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ac913-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ac913-165">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ac913-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac913-166">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ac913-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="ac913-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac913-167">See also</span></span>
