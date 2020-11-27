---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 1cb0cd4e7300920afb900af0291b9e3d3dc778b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268283"
---
# <a name="srmp"></a><span data-ttu-id="0dae1-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="0dae1-102">SRMP</span></span>

<span data-ttu-id="0dae1-103">這個範例示範如何使用訊息佇列 (MSMQ)，透過 HTTP 來執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="0dae1-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="0dae1-104">在佇列通訊中，用戶端會使用佇列與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="0dae1-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0dae1-105">更精確地說，用戶端會傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="0dae1-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0dae1-106">服務會接收來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="0dae1-106">The service receives messages from the queue.</span></span> <span data-ttu-id="0dae1-107">因此，服務與用戶端不需同時執行，就能使用佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="0dae1-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="0dae1-108">MSMQ 允許使用 HTTP (包括使用 HTTPS) 傳送訊息至佇列。</span><span class="sxs-lookup"><span data-stu-id="0dae1-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="0dae1-109">在此範例中，我們會示範如何使用 Windows Communication Foundation (WCF) 佇列的通訊，以及如何透過 HTTP 傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="0dae1-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="0dae1-110">MSMQ 會使用稱為 SRMP 的通訊協定，這是適用在透過 HTTP 進行通訊的 SOAP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0dae1-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0dae1-111">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0dae1-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0dae1-112">確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0dae1-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0dae1-113">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0dae1-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0dae1-114">若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0dae1-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="0dae1-115">在 [ **新增/移除 Windows 元件**] 中執行範例之前，請確定 MSMQ 已安裝 HTTP 支援。</span><span class="sxs-lookup"><span data-stu-id="0dae1-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="0dae1-116">安裝 HTTP 支援時，會自動安裝網際網路資訊服務 (IIS)，並在 IIS 中為 MSMQ 新增通訊協定支援。</span><span class="sxs-lookup"><span data-stu-id="0dae1-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="0dae1-117">如果您想要確定會在通訊時使用 HTTP，則可以讓 MSMQ 在固定模式中執行。</span><span class="sxs-lookup"><span data-stu-id="0dae1-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="0dae1-118">這可以確保任何訊息都無法使用非 HTTP 傳輸進到電腦上裝載的佇列中。</span><span class="sxs-lookup"><span data-stu-id="0dae1-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="0dae1-119">在您選取 MSMQ 在強化模式中執行之後，電腦需要在 Windows Server 2003 上重新開機。</span><span class="sxs-lookup"><span data-stu-id="0dae1-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="0dae1-120">執行服務。</span><span class="sxs-lookup"><span data-stu-id="0dae1-120">Run the service.</span></span>  
  
8. <span data-ttu-id="0dae1-121">執行該用戶端。</span><span class="sxs-lookup"><span data-stu-id="0dae1-121">Run the client.</span></span> <span data-ttu-id="0dae1-122">確定您已將端點位址改為指向電腦名稱或 IP 位址，而非指向 localhost。</span><span class="sxs-lookup"><span data-stu-id="0dae1-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="0dae1-123">用戶端便會傳送訊息並結束。</span><span class="sxs-lookup"><span data-stu-id="0dae1-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dae1-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="0dae1-124">Requirements</span></span>  

 <span data-ttu-id="0dae1-125">若要執行這個範例，除了安裝 MSMQ 之外，還必須在服務及用戶端機器兩端都安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="0dae1-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0dae1-126">示範</span><span class="sxs-lookup"><span data-stu-id="0dae1-126">Demonstrates</span></span>  

 <span data-ttu-id="0dae1-127">此範例示範如何使用 MSMQ over HTTP 傳送 WCF 佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="0dae1-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="0dae1-128">這也會呼叫 SRMP 訊息處理。</span><span class="sxs-lookup"><span data-stu-id="0dae1-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="0dae1-129">傳送佇列訊息時，在傳送端電腦上的 MSMQ 會透過 TCP 或 HTTP 傳輸，將訊息傳輸至接收端佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="0dae1-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="0dae1-130">如果使用者選擇 SRMP，就表示他選擇了 HTTP 做為佇列傳輸的傳輸機制。</span><span class="sxs-lookup"><span data-stu-id="0dae1-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="0dae1-131">SRMP Secure (SRMPS) 會啟用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="0dae1-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dae1-132">範例</span><span class="sxs-lookup"><span data-stu-id="0dae1-132">Example</span></span>  

 <span data-ttu-id="0dae1-133">此範例程式碼是以交易範例為基礎。</span><span class="sxs-lookup"><span data-stu-id="0dae1-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="0dae1-134">當傳送訊息至佇列以及從佇列接收訊息時，其使用 SRMP 的方式，與使用原生通訊協定傳送和接收訊息的方式相同。</span><span class="sxs-lookup"><span data-stu-id="0dae1-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="0dae1-135">您可以變更用戶端的組態，指定所選擇的佇列傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0dae1-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="0dae1-136">佇列傳輸通訊協定可以是原生、SRMP 或 SrmpSecure 的其中一種通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0dae1-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="0dae1-137">根據預設，傳輸通訊協定為「原生」。</span><span class="sxs-lookup"><span data-stu-id="0dae1-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="0dae1-138">在這個範例中，用戶端和服務會在組態中指定使用 SRMP。</span><span class="sxs-lookup"><span data-stu-id="0dae1-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="0dae1-139">相對於傳輸安全性，SRMP 會有一些限制。</span><span class="sxs-lookup"><span data-stu-id="0dae1-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="0dae1-140">預設的 MSMQ 傳輸安全性需要有 Active Directory，而這會要求傳送端佇列管理員和接收端佇列管理員都必須位於相同的 Windows 網域中。</span><span class="sxs-lookup"><span data-stu-id="0dae1-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="0dae1-141">如果要超越 HTTP 界限傳送訊息，這就變得不可行。</span><span class="sxs-lookup"><span data-stu-id="0dae1-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="0dae1-142">因此，預設的傳輸安全性將無法運作。</span><span class="sxs-lookup"><span data-stu-id="0dae1-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="0dae1-143">如果想要有傳輸安全性，就必須將傳輸安全性設定為憑證，</span><span class="sxs-lookup"><span data-stu-id="0dae1-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="0dae1-144">而您也可以使用訊息安全性來保護訊息的安全性。</span><span class="sxs-lookup"><span data-stu-id="0dae1-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="0dae1-145">在這個範例中，會同時關閉傳輸和訊息安全性，以便於說明 SRMP 訊息處理。</span><span class="sxs-lookup"><span data-stu-id="0dae1-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="0dae1-146">執行範例時會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="0dae1-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="0dae1-147">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0dae1-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0dae1-148">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0dae1-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0dae1-149">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="0dae1-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0dae1-150">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0dae1-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
