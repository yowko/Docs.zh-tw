---
title: 服務架構資料
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="service-framework-data"></a>服務架構資料
此主題會列出服務架構資料產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|指定命名空間中的指定項目無效。 這表示指定的項目是重複項目，或者不是合法的延伸，因為定址命名空間中不能有延伸項目。|  
|BinaryEncoderSessionInvalid|二進位編碼器工作階段無效，因為解碼先前的訊息時發生錯誤。|  
|CannotDetectAddressingVersion|無法偵測 WS-Addressing 版本。 EndpointAddress 的開頭不是項目。|  
|CouldNotFindNamespaceForPrefix|範圍中指定的前置詞沒有命名空間繫結。|  
|EncoderBadContentType|無法處理 contentType。|  
|EncoderEnvelopeVersionMismatch|指定傳入訊息的封套版本與指定編碼器不相符。 請確定繫結設定的版本與預期之訊息的版本相同。|  
|EncoderMessageVersionMismatch|指定傳出訊息的訊息版本與指定編碼器不相符。 請確定繫結設定的版本與訊息的版本相同。|  
|ExtraContentIsPresentInFaultDetail|錯誤詳細資料項目中有其他可延伸標記語言內容。 只允許單一項目。|  
|FilterBadTableType|為篩選器建立的 IMessageFilterTable 不可為 MessageFilterTable 或衍生自 MessageFilterTable。|  
|FilterTableInvalidForLookup|MessageFilterTable 狀態損毀。 無法執行要求的搜尋。|  
|MandatoryHeaderNotUnderstood|無法辨識一或多個必要的簡易物件存取通訊協定標題區塊。|  
|MessageBodyIsStream|訊息本文是資料流。|  
|MessageBodyIsUnknown|訊息本文格式不明。|  
|MessageBodyReaderInvalidReadState|無法取用訊息本文讀取裝置的指定 ReadState。|  
|MessageTextEncodingNotSupported|不支援文字訊息格式中使用的指定文字編碼。|  
|MissingMessageID|要求訊息缺少 MessageID 標頭。 必須有 MessageID 標頭才能與回覆相互關聯。|  
|MultipleMessageHeaders|找到一個以上使用指定名稱與命名空間的標頭。|  
|MultipleMessageHeadersWithActor|找到一個以上使用指定名稱、命名空間與角色的標頭。|  
|MultipleRelatesToHeaders|找到一個以上使用指定關係的 RelatesTo 標頭。 每個關係只允許一個此類標頭。|  
|QueryFunctionTypeNotSupported|不支援 IXsltContextFunction 的指定傳回型別。|  
|QueryIteratorOutOfScope|XPathNodeIterator 已失效。 以引數形式傳送至 IXsltContextFunction 的 XPathNodeIterator，只有在函式內才有效。 無法將它們快取供後續使用或是由函式傳回。|  
|QueryVariableNull|IXsltContextVariable 方法不得傳回 null。|  
|QueryVariableTypeNotSupported|不支援指定的 IXsltContextVariable 衍生型別。|  
|ReceiveShutdownReturnedMessage|通道在關閉時，收到指定「動作」的未預期輸入訊息。 只有在不想收到任何其他輸入訊息時，才關閉通道。|  
|XmlBufferInInvalidState|發生內部錯誤。 因為 XML 緩衝區的狀態，所以無法執行作業。|  
|XmlBufferQuotaExceeded|用來緩衝可延伸標記語言內容的所需大小已超過緩衝區配額。|
