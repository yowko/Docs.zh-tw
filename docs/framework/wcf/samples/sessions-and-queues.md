---
title: 工作階段和佇列
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 623077450157b0bf87b85a85309adc10511b32b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007873"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="0bbc6-102">工作階段和佇列</span><span class="sxs-lookup"><span data-stu-id="0bbc6-102">Sessions and Queues</span></span>
<span data-ttu-id="0bbc6-103">這個範例示範如何透過訊息佇列 (MSMQ) 傳輸，傳送和接收佇列通訊中的一組相關訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="0bbc6-104">這個範例會使用 `netMsmqBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="0bbc6-105">這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bbc6-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0bbc6-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0bbc6-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0bbc6-109">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0bbc6-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="0bbc6-111">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0bbc6-112">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0bbc6-113">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-113">The service receives messages from the queue.</span></span> <span data-ttu-id="0bbc6-114">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="0bbc6-115">有時，用戶端會傳送一組在群組中彼此有關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="0bbc6-116">當訊息必須一併處理或依照指定的順序處理時，可以使用佇列將它們集合成為群組，以便單一接收應用程式進行處理。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="0bbc6-117">如果伺服器群組上有數個接收應用程式，而且必須確保同一群組的訊息是由相同接收應用程式所處理時，這種做法尤其重要。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="0bbc6-118">佇列工作階段提供的機制是用來傳送和接收一組必須全部一次處理完成的相關訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="0bbc6-119">但是佇列工作階段中必須有交易，您才會看到這種模式。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="0bbc6-120">在範例中，用戶端會傳送一些訊息給服務做為單一異動範圍內工作階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="0bbc6-121">服務合約為 `IOrderTaker`，這會定義適合與佇列搭配使用的單向服務。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="0bbc6-122">在下列範例程式碼中示範用於合約的 <xref:System.ServiceModel.SessionMode> 將會顯示該訊息是工作階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="0bbc6-123">服務會定義服務作業，但定義的方式只是讓第一項作業登記在異動中，而不自動完成異動。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="0bbc6-124">後續的作業也會登記在相同的交易中，但是不自動完成。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="0bbc6-125">只有工作階段中的最後一項作業，才會自動完成交易。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="0bbc6-126">因此，服務合約中的數個作業引動過程都會使用同一個異動。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="0bbc6-127">如果有任何作業擲回例外狀況，異動就會復原，並將工作階段重新放回佇列中。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="0bbc6-128">要等到最後一項作業完成，異動才會獲得認可。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="0bbc6-129">服務會使用 `PerSession` 做為 <xref:System.ServiceModel.InstanceContextMode>，以便在同一個服務執行個體上接收工作階段中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="0bbc6-130">服務會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-130">The service is self hosted.</span></span> <span data-ttu-id="0bbc6-131">使用 MSMQ 傳輸時，必須事先建立使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0bbc6-132">這個動作可手動或透過程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-132">This can be done manually or through code.</span></span> <span data-ttu-id="0bbc6-133">在這個範例中，服務包含檢查佇列是否存在並在需要時建立佇列的 <xref:System.Messaging> 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="0bbc6-134">您可以使用 <xref:System.Configuration.ConfigurationManager.AppSettings%2A> 類別，從組態檔中讀取佇列名稱。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="0bbc6-135">MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="0bbc6-136">服務的端點是定義在組態檔的 system.serviceModel 區段中，並且會指定 `netMsmqBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="0bbc6-137">用戶端會建立一個交易範圍。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-137">The client creates a transaction scope.</span></span> <span data-ttu-id="0bbc6-138">工作階段中的所有訊息都會傳送到該異動範圍內的佇列，形成不可部分完成的原子單位 (Atomic Unit)，其中的訊息若不是全部成功，就是全部失敗。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="0bbc6-139">藉由呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 來認可交易。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
>  <span data-ttu-id="0bbc6-140">您對工作階段中的所有訊息只能使用單一交易，而且必須在認可交易之前傳送工作階段中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="0bbc6-141">關閉用戶端就會關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-141">Closing the client closes the session.</span></span> <span data-ttu-id="0bbc6-142">因此，必須在異動完成之前先關閉用戶端，才能將工作階段中的所有訊息傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="0bbc6-143">當您執行範例時，用戶端與服務活動都會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0bbc6-144">您可以查看來自用戶端的服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0bbc6-145">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="0bbc6-146">請注意，因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="0bbc6-147">您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="0bbc6-148">在用戶端上：</span><span class="sxs-lookup"><span data-stu-id="0bbc6-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="0bbc6-149">在服務上：</span><span class="sxs-lookup"><span data-stu-id="0bbc6-149">On the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0bbc6-150">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0bbc6-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0bbc6-151">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0bbc6-152">若要建置C#， C++，或 Visual Basic.NET 版本的解決方案，請依照下列中的指示[Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0bbc6-153">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="0bbc6-154">根據預設，傳輸安全性會透過 <xref:System.ServiceModel.NetMsmqBinding> 啟用。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0bbc6-155">有兩個 MSMQ 傳輸安全性相關屬性的那就是，<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>並<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`根據預設，驗證模式設定為`Windows`和保護層級設定為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0bbc6-156">若要 MSMQ 提供驗證及簽署功能，MSMQ 必須是網域的一部分，而且必須安裝 MSMQ 的 Active Directory 整合選項。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0bbc6-157">如果您在不符合這些條件的電腦上執行這個範例，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0bbc6-158">若要在加入工作群組，或是沒有 Active Directory 整合的電腦上執行這個範例</span><span class="sxs-lookup"><span data-stu-id="0bbc6-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="0bbc6-159">如果您的電腦不是網域的一部分，或是沒有安裝 Active Directory 整合，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="0bbc6-160">請務必先變更伺服器與用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bbc6-161">將安全性模式設定為 `None`，相當於將 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="0bbc6-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
