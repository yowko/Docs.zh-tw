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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df1d796ec5009008e00391eea2987f5256df6c48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="viewing-message-logs"></a>檢視訊息記錄
此主題描述如何檢視訊息記錄。  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>在服務追蹤檢視器中檢視訊息記錄  
 訊息將會如同由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 處理的方式轉換。 因此，記錄的訊息只會反應記錄當時的訊息內容，而不是在網路上傳輸的內容。  
  
 由於訊息記錄輸出與訊息的傳輸格式沒有任何關係，因此訊息記錄會一律輸出解碼的訊息。 如果您已適當地設定訊息記錄，則任何記錄的訊息應為純文字。 例如，使用二進位訊息編碼器不會影響到記錄之訊息的格式 (純文字)。  
  
 XmlWriterTraceListener 的輸出是包含 XML 片段順序的檔案。 請注意該檔案不是有效的 XML 檔案。 建議您改用[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)檢視訊息記錄檔。 如需有關如何使用這項工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和疑難排解](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。  
  
 服務追蹤檢視器，訊息會列在**訊息** 索引標籤。導致處理錯誤或與處理錯誤相關的訊息，會視錯誤的嚴重性以黃色 (警告層級) 或紅色 (錯誤層級) 反白顯示。 在訊息上按兩下會在處理要求的內容中顯示訊息追蹤。  
  
> [!NOTE]
>  如果訊息沒有標頭，就不會記錄 `<header/>` 標記。  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>檢視用戶端、轉送與服務記錄的訊息  
 環境中可能會包含將訊息傳送給轉送的用戶端，之後再將訊息轉寄給服務。 當所有三個位置，已啟用訊息記錄和所有三個訊息的記錄檔中檢視[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時，將不正確地呈現訊息記錄交換。 這是因為訊息標頭中的 `CorrelationId` 和 `ActivityId`，對每個傳送接收組來說不是唯一的。  
  
 您可以使用下列其中一種方法解決這個問題。  
  
-   只能檢視中的三個訊息記錄檔的兩個[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)在任何時間。  
  
-   如果您必須檢視中的所有三個記錄[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時，您可以修改轉送服務來建立新<xref:System.ServiceModel.Channels.Message>執行個體。 這個執行個體應該是傳入訊息本文的複本，加上所有的標頭 (除了 `ActivityId` 和 `Action` 標頭以外)。 下列範例程式碼示範如何進行這項操作：  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>不正確之訊息記錄內容的例外情況  
 在下列情況中，記錄的訊息可能不是在網路上傳輸之八位元資料流的完整表示。  
  
-   針對 BasicHttpBinding，在 /addressing/none 命名空間中會記錄傳入訊息的封套標頭。  
  
-   空白可能不相符。  
  
-   針對傳入訊息，空白項目可以用不同方式表示。 例如，\<標記 >\</標記 > 而不是\<標記 / >  
  
-   當藉由預設或明確設定 enableLoggingKnownPii="true" 停用已知 PII 記錄時。  
  
-   啟用編碼以轉換至 UTF-8。  
  
## <a name="see-also"></a>另請參閱  
 [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)
