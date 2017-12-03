---
title: "寄不出的信件佇列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2cd61bf9c1e3d7165b76f55f1808b04c979d4d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="dead-letter-queues"></a><span data-ttu-id="f6840-102">寄不出的信件佇列</span><span class="sxs-lookup"><span data-stu-id="f6840-102">Dead Letter Queues</span></span>
<span data-ttu-id="f6840-103">這個範例示範如何處理已傳遞失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="f6840-104">它基礎[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="f6840-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f6840-105">這個範例會使用 `netMsmqBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="f6840-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="f6840-106">這個服務是自我裝載的主控台應用程式，可讓您觀察接收佇列訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6840-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="f6840-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6840-108">這個範例會示範每個應用程式的「寄不出的信件」佇列，而此佇列只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中使用。</span><span class="sxs-lookup"><span data-stu-id="f6840-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="f6840-109">您可以修改此範例，以便在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上使用 MSMQ 3.0 的預設全系統佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 <span data-ttu-id="f6840-110">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="f6840-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f6840-111">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f6840-112">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-112">The service receives messages from the queue.</span></span> <span data-ttu-id="f6840-113">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="f6840-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f6840-114">因為佇列通訊會有一定的期間不活動，您可能需要在訊息上建立與某段存留時間值的關聯，以確保不會在過了這段時間，還將訊息傳遞到應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6840-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="f6840-115">另有一些情況，應用程式必須獲知訊息是否傳遞失敗。</span><span class="sxs-lookup"><span data-stu-id="f6840-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="f6840-116">如果發生這些情況，像是訊息的存留時間已過，或是訊息傳遞失敗等，都會將訊息放在寄不出的信件佇列中。</span><span class="sxs-lookup"><span data-stu-id="f6840-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="f6840-117">進行傳送的應用程式就可以接著從寄不出的信件佇列讀取訊息，然後採取更正動作 (舉凡不做動作到修改傳遞失敗原因等)，再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>  
  
 <span data-ttu-id="f6840-118">在 `NetMsmqBinding` 繫結中，會使用下列屬性來表示寄不出的信件佇列：</span><span class="sxs-lookup"><span data-stu-id="f6840-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>  
  
-   <span data-ttu-id="f6840-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> 屬性，用來表示用戶端所需之寄不出的信件佇列種類。</span><span class="sxs-lookup"><span data-stu-id="f6840-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="f6840-120">這個列舉具有下列值：</span><span class="sxs-lookup"><span data-stu-id="f6840-120">This enumeration has the following values:</span></span>  
  
-   <span data-ttu-id="f6840-121">`None`：沒有用戶端需要之寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-121">`None`: No dead-letter queue is required by the client.</span></span>  
  
-   <span data-ttu-id="f6840-122">`System`：系統之寄不出的信件佇列，用來存放無法傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="f6840-123">電腦上執行的所有應用程式會共用系統之寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>  
  
-   <span data-ttu-id="f6840-124">`Custom`：使用 <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 屬性所指定的自訂寄不出的信件佇列，用來存放無法傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="f6840-125">這項功能只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="f6840-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="f6840-126">當應用程式必須使用自己的寄不出的信件佇列，而不與執行於同一台電腦的其他應用程式共用時，會使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="f6840-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>  
  
-   <span data-ttu-id="f6840-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 屬性，用來表示要當做寄不出的信件佇列使用的特定佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="f6840-128">這只能在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="f6840-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="f6840-129">在這個範例中，用戶端會從交易範圍內傳送一批訊息至服務，並隨意為這些訊息指定很低的「存留時間」值 (約 2 秒)。</span><span class="sxs-lookup"><span data-stu-id="f6840-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="f6840-130">用戶端還會指定要使用的自訂寄不出的信件佇列，以便將過期的訊息加入。</span><span class="sxs-lookup"><span data-stu-id="f6840-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>  
  
 <span data-ttu-id="f6840-131">用戶端應用程式可以讀取寄不出的信件佇列中的訊息，然後重新嘗試傳送訊息，或是修正導致原始訊息置入寄不出的信件佇列的錯誤，再傳送該訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="f6840-132">在範例中，用戶端會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-132">In the sample, the client displays an error message.</span></span>  
  
 <span data-ttu-id="f6840-133">服務合約是 `IOrderProcessor`，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f6840-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="f6840-134">服務中的程式碼範例是屬於[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="f6840-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="f6840-135">與服務進行的通訊會在異動範圍內發生。</span><span class="sxs-lookup"><span data-stu-id="f6840-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="f6840-136">服務會讀取佇列中的訊息、執行作業，然後顯示作業的結果。</span><span class="sxs-lookup"><span data-stu-id="f6840-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="f6840-137">應用程式也會為寄不出的信件訊息建立寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>  
  
```  
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
  
 <span data-ttu-id="f6840-138">用戶端的組態會指定很短的期間讓訊息送達服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="f6840-139">如果無法在指定期間內傳輸訊息，訊息就會過期，然後移入寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6840-140">用戶端可能會在指定的時間內將訊息傳遞到服務佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="f6840-141">為確保您看得到寄不出的信件服務的實際執行過程，您必須先執行用戶端，再啟動服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="f6840-142">此訊息會逾時，然後傳遞到寄不出的信件服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-142">The message times out and is delivered to the dead-letter service.</span></span>  
  
 <span data-ttu-id="f6840-143">應用程式必須定義要當做寄不出的信件佇列使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="f6840-144">如果未指定佇列，就會使用預設全系統交易式寄不出的信件佇列，將無法傳遞的訊息加入佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="f6840-145">在這個範例中，用戶端應用程式會指定它自己的應用程式寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-145">In this example, the client application specifies its own application dead-letter queue.</span></span>  
  
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
  
 <span data-ttu-id="f6840-146">寄不出的信件訊息服務會從寄不出的信件佇列讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="f6840-147">寄不出的信件訊息服務會實作 `IOrderProcessor` 合約。</span><span class="sxs-lookup"><span data-stu-id="f6840-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="f6840-148">然而，這個實作不是要用來處理訂單。</span><span class="sxs-lookup"><span data-stu-id="f6840-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="f6840-149">寄不出的信件訊息服務是用戶端服務，並沒有處理訂單的能力。</span><span class="sxs-lookup"><span data-stu-id="f6840-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6840-150">寄不出的信件佇列是用戶端佇列，而且是用戶端佇列管理員本機上的佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>  
  
 <span data-ttu-id="f6840-151">寄不出的信件訊息服務實作會檢查訊息傳遞失敗的原因，然後採取更正措施。</span><span class="sxs-lookup"><span data-stu-id="f6840-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="f6840-152">訊息失敗的原因可以擷取自兩個列舉：<xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> 和 <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>。</span><span class="sxs-lookup"><span data-stu-id="f6840-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="f6840-153">您可以從 <xref:System.ServiceModel.Channels.MsmqMessageProperty> 擷取 <xref:System.ServiceModel.OperationContext>，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f6840-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>  
  
```  
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
    ….  
}  
```  
  
 <span data-ttu-id="f6840-154">寄不出的信件佇列中的訊息是針對處理訊息之服務所發出的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="f6840-155">因此，當寄不出的信件訊息服務從佇列讀取訊息時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 通道層會發覺端點中有不相符的情況，從而不分派訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-155">Therefore, when the dead-letter message service reads messages from the queue, the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f6840-156">在本例中，訊息是針對訂單處理服務發出的，但是會由寄不出的信件訊息服務接收。</span><span class="sxs-lookup"><span data-stu-id="f6840-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="f6840-157">為了接收針對不同端點發出的訊息，在 `ServiceBehavior` 中會指定用來比對所有位址的位址篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f6840-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="f6840-158">若要順利處理從寄不出的信件佇列中讀取的訊息，就必須這麼做。</span><span class="sxs-lookup"><span data-stu-id="f6840-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>  
  
 <span data-ttu-id="f6840-159">在這個範例中，如果失敗的原因是訊息逾時，寄不出的信件訊息服務將會重新傳送訊息。對於其他所有原因，則顯示傳遞失敗，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f6840-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>  
  
```  
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
  
 <span data-ttu-id="f6840-160">下列範例示範寄不出的信件訊息的組態：</span><span class="sxs-lookup"><span data-stu-id="f6840-160">The following sample shows the configuration for a dead-letter message:</span></span>  
  
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
  
 <span data-ttu-id="f6840-161">在執行的範例中，有 3 個可執行檔要執行，藉以觀察每個應用程式 (用戶端、服務和寄不出的信件服務) 運用寄不出的信件佇列的方式；每個應用程式都會從各自寄不出的信件佇列讀取訊息，然後重新傳送給服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="f6840-162">這些都是會在主控台視窗中產生輸出的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6840-162">All are console applications with output in console windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6840-163">因為佇列正在使用中，所以用戶端與服務不需要同時啟動與執行。</span><span class="sxs-lookup"><span data-stu-id="f6840-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f6840-164">您可以執行用戶端，關閉用戶端，然後再啟動服務，服務還是會收到訊息。</span><span class="sxs-lookup"><span data-stu-id="f6840-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="f6840-165">您應該啟動服務再加以關閉，這樣就可以建立佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-165">You should start the service and shut it down so that the queue can be created.</span></span>  
  
 <span data-ttu-id="f6840-166">執行用戶端時，用戶端會顯示訊息：</span><span class="sxs-lookup"><span data-stu-id="f6840-166">When running the client, the client displays the message:</span></span>  
  
```  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f6840-167">用戶端已嘗試傳送訊息，但是因為逾時期限很短，訊息已過期，且已加入至每個應用程式之寄不出的信件佇列中。</span><span class="sxs-lookup"><span data-stu-id="f6840-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>  
  
 <span data-ttu-id="f6840-168">此時，請執行寄不出的信件服務，它會讀取訊息並顯示錯誤碼，然後將訊息重新傳回到服務。</span><span class="sxs-lookup"><span data-stu-id="f6840-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>  
  
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
  
 <span data-ttu-id="f6840-169">服務會啟動，然後讀取重送的訊息，再加以處理。</span><span class="sxs-lookup"><span data-stu-id="f6840-169">The service starts and then reads the resent message and processes it.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6840-170">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="f6840-170">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f6840-171">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f6840-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f6840-172">如果服務優先執行，它就會檢查以確定佇列存在。</span><span class="sxs-lookup"><span data-stu-id="f6840-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f6840-173">如果佇列不存在，服務將建立一個佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f6840-174">您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f6840-175">請依照下列步驟，在 Windows 2008 中建立佇列。</span><span class="sxs-lookup"><span data-stu-id="f6840-175">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="f6840-176">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="f6840-176">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="f6840-177">展開**功能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f6840-177">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="f6840-178">以滑鼠右鍵按一下**私用訊息佇列**，然後選取**新增**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="f6840-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="f6840-179">請檢查**交易式**方塊。</span><span class="sxs-lookup"><span data-stu-id="f6840-179">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="f6840-180">輸入`ServiceModelSamplesTransacted`做為新佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6840-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="f6840-181">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f6840-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f6840-182">此範例中執行單一或跨電腦組態變更佇列名稱適當地使用電腦的完整名稱取代 localhost，依照[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6840-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f6840-183">若要在加入至工作群組的電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="f6840-183">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="f6840-184">如果您的電腦不是網域的一部分，請將驗證模式和保護層級設定為 `None`，以關閉傳輸安全性，如下面的範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="f6840-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="f6840-185">請透過設定端點的 `bindingConfiguration` 屬性，確定端點與繫結相關聯。</span><span class="sxs-lookup"><span data-stu-id="f6840-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>  
  
2.  <span data-ttu-id="f6840-186">請務必先變更 DeadLetterService、伺服器和用戶端上的組態，再執行範例。</span><span class="sxs-lookup"><span data-stu-id="f6840-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6840-187">將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="f6840-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="f6840-188">註解</span><span class="sxs-lookup"><span data-stu-id="f6840-188">Comments</span></span>  
 <span data-ttu-id="f6840-189">根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。</span><span class="sxs-lookup"><span data-stu-id="f6840-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f6840-190">`MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。</span><span class="sxs-lookup"><span data-stu-id="f6840-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f6840-191">根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="f6840-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f6840-192">若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。</span><span class="sxs-lookup"><span data-stu-id="f6840-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f6840-193">如果您在不屬於網域的電腦上執行這個範例，就會收到下列錯誤：「使用者的內部訊息佇列憑證不存在」。</span><span class="sxs-lookup"><span data-stu-id="f6840-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6840-194">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f6840-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f6840-195">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f6840-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f6840-196">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f6840-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6840-197">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f6840-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a><span data-ttu-id="f6840-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6840-198">See Also</span></span>
