---
title: "使用 Message 類別"
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
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 999b0105bf6ab97eb3ab38423efbc31f9b322254
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-message-class"></a>使用 Message 類別
<xref:System.ServiceModel.Channels.Message> 類別對 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 來說十分重要。 用戶端和服務之間的通訊，最終結果都是要傳送和接收 <xref:System.ServiceModel.Channels.Message> 執行個體。  
  
 您通常不會直接和 <xref:System.ServiceModel.Channels.Message> 類別進行互動。 而是會使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務模型建構 (例如資料合約、訊息合約和作業合約) 來描述傳入和傳出訊息。 不過，在某些進階案例中，您可以直接使用 <xref:System.ServiceModel.Channels.Message> 類別來設計程式。 例如，您可能想要使用 <xref:System.ServiceModel.Channels.Message> 類別：  
  
-   當您需要其他建立傳出訊息內容的方法 (例如，直接從磁碟上的檔案建立訊息)，而非序列化 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件時。  
  
-   當您需要其他使用傳入訊息內容的方法 (例如，要將 XSLT 轉換套用至未經處理的 XML 內容)，而非還原序列化至 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件。  
  
-   當您需要以一般方法處理訊息，而不管訊息內容時 (例如，當建置路由器、負載平衡器或發行/訂閱系統遞送或轉寄訊息時)。  
  
 使用之前<xref:System.ServiceModel.Channels.Message>類別中，熟悉[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]資料傳輸架構[資料傳輸架構概觀](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)。  
  
 <xref:System.ServiceModel.Channels.Message> 是資料的一般用途容器，但是其設計則緊密遵循 SOAP 通訊協定中的訊息設計。 就和在 SOAP 中一樣，訊息同時具有訊息本文和標頭。 訊息本文中包含實際的承載資料，而標頭則包含其他具名的資料容器。 讀取及撰寫本文和標頭的規則不太一樣，例如，標頭一定會在記憶體中緩衝處理並且可不限次數以任何順序存取，而本文可能只讀取一次，並可能進行資料流處理。 一般來說，使用 SOAP 時，訊息本文會對映至 SOAP 本文，而訊息標頭則對映至 SOAP 標頭。  
  
## <a name="using-the-message-class-in-operations"></a>在作業中使用 Message 類別  
 您可以使用 <xref:System.ServiceModel.Channels.Message> 類別做為作業的輸入參數、作業的傳回值或同時使用以上兩者。 如果在作業的任意處使用 <xref:System.ServiceModel.Channels.Message>，則會套用下列限制：  
  
-   作業不可具有任何 `out` 或 `ref` 參數。  
  
-   不可有一個以上的 `input` 參數。 如果出現參數，這個參數必須為 Message 或是訊息合約類型。  
  
-   傳回類型必須為 `void`、`Message` 或訊息合約類型。  
  
 下列程式碼範例包含了有效的作業合約。  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>建立基本訊息  
 <xref:System.ServiceModel.Channels.Message> 類別會提供可用來建立基本訊息的靜態 `CreateMessage` 處理站方法。  
  
 所有 `CreateMessage` 多載都會採用型別為 <xref:System.ServiceModel.Channels.MessageVersion> 的版本參數，這表示要用於訊息的 SOAP 和 WS-Addressing 版本。 如果您要使用與傳入訊息相同的通訊協定版本，則可以使用 <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> 執行個體上從 <xref:System.ServiceModel.OperationContext> 屬性取得的 <xref:System.ServiceModel.OperationContext.Current%2A> 屬性。 大多數 `CreateMessage` 多載也會有字串參數，可指出要用於訊息的 SOAP 動作。 您可以將版本設定為 `None`，即可停用 SOAP 封套產生作業；這則訊息只會包含本文。  
  
## <a name="creating-messages-from-objects"></a>從物件建立訊息  
 僅採用一個版本和動作、最基本的 `CreateMessage` 多載，會建立帶有空本文的訊息。 其他多載則會採用額外的 <xref:System.Object> 參數；這樣會建立本文是所提供之物件的序列化表示之訊息。 使用 <xref:System.Runtime.Serialization.DataContractSerializer> 的預設值來進行序列化。 如果您要使用不同的序列化程式，或者要以不同的方式設定 `DataContractSerializer`，請使用也會採用 `CreateMessage` 參數的 `XmlObjectSerializer` 多載。  
  
 例如，若要傳回訊息中的物件，您可以使用下列程式碼。  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>從 XML 讀取器建立訊息  
 `CreateMessage` 多載會對本文採用 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlDictionaryReader>，而不是採用物件。 在這個情況下，訊息的本文會包含讀取自所傳遞 XML 讀取器時所產生的 XML。 例如，下列程式碼傳回的訊息，其本文內容便是從 XML 檔案讀取而來。  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 此外，有一些 `CreateMessage` 多載會採用 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlDictionaryReader>，用以表示整個訊息而不單單是本文而已。 這些多載也會採用整數 `maxSizeOfHeaders` 參數。 只要一建立訊息時，標頭一定會在記憶體中進行緩衝處理，而這個參數會限制所進行的緩衝數量。 如果 XML 是來自不受信任的來源，則將此參數設定為安全的值以降低阻絕服務攻擊的可能性則相當重要。 XML 讀取器所表示之訊息的 SOAP 和 WS-Addressing 版本必須符合使用版本參數所指出的版本。  
  
## <a name="creating-messages-with-bodywriter"></a>使用 BodyWriter 建立訊息  
 一個 `CreateMessage` 多載會採用 `BodyWriter` 執行個體以描述訊息的本文。 `BodyWriter` 是一種抽象類別 (Abstract Class)，衍生之後可以自訂建立訊息本文的方式。 您也可以建立自己的 `BodyWriter` 衍生類別 (Derived Class)，以自訂的方式描述訊息本文。 您必須覆寫會採用 `BodyWriter.OnWriteBodyContents` 的 <xref:System.Xml.XmlDictionaryWriter> 方法，這個方法會負責寫出本文。  
  
 本文寫入器可以經過緩衝處理或非緩衝處理 (資料流處理)。 緩衝處理的本文寫入器可不限次數寫出其內容，而資料流處理的本文寫入器只能寫出內容一次。 `IsBuffered` 屬性會指出本文寫入器是否有經過緩衝處理。 您可以呼叫受保護的 `BodyWriter` 建構函式 (Constructor) 來為本文寫入器設定此屬性，而此建構函式會採用 `isBuffered` 布林 (Boolean) 參數。 本文寫入器支援從非緩衝處理的本文寫入器建立緩衝處理的本文寫入器。 您可以覆寫 `OnCreateBufferedCopy` 方法以自訂這個程序。 根據預設，將會使用包含 `OnWriteBodyContents` 所傳回之 XML 的記憶體中緩衝區。 `OnCreateBufferedCopy` 則會採用 `maxBufferSize` 整數參數，如果您覆寫這個方法，就不得建立大於此大小上限的緩衝區。  
  
 `BodyWriter` 類別會提供 `WriteBodyContents` 和 `CreateBufferedCopy` 方法，而這些方法分別是圍繞在 `OnWriteBodyContents` 和 `OnCreateBufferedCopy` 方法的精簡型包裝函式。 這些方法會執行狀態檢查，以確定沒有多次存取非緩衝處理的本文寫入器。 只有在建立以 `Message` 為基礎的自訂 `BodyWriters` 衍生類別時，才會直接呼叫這些方法。  
  
## <a name="creating-fault-messages"></a>建立錯誤訊息  
 您可以使用特定 `CreateMessage` 多載來建立 SOAP 錯誤訊息。 其中最基本的錯誤訊息會採用描述該錯誤的 <xref:System.ServiceModel.Channels.MessageFault> 物件。 也會針對便利性而提供其他多載。 第一個這樣的多載會採用 `FaultCode` 和原因字串，並透過會使用此資訊的 `MessageFault` 來建立 `MessageFault.CreateFault`。 其他多載則會採用詳細資訊物件，並將該物件、錯誤碼和原因一起傳遞至 `CreateFault`。 例如，下列作業會傳回錯誤。  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>擷取訊息本文資料  
 `Message` 類別支援多種方法，可從其本文擷取資訊。 這些方法則分類為下列類別：  
  
-   取得一次寫出至 XML 寫入器的訊息本文。 這指*撰寫郵件*。  
  
-   取得訊息本文的 XML 讀取器。 這樣可讓您在之後有需要時，一點一點的存取訊息本文。 這指*讀取訊息*。  
  
-   整個訊息 (包含其本文) 都可複製至 <xref:System.ServiceModel.Channels.MessageBuffer> 型別的記憶體中緩衝區。 這指*將訊息複製*。  
  
 不管您使用何種方式存取本文，都只能存取 `Message` 本文一次。 訊息物件中帶有 `State` 屬性，這個屬性一開始會設定為「已建立」。 先前的清單中所描述的三個存取方法，會分別將狀態設定為「已寫入」、「已讀取」和「已複製」。 此外，`Close` 方法可以在不再需要訊息本文內容時，將狀態設定為「已關閉」。 您只能在「已建立」狀態中存取訊息本文，而在變更狀態之後，就無法再回到「已建立」狀態。  
  
## <a name="writing-messages"></a>寫入訊息  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> 方法會將所提供的 `Message` 執行個體的本文內容寫出至所提供的 XML 寫入器。 <xref:System.ServiceModel.Channels.Message.WriteBody%2A> 方法會執行相同的動作，差別在於它是將本文內容放在適當的包裝函式項目中 (例如，<`soap:body`>)。 最後，<xref:System.ServiceModel.Channels.Message.WriteMessage%2A> 會寫出整個訊息，包括包裝的 SOAP 封套和標頭。 如果關閉 SOAP (版本為 `MessageVersion.None`)，這三個方法都會執行相同的動作：寫出訊息本文內容。  
  
 例如，下列程式碼會將傳入訊息的本文寫出至檔案。  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 有兩個額外的 Helper 方法會寫出特定 SOAP 開始項目標記。 這些方法不會存取訊息本文，因此不會變更訊息狀態。 這些活動包括：  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> 會寫入開始本文項目，例如 `<soap:Body>`。  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> 會寫入開始封套項目，例如 `<soap:Envelope>`。  
  
 若要寫入對應的結束項目標記，請在對應的 XML 寫入器上呼叫 `WriteEndElement`。 這些方法很少被直接呼叫。  
  
## <a name="reading-messages"></a>讀取訊息  
 讀取訊息本文的主要方法為呼叫 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>。 您會回到可用來讀取訊息本文的 <xref:System.Xml.XmlDictionaryReader>。 請注意，只要一呼叫 <xref:System.ServiceModel.Channels.Message>，<xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 就會轉換至「已讀取」狀態，而不是在您使用傳回的 XML 讀取器時轉換。  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> 方法也可讓您以具有型別的物件存取訊息本文。 這個方法會在內部使用 `GetReaderAtBodyContents`，因此也會將訊息狀態轉換至 <xref:System.ServiceModel.Channels.MessageState.Read> 狀態 (請參閱 <xref:System.ServiceModel.Channels.Message.State%2A> 屬性)。  
  
 最佳作法是檢查 <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> 屬性，在此情況下訊息本文為空，而且 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 會擲回 <xref:System.InvalidOperationException>。 因此，如果這是接收的訊息 (例如，回覆)，您可能也要檢查指出訊息中是否包含錯誤的 <xref:System.ServiceModel.Channels.Message.IsFault%2A>。  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> 最基本的多載會使用以預設值設定，且已停用 <xref:System.Runtime.Serialization.DataContractSerializer> 配額的 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A>，將訊息本文還原序列化至型別的執行個體 (由泛型參數所指定)。 如果您要使用不同的序列化引擎，或者以非預設的方法設定 `DataContractSerializer`，請使用會採用 <xref:System.ServiceModel.Channels.Message.GetBody%2A> 的 <xref:System.Runtime.Serialization.XmlObjectSerializer> 多載。  
  
 例如，下列程式碼會從含有序列化 `Person` 物件的訊息本文中擷取資料，並列印出人員的名稱。  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>將訊息複製至緩衝區  
 有時候您需要多次存取訊息本文，例如，要將相同訊息轉寄給屬於發行者/訂閱者系統一部分之多個目的端時。 在此情況下，需要在記憶體中緩衝處理整個訊息 (包括本文)。 藉由呼叫 <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29> 即可達到此目的。 這個方法會採用表示緩衝區大小上限的整數參數，而且建立不會超過此大小的緩衝區。 如果訊息是來自不受信任的來源，則將此項設為安全的值就顯得相當重要。  
  
 緩衝區會當做 <xref:System.ServiceModel.Channels.MessageBuffer> 執行個體傳回。 有數種方法可讓您存取緩衝區中的資料。 主要的方法為呼叫 <xref:System.ServiceModel.Channels.Message.CreateMessage%2A>，以從緩衝區中建立 `Message` 執行個體。  
  
 另一個存取緩衝區資料的方法為實作 <xref:System.Xml.XPath.IXPathNavigable> 介面，而 <xref:System.ServiceModel.Channels.MessageBuffer> 類別會實作這個介面以直接存取基礎 XML。 有些 <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> 多載可讓您建立節點配額所保護的 <xref:System.Xml.XPath> 導覽，進而限制可造訪的 XML 節點數。 這樣做可防止長處理時間所導致的阻絕服務攻擊。 預設會停用此配額。 有些 `CreateNavigator` 多載會讓您使用 <xref:System.Xml.XmlSpace> 列舉搭配預設值 `XmlSpace.None`，以指定在 XML 中處理空白字元的方式。  
  
 最後一個存取訊息緩衝區內容的方法為使用 <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> 將內容寫出至資料流。  
  
 下列範例會示範使用 `MessageBuffer` 的處理序：傳入訊息會轉寄至多個收件者，然後記錄至檔案。 沒有緩衝處理的話，則不可能這樣做，這樣的話只能存取一次訊息本文。  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` 類別則具有不重要的成員。 不再需要緩衝區內容時，可以呼叫 <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> 方法釋放資源。 <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> 屬性會傳回所配置緩衝區的大小。 <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> 屬性則會傳回訊息的 MIME 內容型別。  
  
## <a name="accessing-the-message-body-for-debugging"></a>存取訊息本文以進行偵錯  
 為了進行偵錯，您可以呼叫 <xref:System.ServiceModel.Channels.Message.ToString%2A> 方法而取得以訊息做為字串的表示。 這個表示通常會符合訊息在網路上的呈現方式 (若此訊息是以文字編碼器編碼)，差別在於 XML 會針對人們可讀取性達成更佳的格式化效果。 此項的例外為訊息本文。 本文只能讀取一次，而且 `ToString` 不會變更訊息狀態。 因此，`ToString`方法可能無法存取本文，並可能替代預留位置 （例如，"…"或三個點） 而非訊息本文。 所以，如果訊息的本文內容十分重要，請勿使用 `ToString` 來記錄訊息。  
  
## <a name="accessing-other-message-parts"></a>存取其他訊息部分  
 將會提供各種屬性以存取訊息 (而非其本文內容) 的相關資訊。 不過，一旦關閉訊息就無法呼叫這些屬性：  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> 屬性表示訊息標頭。 請參閱這個主題稍後的 「 使用標頭 」 一節。  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> 屬性表示訊息屬性，這些訊息屬性為附加至訊息 (傳送訊息時通常不會發出的訊息) 的具名資料片段。 請參閱本主題稍後的「使用屬性」這一節。  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> 屬性會指出與訊息相關聯的 SOAP 和 WS-Addressing 版本，而若停用 SOAP，則指出 `None`。  
  
-   如果訊息為 SOAP 錯誤訊息，<xref:System.ServiceModel.Channels.Message.IsFault%2A> 屬性會傳回 `true`。  
  
-   如果訊息為空，則 <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> 屬性會傳回 `true`。  
  
 您可以使用 <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> 方法，存取以特定名稱和命名空間所識別之本文包裝函式項目 (例如，`<soap:Body>`) 上的特定屬性。 如果找不到這類屬性，則會傳回 `null`。 只有當 `Message` 處於「已建立」狀態時 (訊息本文尚未被存取)，才能呼叫這個方法。  
  
## <a name="working-with-headers"></a>使用標頭  
 A`Message`可以包含任何數目的具名 XML 片段，稱為*標頭*。 每個片段通常都會對映至 SOAP 標頭。 您可以透過型別為 `Headers` 的 <xref:System.ServiceModel.Channels.MessageHeaders> 屬性來存取標頭。 <xref:System.ServiceModel.Channels.MessageHeaders> 是 <xref:System.ServiceModel.Channels.MessageHeaderInfo> 物件的集合，而您可以藉由標頭的 <xref:System.Collections.IEnumerable> 介面或索引子 (Indexer) 來存取個別標頭。 例如，下列程式碼會列出 `Message` 中所有標頭的名稱。  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>新增、移除、尋找標頭  
 您可以使用 <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> 方法，將新標頭新增至所有現有標頭的尾端。 您也可以使用 <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> 方法在特定索引中插入標頭。 現有的標頭會因插入的項目而移位。 將會根據標頭的索引排列標頭的順序，而第一個可用的索引為 0。 您可以使用各種 <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> 方法多載，從不同的 `Message` 或 `MessageHeaders` 執行個體中加入標頭。 有些多載會複製一則個別標頭，而其他多載則複製所有標頭。 <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> 方法會移除所有標頭。 <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> 方法則會移除特定索引的標頭 (該標頭之後的所有標頭都會移位)。 <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> 方法會移除具有特定名稱和命名空間的所有標頭。  
  
 您可使用 <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> 方法擷取特定標頭。 這個方法會採用要尋找的標頭名稱和命名空間，並傳回其索引。 如果標頭在多個地方出現，則會擲出例外狀況。 如果找不到標頭，則會傳回 -1。  
  
 在 SOAP 標頭模型中，標頭所擁有的 `Actor` 值會指定標頭的預定收件者。 最基本的 `FindHeader` 多載只會搜尋用於訊息最終接收者的標頭。 不過，其他多載則可讓您指定搜尋中所含的 `Actor` 值。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] SOAP 規格。  
  
 將會提供 <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> 方法以將標頭從 <xref:System.ServiceModel.Channels.MessageHeaders> 集合複製至 <xref:System.ServiceModel.Channels.MessageHeaderInfo> 物件的陣列。  
  
 若要存取標頭中的 XML 資料，您可以對特定標頭索引呼叫 <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> 並傳回 XML 讀取器。 如果您要將標頭內容還原序列化至物件，請使用 <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> 或其他多載。 最基本的多載會使用以預設方法設定的 <xref:System.Runtime.Serialization.DataContractSerializer> 來還原序列化標頭。 如果您要使用不同的序列化程式或不同的 `DataContractSerializer` 組態，請使用下列其中一個會採用 `XmlObjectSerializer` 的多載。 也會有採用標頭名稱、命名空間和選擇性採用 `Actor` 值清單，而不採用索引的多載；而這是 `FindHeader` 和 `GetHeader` 的組合。  
  
## <a name="working-with-properties"></a>使用屬性  
 `Message` 執行個體中可包含任意數目、任意型別的具名物件。 您可以透過型別為 `Properties` 的 `MessageProperties` 屬性來存取這個集合。 這個集合會實作 <xref:System.Collections.Generic.IDictionary%602> 介面，並且會做為從 <xref:System.String> 到 <xref:System.Object> 的對應。 一般來說，屬性值不會直接對應至 Wire 上的訊息任何部分，而是會對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道堆疊中的各種通道或 <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> 服務架構提供各種訊息處理提示。 如需範例，請參閱[資料傳輸架構概觀](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)。  
  
## <a name="inheriting-from-the-message-class"></a>繼承自 Message 類別  
 如果使用 `CreateMessage` 建立的內建訊息類型不符合您的需求，請建立衍生自 `Message` 類別的類別。  
  
### <a name="defining-the-message-body-contents"></a>定義訊息本文內容  
 有三種主要技術可讓您在訊息本文內存取資料：寫入、讀取以及將資料複製至緩衝區。 這些作業最後會導致在 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> 的衍生類別上，分別呼叫 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>、<xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> 和 `Message` 方法。 基底 `Message` 類別可保證，針對每個 `Message` 執行個體只會呼叫其中一個方法，而且該方法不會呼叫超過一次。 基底類別也會確保不會在關閉的訊息上呼叫方法。 因此在您的實作中不需要追蹤訊息狀態。  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> 是一種抽象方法，而且必須進行實作。 定義訊息之本文內容最基本的方法為使用這個方法來寫入。 例如，下列訊息包含 100,000 個 1 到 20 的亂數。  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 `OnGetReaderAtBodyContents` 和 `OnCreateBufferedCopy` 方法都具有可用於大多數情況的預設實作。 預設實作會呼叫 `OnWriteBodyContents`，然後緩衝處理結果，再使用產生的緩衝區。 不過，在某些情況下，只有此實作可能不太夠。 在先前的範例中，讀取訊息會造成緩衝處理 100,000 個 XML 項目，而這可能不是想要的目的。 您可能想要覆寫 `OnGetReaderAtBodyContents`，以傳回提供亂數的自訂 `XmlDictionaryReader` 衍生類別。 您接著可以覆寫 `OnWriteBodyContents` 以使用 `OnGetReaderAtBodyContents` 正確傳回的讀取器，如下列範例所示。  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 同樣地，您可能想要覆寫 `OnCreateBufferedCopy` 以傳回自己的 `MessageBuffer` 衍生類別。  
  
 除了提供訊息本文內容以外，您的訊息衍生類別也必須覆寫 `Version`、`Headers` 和 `Properties` 屬性。  
  
 請注意，如果建立訊息複本，該複本會使用原始的訊息標頭。  
  
### <a name="other-members-that-can-be-overridden"></a>可以覆寫的其他成員  
 您可以覆寫 <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>、<xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> 和 <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> 方法，以指定寫出 SOAP 信封、SOAP 標頭和 SOAP 本文項目開始標記的方法。這些方法通常會對應至 `<soap:Envelope>`、`<soap:Header>` 和 `<soap:Body>`。 如果 `Version` 正確地傳回 `MessageVersion.None`，則這些方法一般不應該寫出任何項目。  
  
> [!NOTE]
>  `OnGetReaderAtBodyContents` 預設實作會在呼叫 `OnWriteStartEnvelope` 和緩衝處理結果之前，先呼叫 `OnWriteStartBody` 和 `OnWriteBodyContents`。 如此將不會寫出標頭。  
  
 覆寫 <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> 方法，以變更從各種訊息片段建構整個訊息的方法。 將會從 `OnWriteMessage` 和預設 <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> 實作中呼叫 <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> 方法。 請注意，覆寫 <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> 不是最佳作法。 最好是覆寫適當的 `On` 方法 (例如，<xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>、<xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> 和 <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>)。  
  
 覆寫 <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> 以覆寫偵錯期間呈現訊息本文的方法。 預設是以三個點 ("…") 來表示。 請注意，當訊息狀態為「已關閉」以外的狀態時，就可以多次呼叫這個方法。 實作這個方法後，絕不能造成任何動作只能執行一次 (例如，從順向資料流讀取)。  
  
 覆寫 <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> 方法以允許存取 SOAP 本文項目上的屬性。 這個方法可以無限次數呼叫，但 `Message` 基底類別會保證只有當訊息處於「已建立」狀態時才會呼叫此方法。 您不需要檢查實作中的狀態。 預設實作一定會傳回 `null`，表示在本文項目上沒有任何屬性。  
  
 如果不再需要訊息本文，同時 `Message` 物件必須執行特殊清除動作，這時您可以覆寫 <xref:System.ServiceModel.Channels.Message.OnClose%2A>。 預設實作不做任何動作。  
  
 您可以覆寫 `IsEmpty` 和 `IsFault` 屬性。 根據預設，這兩個屬性都會傳回 `false`。
