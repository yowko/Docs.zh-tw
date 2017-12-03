---
title: "資料流"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0cbbae6ae8ba486791c525b70e8d208880661d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="stream"></a><span data-ttu-id="14830-102">資料流</span><span class="sxs-lookup"><span data-stu-id="14830-102">Stream</span></span>
<span data-ttu-id="14830-103">這個資料流範例將示範資料流傳輸模式通訊的使用。</span><span class="sxs-lookup"><span data-stu-id="14830-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="14830-104">服務會公開數個傳送和接收資料流的作業。</span><span class="sxs-lookup"><span data-stu-id="14830-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="14830-105">這個範例會自我裝載。</span><span class="sxs-lookup"><span data-stu-id="14830-105">This sample is self-hosted.</span></span> <span data-ttu-id="14830-106">用戶端和服務都是主控台程式。</span><span class="sxs-lookup"><span data-stu-id="14830-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14830-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="14830-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="14830-108"> 可以使用兩種傳輸模式進行通訊：緩衝或資料流。</span><span class="sxs-lookup"><span data-stu-id="14830-108"> can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="14830-109">在預設的緩衝傳輸模式中，必須完整傳遞訊息，接收者才能讀取。</span><span class="sxs-lookup"><span data-stu-id="14830-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="14830-110">在資料流傳輸模式中，接收者不需等到訊息完全送達，就可以開始處理訊息。</span><span class="sxs-lookup"><span data-stu-id="14830-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="14830-111">當資訊的傳遞很漫長，但是可依序列處理時，使用資料流模式將十分有幫助。</span><span class="sxs-lookup"><span data-stu-id="14830-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="14830-112">當訊息太龐大而無法完整加以緩衝時，資料流模式也很有用處。</span><span class="sxs-lookup"><span data-stu-id="14830-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="14830-113">資料流和服務合約</span><span class="sxs-lookup"><span data-stu-id="14830-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="14830-114">設計服務合約時，資料流是一項需要考慮的重點。</span><span class="sxs-lookup"><span data-stu-id="14830-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="14830-115">如果作業會接收或傳回大量的資料，您應該考慮透過資料流處理這筆資料，以避免因為要緩衝輸入或輸出訊息而佔用太多記憶體。</span><span class="sxs-lookup"><span data-stu-id="14830-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="14830-116">若要以資料流方式處理資料，存放該資料的參數必須是訊息中的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="14830-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="14830-117">例如，如果輸入訊息是要處理成資料流的訊息，這項處理作業就必須剛好只有一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="14830-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="14830-118">同樣地，如果要將輸出訊息處理成資料流，這項作業也必須剛好只有一個輸出參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="14830-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="14830-119">不論是何種情況，參數或傳回值型別都必須是 `Stream`、`Message` 或 `IXmlSerializable`。</span><span class="sxs-lookup"><span data-stu-id="14830-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="14830-120">下列是這個資料流範例中使用的服務合約。</span><span class="sxs-lookup"><span data-stu-id="14830-120">The following is the service contract used in this streaming sample.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="14830-121">`GetStream` 作業會接收經過緩衝處理做為字串的一些輸入資料，然後傳回經過資料流處理的 `Stream`。</span><span class="sxs-lookup"><span data-stu-id="14830-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="14830-122">相反地，`UploadStream` 會接受 `Stream` (經過資料流處理) 並傳回 `bool` (經過緩衝處理)。</span><span class="sxs-lookup"><span data-stu-id="14830-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="14830-123">`EchoStream` 會接受並傳回 `Stream`，而這項作業也是對輸入和輸出兩種訊息都進行資料流處理的範例。</span><span class="sxs-lookup"><span data-stu-id="14830-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="14830-124">最後，`GetReversedStream` 不接受任何輸入，而只是傳回 `Stream` (經過資料流處理)。</span><span class="sxs-lookup"><span data-stu-id="14830-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="14830-125">啟用資料流處理的傳輸</span><span class="sxs-lookup"><span data-stu-id="14830-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="14830-126">如先前所述，定義作業合約就可以在程式設計模型層級上提供資料流。</span><span class="sxs-lookup"><span data-stu-id="14830-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="14830-127">如果您在此停止作業，則傳輸仍然會緩衝整個訊息內容。</span><span class="sxs-lookup"><span data-stu-id="14830-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="14830-128">若要啟用傳輸資料流，請在傳輸的繫結項目上選取傳輸模式。</span><span class="sxs-lookup"><span data-stu-id="14830-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="14830-129">繫結項目包含可設為 `TransferMode`、`Buffered`、`Streamed` 或 `StreamedRequest` 的 `StreamedResponse` 屬性。</span><span class="sxs-lookup"><span data-stu-id="14830-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="14830-130">將傳輸模式設為 `Streamed` 可啟用雙向資料流通訊。</span><span class="sxs-lookup"><span data-stu-id="14830-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="14830-131">將傳輸模式設為 `StreamedRequest` 或 `StreamedResponse` 可以分別啟用只有要求或回應方向的資料流通訊。</span><span class="sxs-lookup"><span data-stu-id="14830-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="14830-132">`basicHttpBinding` 也會公開繫結上的 `TransferMode` 屬性，就像 `NetTcpBinding` 和 `NetNamedPipeBinding` 一樣。</span><span class="sxs-lookup"><span data-stu-id="14830-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="14830-133">如果是其他傳輸模式，您必須建立自訂繫結才能設定傳輸模式。</span><span class="sxs-lookup"><span data-stu-id="14830-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="14830-134">範例中的下列組態程式碼示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理：</span><span class="sxs-lookup"><span data-stu-id="14830-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="14830-135">除了將 `transferMode` 設定為 `Streamed` 之外，上述組態程式碼還會將 `maxReceivedMessageSize` 設定為 64MB。</span><span class="sxs-lookup"><span data-stu-id="14830-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="14830-136">`maxReceivedMessageSize` 會限制允許接收的最大訊息大小，以形成保護機制。</span><span class="sxs-lookup"><span data-stu-id="14830-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="14830-137">預設的 `maxReceivedMessageSize` 是 64 KB，但這對資料流案例來說，通常是過低的。</span><span class="sxs-lookup"><span data-stu-id="14830-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="14830-138">在資料流處理時處理資料</span><span class="sxs-lookup"><span data-stu-id="14830-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="14830-139">`GetStream`、`UploadStream` 和 `EchoStream` 作業都會處理直接從檔案傳送資料或直接將接收資料儲存至檔案的作業。</span><span class="sxs-lookup"><span data-stu-id="14830-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="14830-140">但是在某些情況下，還是需要傳送或接收大量的資料，並在資料送達或收到時對其資料區塊 (Chunk) 進行某種處理。</span><span class="sxs-lookup"><span data-stu-id="14830-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="14830-141">處理此類案例的其中一種方式是，撰寫自訂資料流 (衍生自 <xref:System.IO.Stream> 的類別)，以便在讀取或寫入資料時加以處理。</span><span class="sxs-lookup"><span data-stu-id="14830-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="14830-142">例如，`GetReversedStream` 作業和 `ReverseStream` 類別即是這種方式的範例。</span><span class="sxs-lookup"><span data-stu-id="14830-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="14830-143">`GetReversedStream` 會建立並傳回 `ReverseStream` 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="14830-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="14830-144">實際的處理會在系統從這個 `ReverseStream` 物件讀取時進行。</span><span class="sxs-lookup"><span data-stu-id="14830-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="14830-145">`ReverseStream.Read` 的實作會從基礎檔案讀取位元組區塊，然後將其反向，再傳回此反向的位元組。</span><span class="sxs-lookup"><span data-stu-id="14830-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="14830-146">這並不會反向整個檔案內容；一次只反向一個位元組區塊。</span><span class="sxs-lookup"><span data-stu-id="14830-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="14830-147">下列是示範如何在對資料流讀取或寫入內容時執行資料流處理的範例。</span><span class="sxs-lookup"><span data-stu-id="14830-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```  
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="14830-148">執行範例</span><span class="sxs-lookup"><span data-stu-id="14830-148">Running the Sample</span></span>  
 <span data-ttu-id="14830-149">若要執行此範例，請先依照本文件結尾的指示建置服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="14830-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="14830-150">接下來，分別在兩個不同的主控台視窗中啟動服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="14830-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="14830-151">當用戶端啟動時，會等候您在服務就緒時按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="14830-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="14830-152">然後，用戶端先透過 HTTP 呼叫 `GetStream()`、`UploadStream()` 和 `GetReversedStream()` 方法，再透過 TCP 呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="14830-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="14830-153">下面是服務的範例輸出，接著是用戶端的範例輸出：</span><span class="sxs-lookup"><span data-stu-id="14830-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="14830-154">服務輸出：</span><span class="sxs-lookup"><span data-stu-id="14830-154">Service Output:</span></span>  
  
```  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="14830-155">用戶端輸出：</span><span class="sxs-lookup"><span data-stu-id="14830-155">Client Output:</span></span>  
  
```  
Press <ENTER> when service is ready  
------ Using HTTP ------   
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14830-156">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="14830-156">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="14830-157">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="14830-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="14830-158">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="14830-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="14830-159">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="14830-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14830-160">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="14830-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14830-161">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="14830-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14830-162">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="14830-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14830-163">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="14830-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14830-164">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="14830-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a><span data-ttu-id="14830-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14830-165">See Also</span></span>
