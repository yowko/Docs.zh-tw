---
title: 單一 ListenUri 的多個端點
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 6249690b7fdc95affd21eee13e0c6e2af1c4f8a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755970"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="54f59-102">單一 ListenUri 的多個端點</span><span class="sxs-lookup"><span data-stu-id="54f59-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="54f59-103">這個範例會示範在單一 `ListenUri` 裝載多個端點的服務。</span><span class="sxs-lookup"><span data-stu-id="54f59-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="54f59-104">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="54f59-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54f59-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="54f59-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="54f59-106">如所示[多個端點](../../../../docs/framework/wcf/samples/multiple-endpoints.md)範例中，服務可以裝載多個端點，各有不同的位址，可能也有不同的繫結。</span><span class="sxs-lookup"><span data-stu-id="54f59-106">As demonstrated in the [Multiple Endpoints](../../../../docs/framework/wcf/samples/multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="54f59-107">這個範例會示範如何在相同位址裝載多個端點。</span><span class="sxs-lookup"><span data-stu-id="54f59-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="54f59-108">此外，這個範例還會示範服務端點所具有兩種位址的差異：`EndpointAddress` 和 `ListenUri`。</span><span class="sxs-lookup"><span data-stu-id="54f59-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="54f59-109">`EndpointAddress` 是服務的邏輯位址。</span><span class="sxs-lookup"><span data-stu-id="54f59-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="54f59-110">這是 SOAP 訊息傳送至的目標位址。</span><span class="sxs-lookup"><span data-stu-id="54f59-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="54f59-111">`ListenUri` 是服務的實際位址，</span><span class="sxs-lookup"><span data-stu-id="54f59-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="54f59-112">含有連接埠和位址資訊，而服務端點實際上會接聽目前電腦上的訊息。</span><span class="sxs-lookup"><span data-stu-id="54f59-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="54f59-113">在大多數情況下，這些位址不需要有所不同，因為未明確指定 `ListenUri` 時，預設會是端點之 `EndpointAddress` 的 URI。</span><span class="sxs-lookup"><span data-stu-id="54f59-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="54f59-114">在少數情況下，例如設定路由器時區分這些位址就很有用，該路由器可能會接受傳送至一些不同服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="54f59-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="54f59-115">服務</span><span class="sxs-lookup"><span data-stu-id="54f59-115">Service</span></span>  
 <span data-ttu-id="54f59-116">這個範例中的服務有兩個合約，`ICalculator` 和 `IEcho`。</span><span class="sxs-lookup"><span data-stu-id="54f59-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="54f59-117">除了可自訂的 `IMetadataExchange` 端點外，還有三個應用程式端點，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="54f59-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="54f59-118">這三個端點都會裝載在相同的 `ListenUri`，並使用相同的 `binding`。相同 `ListenUri` 上的端點必須具有相同的繫結，這樣才可以共用接聽電腦上該實際位址之訊息的單一通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="54f59-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="54f59-119">每個端點的 `address` 為 URN。雖然一般來說，位址表示實際位置，事實上位址可以是任何種類的 URI，因為位址的用途就是比對和篩選，如本範例所示。</span><span class="sxs-lookup"><span data-stu-id="54f59-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="54f59-120">因為所有的三個端點都共用相同`ListenUri`，當訊息抵達時，Windows Communication Foundation (WCF) 必須決定訊息的目的地的哪一個端點。</span><span class="sxs-lookup"><span data-stu-id="54f59-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, Windows Communication Foundation (WCF) must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="54f59-121">每個端點都具有由兩個部分組成的訊息篩選條件：位址篩選條件和合約篩選條件。</span><span class="sxs-lookup"><span data-stu-id="54f59-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="54f59-122">位址篩選條件會比對 SOAP 訊息的 `To` 和服務端點的位址。</span><span class="sxs-lookup"><span data-stu-id="54f59-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="54f59-123">例如，只有指定 `To "Urn:OtherEcho"` 的訊息是這個服務第三個端點的候選。</span><span class="sxs-lookup"><span data-stu-id="54f59-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="54f59-124">合約篩選條件會比對與特定合約作業相關聯的動作。</span><span class="sxs-lookup"><span data-stu-id="54f59-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="54f59-125">例如，具有 `IEcho` 動作的訊息。</span><span class="sxs-lookup"><span data-stu-id="54f59-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="54f59-126">`Echo` 會比對這個服務第二和第三個端點的合約篩選條件，因為這兩個端點都會裝載 `IEcho` 合約。</span><span class="sxs-lookup"><span data-stu-id="54f59-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="54f59-127">因此，結合位址篩選條件和合約篩選條件之後，就可以將抵達這個服務之 `ListenUri` 的每個訊息路由至正確的端點。</span><span class="sxs-lookup"><span data-stu-id="54f59-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="54f59-128">第三個端點與其他兩個端點不同，它會接受從其他端點傳送至不同位址的訊息。</span><span class="sxs-lookup"><span data-stu-id="54f59-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="54f59-129">第一個和第二個端點可以依合約 (傳入訊息的動作) 區分。</span><span class="sxs-lookup"><span data-stu-id="54f59-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="54f59-130">用戶端</span><span class="sxs-lookup"><span data-stu-id="54f59-130">Client</span></span>  
 <span data-ttu-id="54f59-131">由於伺服器上的端點有兩個不同的位址，用戶端端點也會有兩個位址。</span><span class="sxs-lookup"><span data-stu-id="54f59-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="54f59-132">在伺服器和用戶端上，邏輯位址稱為 `EndpointAddress`。</span><span class="sxs-lookup"><span data-stu-id="54f59-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="54f59-133">不過，在伺服器上，實際位址稱為 `ListenUri`，在用戶端上，實際位址則稱為 `Via`。</span><span class="sxs-lookup"><span data-stu-id="54f59-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="54f59-134">根據預設，伺服器上的這兩個位址是相同的。</span><span class="sxs-lookup"><span data-stu-id="54f59-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="54f59-135">若要在用戶端上指定與端點位址不同的 `Via`，請使用 `ClientViaBehavior`：</span><span class="sxs-lookup"><span data-stu-id="54f59-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="54f59-136">位址照例是來自 Svcutil.exe 所產生的用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="54f59-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="54f59-137">`Via` (對應至服務的 `ListenUri`) 不會顯示在服務的中繼資料中，因此這個資訊必須傳送到超出範圍的用戶端 (就和服務的中繼資料位址一樣)。</span><span class="sxs-lookup"><span data-stu-id="54f59-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="54f59-138">這個範例中的用戶端會將訊息傳送至伺服器的三個應用程式端點，示範它可以與這三個端點通訊 (也可以區別這三個端點)，即使這三個端點具有相同的 `Via` 也是一樣。</span><span class="sxs-lookup"><span data-stu-id="54f59-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54f59-139">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="54f59-139">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="54f59-140">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="54f59-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="54f59-141">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="54f59-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="54f59-142">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="54f59-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54f59-143">如果是跨電腦，您必須以服務電腦的名稱取代 Client.cs 檔案中的 localhost。</span><span class="sxs-lookup"><span data-stu-id="54f59-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54f59-144">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="54f59-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="54f59-145">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="54f59-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="54f59-146">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="54f59-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="54f59-147">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="54f59-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
