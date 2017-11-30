---
title: "檢視訊息記錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10a4c0e9e2680e2f858f2a0e3e1045ab346c3f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="viewing-message-logs"></a><span data-ttu-id="916e3-102">檢視訊息記錄</span><span class="sxs-lookup"><span data-stu-id="916e3-102">Viewing Message Logs</span></span>
<span data-ttu-id="916e3-103">此主題描述如何檢視訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="916e3-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="916e3-104">在服務追蹤檢視器中檢視訊息記錄</span><span class="sxs-lookup"><span data-stu-id="916e3-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="916e3-105">訊息將會如同由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 處理的方式轉換。</span><span class="sxs-lookup"><span data-stu-id="916e3-105">A message will be transformed as it is processed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="916e3-106">因此，記錄的訊息只會反應記錄當時的訊息內容，而不是在網路上傳輸的內容。</span><span class="sxs-lookup"><span data-stu-id="916e3-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="916e3-107">由於訊息記錄輸出與訊息的傳輸格式沒有任何關係，因此訊息記錄會一律輸出解碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="916e3-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="916e3-108">如果您已適當地設定訊息記錄，則任何記錄的訊息應為純文字。</span><span class="sxs-lookup"><span data-stu-id="916e3-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="916e3-109">例如，使用二進位訊息編碼器不會影響到記錄之訊息的格式 (純文字)。</span><span class="sxs-lookup"><span data-stu-id="916e3-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="916e3-110">XmlWriterTraceListener 的輸出是包含 XML 片段順序的檔案。</span><span class="sxs-lookup"><span data-stu-id="916e3-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="916e3-111">請注意該檔案不是有效的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="916e3-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="916e3-112">建議您改用[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)檢視訊息記錄檔。</span><span class="sxs-lookup"><span data-stu-id="916e3-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="916e3-113">如需有關如何使用這項工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和疑難排解](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="916e3-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="916e3-114">服務追蹤檢視器，訊息會列在**訊息** 索引標籤。導致處理錯誤或與處理錯誤相關的訊息，會視錯誤的嚴重性以黃色 (警告層級) 或紅色 (錯誤層級) 反白顯示。</span><span class="sxs-lookup"><span data-stu-id="916e3-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="916e3-115">在訊息上按兩下會在處理要求的內容中顯示訊息追蹤。</span><span class="sxs-lookup"><span data-stu-id="916e3-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="916e3-116">如果訊息沒有標頭，就不會記錄 `<header/>` 標記。</span><span class="sxs-lookup"><span data-stu-id="916e3-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="916e3-117">檢視用戶端、轉送與服務記錄的訊息</span><span class="sxs-lookup"><span data-stu-id="916e3-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="916e3-118">環境中可能會包含將訊息傳送給轉送的用戶端，之後再將訊息轉寄給服務。</span><span class="sxs-lookup"><span data-stu-id="916e3-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="916e3-119">當所有三個位置，已啟用訊息記錄和所有三個訊息的記錄檔中檢視[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時，將不正確地呈現訊息記錄交換。</span><span class="sxs-lookup"><span data-stu-id="916e3-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="916e3-120">這是因為訊息標頭中的 `CorrelationId` 和 `ActivityId`，對每個傳送接收組來說不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="916e3-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="916e3-121">您可以使用下列其中一種方法解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="916e3-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="916e3-122">只能檢視中的三個訊息記錄檔的兩個[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)在任何時間。</span><span class="sxs-lookup"><span data-stu-id="916e3-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="916e3-123">如果您必須檢視中的所有三個記錄[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時，您可以修改轉送服務來建立新<xref:System.ServiceModel.Channels.Message>執行個體。</span><span class="sxs-lookup"><span data-stu-id="916e3-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="916e3-124">這個執行個體應該是傳入訊息本文的複本，加上所有的標頭 (除了 `ActivityId` 和 `Action` 標頭以外)。</span><span class="sxs-lookup"><span data-stu-id="916e3-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="916e3-125">下列範例程式碼示範如何進行這項操作：</span><span class="sxs-lookup"><span data-stu-id="916e3-125">The following example code demonstrates how to do this.</span></span>  
  
```  
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="916e3-126">不正確之訊息記錄內容的例外情況</span><span class="sxs-lookup"><span data-stu-id="916e3-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="916e3-127">在下列情況中，記錄的訊息可能不是在網路上傳輸之八位元資料流的完整表示。</span><span class="sxs-lookup"><span data-stu-id="916e3-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="916e3-128">針對 BasicHttpBinding，在 /addressing/none 命名空間中會記錄傳入訊息的封套標頭。</span><span class="sxs-lookup"><span data-stu-id="916e3-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="916e3-129">空白可能不相符。</span><span class="sxs-lookup"><span data-stu-id="916e3-129">Whitespaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="916e3-130">針對傳入訊息，空白項目可以用不同方式表示。</span><span class="sxs-lookup"><span data-stu-id="916e3-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="916e3-131">例如，\<標記 >\</標記 > 而不是\<標記 / ></span><span class="sxs-lookup"><span data-stu-id="916e3-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="916e3-132">當藉由預設或明確設定 enableLoggingKnownPii="true" 停用已知 PII 記錄時。</span><span class="sxs-lookup"><span data-stu-id="916e3-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="916e3-133">啟用編碼以轉換至 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="916e3-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916e3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="916e3-134">See Also</span></span>  
 [<span data-ttu-id="916e3-135">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="916e3-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="916e3-136">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="916e3-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="916e3-137">訊息記錄</span><span class="sxs-lookup"><span data-stu-id="916e3-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
