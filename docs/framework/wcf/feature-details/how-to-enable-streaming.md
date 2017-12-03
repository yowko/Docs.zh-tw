---
title: "HOW TO：啟用資料流"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea506499cf6678beb51195654739f2537b98a188
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="fe188-102">HOW TO：啟用資料流</span><span class="sxs-lookup"><span data-stu-id="fe188-102">How to: Enable Streaming</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fe188-103"> 可以透過緩衝處理或資料流處理的傳輸來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="fe188-103"> can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="fe188-104">在預設的緩衝傳輸模式中，必須完整傳遞訊息，接收者才能讀取。</span><span class="sxs-lookup"><span data-stu-id="fe188-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="fe188-105">在資料流傳輸模式中，接收者不需等到訊息完全送達，就可以開始處理訊息。</span><span class="sxs-lookup"><span data-stu-id="fe188-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="fe188-106">當資訊的傳遞很漫長，但是可依序列處理時，使用資料流模式將十分有幫助。</span><span class="sxs-lookup"><span data-stu-id="fe188-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="fe188-107">當訊息太龐大而無法完整加以緩衝時，資料流模式也很有用處。</span><span class="sxs-lookup"><span data-stu-id="fe188-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="fe188-108">若要啟用資料流處理，請適當定義 `OperationContract` 並在傳輸層級啟用資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="fe188-109">若要以資料流方式處理資料</span><span class="sxs-lookup"><span data-stu-id="fe188-109">To stream data</span></span>  
  
1.  <span data-ttu-id="fe188-110">若要以資料流方式處理資料，服務的 `OperationContract` 必須滿足兩項需求：</span><span class="sxs-lookup"><span data-stu-id="fe188-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1.  <span data-ttu-id="fe188-111">用來存放要進行資料流處理之資料的參數，必須是方法中的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="fe188-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="fe188-112">例如，如果輸入訊息是要處理成資料流的訊息，這項處理作業就必須剛好只有一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="fe188-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="fe188-113">同樣地，如果要將輸出訊息處理成資料流，這項作業也必須剛好只有一個輸出參數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="fe188-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2.  <span data-ttu-id="fe188-114">至少有一個參數型別與傳回值必須是 <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message> 或 <xref:System.Xml.Serialization.IXmlSerializable>。</span><span class="sxs-lookup"><span data-stu-id="fe188-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="fe188-115">下列為資料流處理資料合約的範例。</span><span class="sxs-lookup"><span data-stu-id="fe188-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="fe188-116">`GetStream` 作業會接收一些緩衝處理的輸入資料做為 `string` (會經過緩衝處理，並傳回已經過資料流處理的 `Stream`)。</span><span class="sxs-lookup"><span data-stu-id="fe188-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="fe188-117">相反地，`UploadStream` 會接受 `Stream` (經過資料流處理) 並傳回 `bool` (經過緩衝處理)。</span><span class="sxs-lookup"><span data-stu-id="fe188-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="fe188-118">`EchoStream` 會接受並傳回 `Stream`，而這項作業也是對輸入和輸出兩種訊息都進行資料流處理的範例。</span><span class="sxs-lookup"><span data-stu-id="fe188-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="fe188-119">最後，`GetReversedStream` 不接受任何輸入，而只是傳回 `Stream` (經過資料流處理)。</span><span class="sxs-lookup"><span data-stu-id="fe188-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2.  <span data-ttu-id="fe188-120">繫結必須啟用資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="fe188-121">您可以設定 `TransferMode` 屬性，並採用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="fe188-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1.  <span data-ttu-id="fe188-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="fe188-122">`Buffered`,</span></span>  
  
    2.  <span data-ttu-id="fe188-123">`Streamed`，可啟用雙向資料流通訊。</span><span class="sxs-lookup"><span data-stu-id="fe188-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3.  <span data-ttu-id="fe188-124">`StreamedRequest`，只會啟用要求的資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4.  <span data-ttu-id="fe188-125">`StreamedResponse`，只會啟用回應的資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="fe188-126">`BasicHttpBinding` 會公開繫結上的 `TransferMode` 屬性，就像 `NetTcpBinding` 和 `NetNamedPipeBinding` 一樣。</span><span class="sxs-lookup"><span data-stu-id="fe188-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="fe188-127">`TransferMode` 屬性也可以在傳輸繫結項目上設定，並用於自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="fe188-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="fe188-128">下列範例說明如何透過程式碼與藉由變更組態檔來設定 `TransferMode`。</span><span class="sxs-lookup"><span data-stu-id="fe188-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="fe188-129">這些範例同時都會將 `maxReceivedMessageSize` 屬性設為 64 MB，以限制允許接收的最大訊息大小。</span><span class="sxs-lookup"><span data-stu-id="fe188-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="fe188-130">預設的 `maxReceivedMessageSize` 是 64 KB，但這對資料流案例來說，通常是過低的。</span><span class="sxs-lookup"><span data-stu-id="fe188-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="fe188-131">適當的配額設定取決於您的應用程式預期接收的最大訊息大小。</span><span class="sxs-lookup"><span data-stu-id="fe188-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="fe188-132">同時請注意，`maxBufferSize` 會控制緩衝處理的最大大小，請適當設定。</span><span class="sxs-lookup"><span data-stu-id="fe188-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1.  <span data-ttu-id="fe188-133">範例中的下列組態片段示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  <span data-ttu-id="fe188-134">下列程式碼片段示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  <span data-ttu-id="fe188-135">下列程式碼片段示範將 `TransferMode` 屬性設定為會在自訂 TCP 繫結上進行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  <span data-ttu-id="fe188-136">`GetStream`、`UploadStream` 和 `EchoStream` 都會處理直接從檔案傳送資料或直接將接收的資料儲存至檔案的作業。</span><span class="sxs-lookup"><span data-stu-id="fe188-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="fe188-137">下列為 `GetStream` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe188-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="fe188-138">撰寫自訂資料流</span><span class="sxs-lookup"><span data-stu-id="fe188-138">Writing a custom stream</span></span>  
  
1.  <span data-ttu-id="fe188-139">若要對每個正在傳送或接收的資料流區塊 (Chunk) 進行特殊處理，請從 <xref:System.IO.Stream> 衍生自訂資料流類別。</span><span class="sxs-lookup"><span data-stu-id="fe188-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="fe188-140">下列程式碼包含 `GetReversedStream` 方法和 `ReverseStream` 類別，是一個自訂資料流範例。</span><span class="sxs-lookup"><span data-stu-id="fe188-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="fe188-141">`GetReversedStream` 會建立並傳回 `ReverseStream` 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe188-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="fe188-142">實際的處理會在系統從這個 `ReverseStream` 物件讀取時進行。</span><span class="sxs-lookup"><span data-stu-id="fe188-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="fe188-143">`ReverseStream.Read` 方法會從基礎檔案讀取位元組區塊，然後將其序列反轉，再傳回此相反序列的位元組。</span><span class="sxs-lookup"><span data-stu-id="fe188-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="fe188-144">此方法不會反轉整個檔案內容，它只是一次反轉一個位元組區塊。</span><span class="sxs-lookup"><span data-stu-id="fe188-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="fe188-145">下列範例說明如何在對資料流讀取內容或寫入內容時執行資料流處理。</span><span class="sxs-lookup"><span data-stu-id="fe188-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fe188-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe188-146">See Also</span></span>  
 [<span data-ttu-id="fe188-147">大型的資料與資料流</span><span class="sxs-lookup"><span data-stu-id="fe188-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [<span data-ttu-id="fe188-148">資料流</span><span class="sxs-lookup"><span data-stu-id="fe188-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
