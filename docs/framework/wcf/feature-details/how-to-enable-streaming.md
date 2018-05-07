---
title: HOW TO：啟用資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: b28764c4bad88511096ab09fd71cc2a73c735096
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-streaming"></a>HOW TO：啟用資料流
Windows Communication Foundation (WCF) 可以傳送使用緩衝或資料流傳輸的訊息。 在預設的緩衝傳輸模式中，必須完整傳遞訊息，接收者才能讀取。 在資料流傳輸模式中，接收者不需等到訊息完全送達，就可以開始處理訊息。 當資訊的傳遞很漫長，但是可依序列處理時，使用資料流模式將十分有幫助。 當訊息太龐大而無法完整加以緩衝時，資料流模式也很有用處。  
  
 若要啟用資料流處理，請適當定義 `OperationContract` 並在傳輸層級啟用資料流處理。  
  
### <a name="to-stream-data"></a>若要以資料流方式處理資料  
  
1.  若要以資料流方式處理資料，服務的 `OperationContract` 必須滿足兩項需求：  
  
    1.  用來存放要進行資料流處理之資料的參數，必須是方法中的唯一參數。 例如，如果輸入訊息是要處理成資料流的訊息，這項處理作業就必須剛好只有一個輸入參數。 同樣地，如果要將輸出訊息處理成資料流，這項作業也必須剛好只有一個輸出參數或傳回值。  
  
    2.  至少有一個參數型別與傳回值必須是 <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message> 或 <xref:System.Xml.Serialization.IXmlSerializable>。  
  
     下列為資料流處理資料合約的範例。  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` 作業會接收一些緩衝處理的輸入資料做為 `string` (會經過緩衝處理，並傳回已經過資料流處理的 `Stream`)。 相反地，`UploadStream` 會接受 `Stream` (經過資料流處理) 並傳回 `bool` (經過緩衝處理)。 `EchoStream` 會接受並傳回 `Stream`，而這項作業也是對輸入和輸出兩種訊息都進行資料流處理的範例。 最後，`GetReversedStream` 不接受任何輸入，而只是傳回 `Stream` (經過資料流處理)。  
  
2.  繫結必須啟用資料流處理。 您可以設定 `TransferMode` 屬性，並採用下列其中一個值：  
  
    1.  `Buffered`,  
  
    2.  `Streamed`，可啟用雙向資料流通訊。  
  
    3.  `StreamedRequest`，只會啟用要求的資料流處理。  
  
    4.  `StreamedResponse`，只會啟用回應的資料流處理。  
  
     `BasicHttpBinding` 會公開繫結上的 `TransferMode` 屬性，就像 `NetTcpBinding` 和 `NetNamedPipeBinding` 一樣。 `TransferMode` 屬性也可以在傳輸繫結項目上設定，並用於自訂繫結。  
  
     下列範例說明如何透過程式碼與藉由變更組態檔來設定 `TransferMode`。 這些範例同時都會將 `maxReceivedMessageSize` 屬性設為 64 MB，以限制允許接收的最大訊息大小。 預設的 `maxReceivedMessageSize` 是 64 KB，但這對資料流案例來說，通常是過低的。 適當的配額設定取決於您的應用程式預期接收的最大訊息大小。 同時請注意，`maxBufferSize` 會控制緩衝處理的最大大小，請適當設定。  
  
    1.  範例中的下列組態片段示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理。  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  下列程式碼片段示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理。  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  下列程式碼片段示範將 `TransferMode` 屬性設定為會在自訂 TCP 繫結上進行資料流處理。  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  `GetStream`、`UploadStream` 和 `EchoStream` 都會處理直接從檔案傳送資料或直接將接收的資料儲存至檔案的作業。 下列為 `GetStream` 程式碼。  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>撰寫自訂資料流  
  
1.  若要對每個正在傳送或接收的資料流區塊 (Chunk) 進行特殊處理，請從 <xref:System.IO.Stream> 衍生自訂資料流類別。 下列程式碼包含 `GetReversedStream` 方法和 `ReverseStream` 類別，是一個自訂資料流範例。  
  
     `GetReversedStream` 會建立並傳回 `ReverseStream` 的新執行個體。 實際的處理會在系統從這個 `ReverseStream` 物件讀取時進行。 `ReverseStream.Read` 方法會從基礎檔案讀取位元組區塊，然後將其序列反轉，再傳回此相反序列的位元組。 此方法不會反轉整個檔案內容，它只是一次反轉一個位元組區塊。 下列範例說明如何在對資料流讀取內容或寫入內容時執行資料流處理。  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [大型資料和資料流](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [資料流](../../../../docs/framework/wcf/samples/stream.md)
