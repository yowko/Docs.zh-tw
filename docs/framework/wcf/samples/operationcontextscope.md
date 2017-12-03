---
title: OperationContextScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7cf84c30c5784de813f947d26b18816906ec6a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="operationcontextscope"></a><span data-ttu-id="054fd-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="054fd-102">OperationContextScope</span></span>
<span data-ttu-id="054fd-103">OperationContextScope 範例會示範如何使用標頭經由 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 呼叫傳送額外資訊。</span><span class="sxs-lookup"><span data-stu-id="054fd-103">The OperationContextScope sample demonstrates how to send extra information on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] call using headers.</span></span> <span data-ttu-id="054fd-104">在此範例中，伺服器與用戶端都是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="054fd-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="054fd-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="054fd-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="054fd-106">此範例會示範用戶端如何使用 <xref:System.ServiceModel.Channels.MessageHeader> 將額外的資訊當做 <xref:System.ServiceModel.OperationContextScope> 傳送。</span><span class="sxs-lookup"><span data-stu-id="054fd-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="054fd-107">將物件範圍設定至通道以建立 <xref:System.ServiceModel.OperationContextScope> 物件。</span><span class="sxs-lookup"><span data-stu-id="054fd-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="054fd-108">必須轉譯至遠端服務的標頭可以新增至 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="054fd-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="054fd-109">藉由存取 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>，可以在服務上擷取新增至此集合的標頭。</span><span class="sxs-lookup"><span data-stu-id="054fd-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="054fd-110">它會對多個通道進行呼叫，接著，新增至用戶端的標頭只會套用到建立 <xref:System.ServiceModel.OperationContextScope> 時所使用的通道。</span><span class="sxs-lookup"><span data-stu-id="054fd-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="054fd-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="054fd-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="054fd-112">這個範例服務會接收來自用戶端的訊息，並嘗試查閱 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> 集合中的標頭。</span><span class="sxs-lookup"><span data-stu-id="054fd-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="054fd-113">用戶端會傳遞標頭中所傳送的 GUID，而服務會擷取自訂標頭，並在有出現自訂標頭時，比較此標頭和用戶端當做引數傳遞的 GUID。</span><span class="sxs-lookup"><span data-stu-id="054fd-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```  
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =   
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,   
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+   
         "Does it match with GUID sent as parameter: {1}",   
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="054fd-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="054fd-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="054fd-115">這是會使用所產生的 proxy 的用戶端實作[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)與遠端服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="054fd-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="054fd-116">它會先建立兩個 `MessageHeaderReaderClient` 的 Proxy 物件。</span><span class="sxs-lookup"><span data-stu-id="054fd-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```  
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="054fd-117">然後，用戶端會建立 OperationContextScope，並將其範圍設定為 `client1`。</span><span class="sxs-lookup"><span data-stu-id="054fd-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="054fd-118">它會將 <xref:System.ServiceModel.Channels.MessageHeader> 新增至 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>，然後在這兩個用戶端上叫用一次呼叫。</span><span class="sxs-lookup"><span data-stu-id="054fd-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="054fd-119">它會確保只傳送標頭`client1`而不是在`client2`檢查傳回的值從`RetrieveHeader`呼叫。</span><span class="sxs-lookup"><span data-stu-id="054fd-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```  
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetreieveHeader on both the proxies. Since the OperationContextScope is tied to   
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="054fd-120">這個範例會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="054fd-120">This sample is self-hosted.</span></span> <span data-ttu-id="054fd-121">執行此範例時的範例輸出提供如下：</span><span class="sxs-lookup"><span data-stu-id="054fd-121">The following sample output from running the sample is provided:</span></span>  
  
```  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="054fd-122">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="054fd-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="054fd-123">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="054fd-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="054fd-124">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="054fd-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="054fd-125">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="054fd-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="054fd-126">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="054fd-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="054fd-127">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="054fd-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="054fd-128">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="054fd-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="054fd-129">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="054fd-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
  
## <a name="see-also"></a><span data-ttu-id="054fd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="054fd-130">See Also</span></span>
