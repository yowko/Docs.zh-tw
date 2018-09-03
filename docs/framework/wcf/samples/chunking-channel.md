---
title: 區塊處理通道
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 9572ad6f88786af34252cea1f3c62d5067257b8b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470086"
---
# <a name="chunking-channel"></a><span data-ttu-id="dc35e-102">區塊處理通道</span><span class="sxs-lookup"><span data-stu-id="dc35e-102">Chunking Channel</span></span>
<span data-ttu-id="dc35e-103">傳送使用 Windows Communication Foundation (WCF) 的大型訊息時，它通常會限制用來緩衝處理這些訊息的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="dc35e-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="dc35e-104">一個可能的方案為以資料流處理訊息本文 (假設本文中有大量資料)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="dc35e-105">然而，有些通訊協定需要緩衝處理整個訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="dc35e-106">例如，可靠的傳訊和安全性。</span><span class="sxs-lookup"><span data-stu-id="dc35e-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="dc35e-107">另一個可能的方案為將較大訊息分成較小的訊息 (稱為區塊 (Chunk))，一次以單一區塊傳送這些區塊，然後在接收端重新構成較大訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="dc35e-108">應用程式本身便可執行此區塊處理和取消區塊處理，或可以使用自訂通道來進行此作業。</span><span class="sxs-lookup"><span data-stu-id="dc35e-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="dc35e-109">區塊處理通道範例會顯示如何使用自訂通訊協定或層次通道，以便區塊處理和取消區塊處理任意較大訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="dc35e-110">區塊處理應該只能在要傳送的整個訊息已建構完成之後運用。</span><span class="sxs-lookup"><span data-stu-id="dc35e-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="dc35e-111">區塊處理通道應該只能是安全性通道和可靠工作階段通道下的一層。</span><span class="sxs-lookup"><span data-stu-id="dc35e-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc35e-112">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="dc35e-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc35e-113">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="dc35e-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dc35e-114">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="dc35e-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dc35e-115">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="dc35e-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc35e-116">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="dc35e-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="dc35e-117">區塊處理通道假設前提和限制</span><span class="sxs-lookup"><span data-stu-id="dc35e-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="dc35e-118">訊息結構</span><span class="sxs-lookup"><span data-stu-id="dc35e-118">Message Structure</span></span>  
 <span data-ttu-id="dc35e-119">區塊處理通道會對要區塊處理的訊息假設下列訊息結構：</span><span class="sxs-lookup"><span data-stu-id="dc35e-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="dc35e-120">使用 ServiceModel 時，只有一個輸入參數的合約作業會針對其輸入訊息，遵守此訊息類型。</span><span class="sxs-lookup"><span data-stu-id="dc35e-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="dc35e-121">同樣地，具有一個輸出參數或傳回值的合約作業會針對其輸出訊息，遵守此訊息類型。</span><span class="sxs-lookup"><span data-stu-id="dc35e-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="dc35e-122">下列是這類作業的範例：</span><span class="sxs-lookup"><span data-stu-id="dc35e-122">The following are examples of such operations:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a><span data-ttu-id="dc35e-123">工作階段</span><span class="sxs-lookup"><span data-stu-id="dc35e-123">Sessions</span></span>  
 <span data-ttu-id="dc35e-124">區塊處理通道需要以排序的訊息 (區塊) 傳遞順序，確實傳遞訊息一次。</span><span class="sxs-lookup"><span data-stu-id="dc35e-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="dc35e-125">這表示基礎通道堆疊必須可為工作階段。</span><span class="sxs-lookup"><span data-stu-id="dc35e-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="dc35e-126">傳輸 (例如，TCP 傳輸) 或工作階段通訊協定通道 (例如，ReliableSession 通道) 可提供工作階段。</span><span class="sxs-lookup"><span data-stu-id="dc35e-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="dc35e-127">非同步傳送和接收</span><span class="sxs-lookup"><span data-stu-id="dc35e-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="dc35e-128">不會在此版本的區塊處理通道範例中實作非同步傳送和接收方法。</span><span class="sxs-lookup"><span data-stu-id="dc35e-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="dc35e-129">區塊處理通訊協定</span><span class="sxs-lookup"><span data-stu-id="dc35e-129">Chunking Protocol</span></span>  
 <span data-ttu-id="dc35e-130">區塊處理通道所定義的通訊協定，會指定一連串區塊的開始和結束，以及每個區塊的序號。</span><span class="sxs-lookup"><span data-stu-id="dc35e-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="dc35e-131">下列三個範例訊息會示範開始、區塊和結束訊息，其中的註解會描述每一項的主要概念。</span><span class="sxs-lookup"><span data-stu-id="dc35e-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="dc35e-132">開始訊息</span><span class="sxs-lookup"><span data-stu-id="dc35e-132">Start Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a><span data-ttu-id="dc35e-133">區塊訊息</span><span class="sxs-lookup"><span data-stu-id="dc35e-133">Chunk Message</span></span>  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a><span data-ttu-id="dc35e-134">結束訊息</span><span class="sxs-lookup"><span data-stu-id="dc35e-134">End Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="dc35e-135">區塊處理通道架構</span><span class="sxs-lookup"><span data-stu-id="dc35e-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="dc35e-136">區塊處理通道是一種高層級的 `IDuplexSessionChannel`，並會遵循一般通道架構。</span><span class="sxs-lookup"><span data-stu-id="dc35e-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="dc35e-137">`ChunkingBindingElement` 則可以建置 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="dc35e-138">要求 `ChunkingChannelFactory` 時，可建立 `ChunkingChannel` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc35e-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="dc35e-139">接受新的內部通道時，`ChunkingChannelListener` 會建立 `ChunkingChannel` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc35e-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="dc35e-140">`ChunkingChannel` 本身則是負責傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="dc35e-141">在下一個層級中，`ChunkingChannel` 需要數個元件才能實作區塊處理通訊協定。</span><span class="sxs-lookup"><span data-stu-id="dc35e-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="dc35e-142">在傳送端中，通道會使用名稱為 `XmlDictionaryWriter` 且執行實際區塊處理的自訂 `ChunkingWriter`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-142">On the send side, the channel uses a custom `XmlDictionaryWriter` called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="dc35e-143">`ChunkingWriter` 會使用內部通道直接傳送區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="dc35e-144">使用自訂 `XmlDictionaryWriter` 可讓您在寫入原始訊息的較大本文時，傳送出區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="dc35e-145">這表示您不會緩衝處理整個原始訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-145">This means we do not buffer the entire original message.</span></span>  
  
 <span data-ttu-id="dc35e-146">![區塊處理通道](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span><span class="sxs-lookup"><span data-stu-id="dc35e-146">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span></span>  
  
 <span data-ttu-id="dc35e-147">在接收端上，`ChunkingChannel` 會從內部通道提取訊息，並將這些訊息傳遞給自訂 `XmlDictionaryReader` (稱為 `ChunkingReader`)，而這個項目會將傳入的區塊重新構成原始訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom `XmlDictionaryReader` called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="dc35e-148">`ChunkingChannel` 會將此 `ChunkingReader` 包裝在自訂 `Message` 實作 (稱為 `ChunkingMessage`)，並將此訊息傳回上一層。</span><span class="sxs-lookup"><span data-stu-id="dc35e-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="dc35e-149">`ChunkingReader` 和 `ChunkingMessage` 的組合可讓您在上一層讀取原始訊息本文時，進行取消區塊處理，而不需要緩衝處理整個原始訊息本文。</span><span class="sxs-lookup"><span data-stu-id="dc35e-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="dc35e-150">您可在 `ChunkingReader` 擁有的佇列中，緩衝處理傳入的區塊，最多為已緩衝處理區塊可設定數目的最大值。</span><span class="sxs-lookup"><span data-stu-id="dc35e-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="dc35e-151">達到此上限時，讀取器會等待讓上一層清空佇列中的訊息 (也就是只從原始訊息本文讀取)，或直到到達接收逾時上限為止。</span><span class="sxs-lookup"><span data-stu-id="dc35e-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 <span data-ttu-id="dc35e-152">![區塊處理通道](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span><span class="sxs-lookup"><span data-stu-id="dc35e-152">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span></span>  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="dc35e-153">區塊處理程式設計模型</span><span class="sxs-lookup"><span data-stu-id="dc35e-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="dc35e-154">服務開發人員可以將 `ChunkingBehavior` 屬性套用至合約內的作業，即可指定要區塊處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="dc35e-155">屬性 (Attribute) 會公開 `AppliesTo` 屬性 (Property)，讓開發人員指定是否要將區塊處理套用至輸入訊息、輸出訊息或兩者皆套用。</span><span class="sxs-lookup"><span data-stu-id="dc35e-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="dc35e-156">下列範例會示範 `ChunkingBehavior` 屬性的用法：</span><span class="sxs-lookup"><span data-stu-id="dc35e-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 <span data-ttu-id="dc35e-157">從這個程式設計模型中，`ChunkingBindingElement` 會編譯動作 URI 的清單，而這些動作 URI 會識別要區塊處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="dc35e-158">每個傳出訊息的動作都會與此清單進行比較，以判斷應該區塊處理訊息或直接傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="dc35e-159">實作傳送作業</span><span class="sxs-lookup"><span data-stu-id="dc35e-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="dc35e-160">在高層級中，傳送作業會先檢查是否必須區塊處理傳出訊息，如果不需要，會使用內部通道直接傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="dc35e-161">如果必須區塊處理訊息，傳送作業會建立新的 `ChunkingWriter`，並在傳出訊息上呼叫 `WriteBodyContents`，以傳遞至此 `ChunkingWriter`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="dc35e-162">`ChunkingWriter` 接著會執行訊息區塊處理 (包括將原始訊息標頭複製至開始區塊訊息)，然後使用內部通道傳送區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="dc35e-163">一些不太重要的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="dc35e-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="dc35e-164">傳送作業會先呼叫 `ThrowIfDisposedOrNotOpened`，確認已開啟 `CommunicationState`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="dc35e-165">傳送會經過同步處理，以便每次只會為一個工作階段傳送一個訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="dc35e-166">傳送區塊處理訊息時，會重設名稱為 `ManualResetEvent` 的 `sendingDone`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="dc35e-167">傳送結束區塊訊息之後，就會設定此事件。</span><span class="sxs-lookup"><span data-stu-id="dc35e-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="dc35e-168">傳送方法在嘗試傳送傳出訊息之前，會先等待設定此事件。</span><span class="sxs-lookup"><span data-stu-id="dc35e-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="dc35e-169">傳送會鎖定 `CommunicationObject.ThisLock`，以在傳送時避免變更同步狀態。</span><span class="sxs-lookup"><span data-stu-id="dc35e-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="dc35e-170">如需 <xref:System.ServiceModel.Channels.CommunicationObject> 狀態和狀態機器的詳細資訊，請參閱 <xref:System.ServiceModel.Channels.CommunicationObject> 文件。</span><span class="sxs-lookup"><span data-stu-id="dc35e-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="dc35e-171">傳遞至傳送作業的逾時會當做整個傳送作業的逾時，而這包括傳送所有區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="dc35e-172">已選擇自訂 `XmlDictionaryWriter` 設計，可避免緩衝處理整個原始訊息本文。</span><span class="sxs-lookup"><span data-stu-id="dc35e-172">The custom `XmlDictionaryWriter` design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="dc35e-173">如果要使用 `XmlDictionaryReader` 取得本文上的 `message.GetReaderAtBodyContents`，將會緩衝處理整個本文。</span><span class="sxs-lookup"><span data-stu-id="dc35e-173">If we were to get an `XmlDictionaryReader` on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="dc35e-174">不過您會具有傳遞至 `XmlDictionaryWriter` 的自訂 `message.WriteBodyContents`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-174">Instead, we have a custom `XmlDictionaryWriter` that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="dc35e-175">當訊息呼叫寫入器上的 WriteBase64 時，寫入器會將區塊封裝至訊息，然後使用內部通道傳送這些訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="dc35e-176">傳送區塊之前，會封鎖 WriteBase64。</span><span class="sxs-lookup"><span data-stu-id="dc35e-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="dc35e-177">實作接收作業</span><span class="sxs-lookup"><span data-stu-id="dc35e-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="dc35e-178">在高層級中，接收作業會先檢查傳入訊息不是 `null`，而且其動做為 `ChunkingAction`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="dc35e-179">如果不符合這兩個準則，會從接收作業傳回未變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="dc35e-180">否則，接收作業會建立新的 `ChunkingReader` 和包裝住的新 `ChunkingMessage` (透過呼叫 `GetNewChunkingMessage`)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="dc35e-181">傳回新的 `ChunkingMessage` 之前，接收作業會使用執行緒集區的執行緒來執行 `ReceiveChunkLoop`，而它會呼叫迴圈中的 `innerChannel.Receive`，並在接收結束區塊訊息或達到接收逾時之前將區塊傳回 `ChunkingReader`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="dc35e-182">一些不太重要的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="dc35e-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="dc35e-183">和傳送作業一樣，接收作業會先呼叫 `ThrowIfDisposedOrNotOepned`，確認已開啟 `CommunicationState`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="dc35e-184">接收也會經過同步處理，以便一次只能從工作階段接收一個訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="dc35e-185">其重要性在於，一旦接收開始區塊訊息，所有後續接收的訊息預期都會在此新區塊序列內進行區塊處理，直到接收結束區塊訊息為止。</span><span class="sxs-lookup"><span data-stu-id="dc35e-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="dc35e-186">在接收到目前屬於已取消區塊處理之訊息的所有區塊之前，接收作業無法從內部通道中提取訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="dc35e-187">若要完成此作業，接收作業會使用名稱為 `ManualResetEvent` 的 `currentMessageCompleted`，此項目會在接收結束區塊訊息時設定，並在接收新的開始區塊訊息時重設。</span><span class="sxs-lookup"><span data-stu-id="dc35e-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="dc35e-188">和傳送作業不同，接收作業在接收時不會制止同步處理的狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="dc35e-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="dc35e-189">例如，接收時可以呼叫關閉作業，並等待直到完成接收擱置的原始訊息，或達到指定的逾時值為止。</span><span class="sxs-lookup"><span data-stu-id="dc35e-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="dc35e-190">傳遞至接收作業的逾時會當做整個接收作業的逾時，而這包括接收所有區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="dc35e-191">如果使用訊息的層級正在以低於傳入區塊訊息的速率使用訊息本文，`ChunkingReader` 會緩衝處理這些傳入區塊，而且最多可緩衝處理 `ChunkingBindingElement.MaxBufferedChunks` 所限制的區塊數。</span><span class="sxs-lookup"><span data-stu-id="dc35e-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="dc35e-192">一旦達到該限制，在使用緩衝處理的區塊或達到接收逾時之前，就不會再從較低層級提取區塊。</span><span class="sxs-lookup"><span data-stu-id="dc35e-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="dc35e-193">CommunicationObject 覆寫</span><span class="sxs-lookup"><span data-stu-id="dc35e-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="dc35e-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="dc35e-194">OnOpen</span></span>  
 <span data-ttu-id="dc35e-195">`OnOpen` 會呼叫 `innerChannel.Open`，以開啟內部通道。</span><span class="sxs-lookup"><span data-stu-id="dc35e-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="dc35e-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="dc35e-196">OnClose</span></span>  
 <span data-ttu-id="dc35e-197">`OnClose` 會先將 `stopReceive` 設定為 `true`，以將擱置的 `ReceiveChunkLoop` 標示為停止。</span><span class="sxs-lookup"><span data-stu-id="dc35e-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="dc35e-198">接著會等待`receiveStopped``ManualResetEvent`，此值會設定當`ReceiveChunkLoop`會停止。</span><span class="sxs-lookup"><span data-stu-id="dc35e-198">It then waits for the `receiveStopped``ManualResetEvent`, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="dc35e-199">假設在指定的逾時內停止 `ReceiveChunkLoop`，`OnClose` 會利用剩下的逾時呼叫 `innerChannel.Close`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="dc35e-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="dc35e-200">OnAbort</span></span>  
 <span data-ttu-id="dc35e-201">`OnAbort` 會呼叫 `innerChannel.Abort`，以中止內部通道。</span><span class="sxs-lookup"><span data-stu-id="dc35e-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="dc35e-202">如果有擱置的 `ReceiveChunkLoop`，會從擱置的 `innerChannel.Receive` 呼叫中收到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dc35e-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="dc35e-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="dc35e-203">OnFaulted</span></span>  
 <span data-ttu-id="dc35e-204">通道發生錯誤時，`ChunkingChannel` 不需要特殊行為，因此不會覆寫 `OnFaulted`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="dc35e-205">實作通道處理站</span><span class="sxs-lookup"><span data-stu-id="dc35e-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="dc35e-206">`ChunkingChannelFactory` 會負責建立 `ChunkingDuplexSessionChannel` 的執行個體，並負責將狀態轉換串聯 (Cascade) 至內部通道處理站。</span><span class="sxs-lookup"><span data-stu-id="dc35e-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="dc35e-207">`OnCreateChannel` 會使用內部通道處理站來建立 `IDuplexSessionChannel` 內部通道。</span><span class="sxs-lookup"><span data-stu-id="dc35e-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="dc35e-208">接著會建立新的 `ChunkingDuplexSessionChannel`，傳遞此內部通道和要區塊處理的訊息動作清單，以及接收時要緩衝處理的區塊數上限。</span><span class="sxs-lookup"><span data-stu-id="dc35e-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="dc35e-209">要區塊處理的訊息動作清單以及要緩衝處理的區塊數上限，是在其建構函式中傳遞至 `ChunkingChannelFactory` 的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="dc35e-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="dc35e-210">`ChunkingBindingElement` 上的區段會描述取得這些值的位置。</span><span class="sxs-lookup"><span data-stu-id="dc35e-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="dc35e-211">`OnOpen`、`OnClose`、`OnAbort` 與其非同步對等項目，會在內部通道處理站上呼叫相對應的狀態轉換方法。</span><span class="sxs-lookup"><span data-stu-id="dc35e-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="dc35e-212">實作通道接聽程式</span><span class="sxs-lookup"><span data-stu-id="dc35e-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="dc35e-213">`ChunkingChannelListener` 是內部通道接聽程式周圍的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="dc35e-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="dc35e-214">除了該內部通道接聽程式的委派呼叫以外，其主要函式會包裝新的 `ChunkingDuplexSessionChannels` (從內部通道接聽程式接受之通道的周圍)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="dc35e-215">會在 `OnAcceptChannel` 和 `OnEndAcceptChannel` 中進行此動作。</span><span class="sxs-lookup"><span data-stu-id="dc35e-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="dc35e-216">新建立的 `ChunkingDuplexSessionChannel` 會傳遞內部通道，以及先前描述的其他參數。</span><span class="sxs-lookup"><span data-stu-id="dc35e-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="dc35e-217">實作繫結項目和繫結</span><span class="sxs-lookup"><span data-stu-id="dc35e-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="dc35e-218">`ChunkingBindingElement` 會負責建立 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="dc35e-219">`ChunkingBindingElement`檢查是否在 T `CanBuildChannelFactory` \<T > 和`CanBuildChannelListener` \<T > 的類型`IDuplexSessionChannel`（僅支援區塊處理通道的通道） 和繫結中的其他繫結項目支援此通道型別。</span><span class="sxs-lookup"><span data-stu-id="dc35e-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="dc35e-220">`BuildChannelFactory`\<T > 先檢查要求的通道型別可以建置，然後取得要區塊處理的訊息動作清單。</span><span class="sxs-lookup"><span data-stu-id="dc35e-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="dc35e-221">如需詳細資訊，請參閱下列章節。</span><span class="sxs-lookup"><span data-stu-id="dc35e-221">For more information, see the following section.</span></span> <span data-ttu-id="dc35e-222">接著會建立新的 `ChunkingChannelFactory`，並傳遞內部通道處理站 (從 `context.BuildInnerChannelFactory<IDuplexSessionChannel>` 傳回)、訊息動作清單和要緩衝處理的區塊數上限。</span><span class="sxs-lookup"><span data-stu-id="dc35e-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="dc35e-223">從 `MaxBufferedChunks` 屬性取得的區塊數上限會由 `ChunkingBindingElement` 公開。</span><span class="sxs-lookup"><span data-stu-id="dc35e-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="dc35e-224">`BuildChannelListener<T>` 擁有可建立 `ChunkingChannelListener` 並傳遞至內部通道接聽程式的相似實作。</span><span class="sxs-lookup"><span data-stu-id="dc35e-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="dc35e-225">此範例中包含範例繫結，名稱為 `TcpChunkingBinding`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="dc35e-226">此繫結是由兩個繫結項目所組成：`TcpTransportBindingElement` 和 `ChunkingBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="dc35e-227">除了公開 `MaxBufferedChunks` 屬性以外，繫結也會設定一些 `TcpTransportBindingElement` 屬性，例如 `MaxReceivedMessageSize` (針對標頭將它設定為 `ChunkingUtils.ChunkSize` + 100KB 位元組)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="dc35e-228">`TcpChunkingBinding` 也會實作 `IBindingRuntimePreferences`，並從 `ReceiveSynchronously` 方法傳回 true，而這個方法指出只會實作同步接收呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc35e-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="dc35e-229">判斷要區塊處理的訊息</span><span class="sxs-lookup"><span data-stu-id="dc35e-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="dc35e-230">區塊處理通道只會區塊處理透過 `ChunkingBehavior` 屬性識別的訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="dc35e-231">`ChunkingBehavior` 類別會實作 `IOperationBehavior`，並可透過呼叫 `AddBindingParameter` 方法來實作。</span><span class="sxs-lookup"><span data-stu-id="dc35e-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="dc35e-232">在此方法中，`ChunkingBehavior` 會檢查其 `AppliesTo` 屬性的值 (`InMessage`、`OutMessage` 或這兩者)，以判斷應該區塊處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="dc35e-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="dc35e-233">接著會取得每個訊息的動作 (從 `OperationDescription` 上的訊息集合)，並將該動作新增至 `ChunkingBindingParameter` 執行個體中所含的字串集合。</span><span class="sxs-lookup"><span data-stu-id="dc35e-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="dc35e-234">接著會將此 `ChunkingBindingParameter` 新增至提供的 `BindingParameterCollection`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="dc35e-235">當繫結項目建置通道處理站或通道接聽程式時，此 `BindingParameterCollection` 會從 `BindingContext` 內部傳遞至繫結中的每個繫結項目。</span><span class="sxs-lookup"><span data-stu-id="dc35e-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="dc35e-236">`ChunkingBindingElement`的實作`BuildChannelFactory<T>`並`BuildChannelListener<T>`提取此`ChunkingBindingParameter`共`BindingContext’`s `BindingParameterCollection`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="dc35e-237">`ChunkingBindingParameter` 中內含的動作集合接著會傳遞至 `ChunkingChannelFactory` 或 `ChunkingChannelListener`，後者接著會將動作集合傳遞至 `ChunkingDuplexSessionChannel`。</span><span class="sxs-lookup"><span data-stu-id="dc35e-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="dc35e-238">執行範例</span><span class="sxs-lookup"><span data-stu-id="dc35e-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dc35e-239">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="dc35e-239">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="dc35e-240">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="dc35e-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="dc35e-241">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="dc35e-242">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="dc35e-243">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="dc35e-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="dc35e-244">先執行 Service.exe，然後執行 Client.exe，再查看兩個主控台視窗上的輸出。</span><span class="sxs-lookup"><span data-stu-id="dc35e-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="dc35e-245">執行範例時，預期會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="dc35e-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="dc35e-246">用戶端：</span><span class="sxs-lookup"><span data-stu-id="dc35e-246">Client:</span></span>  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 <span data-ttu-id="dc35e-247">伺服器:</span><span class="sxs-lookup"><span data-stu-id="dc35e-247">Server:</span></span>  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc35e-248">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc35e-248">See Also</span></span>
