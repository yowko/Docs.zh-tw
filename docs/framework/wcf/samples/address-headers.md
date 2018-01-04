---
title: "位址標頭"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafd6ec911464dcc2b936b9f9fc74b9bc39808bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="address-headers"></a><span data-ttu-id="bb383-102">位址標頭</span><span class="sxs-lookup"><span data-stu-id="bb383-102">Address Headers</span></span>
<span data-ttu-id="bb383-103">位址標頭範例會示範用戶端如何將參考參數傳遞至使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的服務。</span><span class="sxs-lookup"><span data-stu-id="bb383-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb383-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="bb383-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bb383-105">WS-Addressing 規格會將端點參考的概念定義成針對特定 Web 服務端點的定址方式。</span><span class="sxs-lookup"><span data-stu-id="bb383-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="bb383-106">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，端點參考會使用 `EndpointAddress` 類別模型化，而 `EndpointAddress` 是 `ServiceEndpoint` 類別之 [位址] 欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="bb383-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="bb383-107">端點參考模型的一部分，是每個參考可以包含一些會新增額外識別資訊的參考參數。</span><span class="sxs-lookup"><span data-stu-id="bb383-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="bb383-108">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，這些參考參數會模型化為 `AddressHeader` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb383-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="bb383-109">在這個範例中，用戶端會新增用戶端端點之 `EndpointAddress` 的參考參數。</span><span class="sxs-lookup"><span data-stu-id="bb383-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="bb383-110">服務會尋找這個參考參數，然後在其 "Hello" 服務作業的邏輯中使用這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="bb383-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="bb383-111">用戶端</span><span class="sxs-lookup"><span data-stu-id="bb383-111">Client</span></span>  
 <span data-ttu-id="bb383-112">對於要傳送參考參數的用戶端，它必須將 `AddressHeader` 新增至 `EndpointAddress` 的 `ServiceEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="bb383-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="bb383-113">因為 `EndpointAddress` 類別是不變的，所以必須使用 `EndpointAddressBuilder` 類別才能修改端點位址。</span><span class="sxs-lookup"><span data-stu-id="bb383-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="bb383-114">下列程式碼會初始化用戶端，以便將參考參數當做其訊息部分來傳送。</span><span class="sxs-lookup"><span data-stu-id="bb383-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="bb383-115">這段程式碼會建立以原始 `EndpointAddressBuilder` 做為初始值的 `EndpointAddress`。</span><span class="sxs-lookup"><span data-stu-id="bb383-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="bb383-116">接下來，它會加入新建的位址標頭，呼叫具有特定名稱、命名空間與值的 `CreateAddressHeadercreates` 標頭。</span><span class="sxs-lookup"><span data-stu-id="bb383-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="bb383-117">此時的值為 "John"。</span><span class="sxs-lookup"><span data-stu-id="bb383-117">Here the value is "John".</span></span> <span data-ttu-id="bb383-118">一旦標頭新增至產生器後，`ToEndpointAddress()` 方法便會將產生器 (可變的) 轉換回端點位址 (不變的)，此位址已指派回該用戶端端點的 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="bb383-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="bb383-119">現在，當用戶端呼叫 `Console.WriteLine(client.Hello());` 時，服務就能夠取得這個位址參數的值，即顯示於用戶端結果輸出中的值。</span><span class="sxs-lookup"><span data-stu-id="bb383-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="bb383-120">伺服器</span><span class="sxs-lookup"><span data-stu-id="bb383-120">Server</span></span>  
 <span data-ttu-id="bb383-121">服務作業 `Hello()` 的實作會使用目前 `OperationContext`，檢查傳入訊息上的標頭值。</span><span class="sxs-lookup"><span data-stu-id="bb383-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="bb383-122">這段程式碼會逐一查看傳入訊息上的所有標頭，以便尋找屬於含有特定名稱之參考參數的標頭。</span><span class="sxs-lookup"><span data-stu-id="bb383-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="bb383-123">如果有找到該參數，它會讀取參數的值，然後將該值儲存在 "id" 變數中。</span><span class="sxs-lookup"><span data-stu-id="bb383-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bb383-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="bb383-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bb383-125">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bb383-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bb383-126">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="bb383-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bb383-127">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bb383-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb383-128">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="bb383-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb383-129">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="bb383-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bb383-130">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="bb383-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb383-131">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="bb383-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="bb383-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb383-132">See Also</span></span>
