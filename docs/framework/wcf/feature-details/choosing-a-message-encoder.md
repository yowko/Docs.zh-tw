---
title: 選擇訊息編碼器
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: a306896af7a73d43956638981908c12d86126a9f
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345247"
---
# <a name="choosing-a-message-encoder"></a>選擇訊息編碼器
本主題討論在 Windows 通信基礎 （WCF） 中包含的消息編碼器中選擇的條件：二進位、文本和消息傳輸優化機制 （MTOM）。  
  
 在 WCF 中，您可以指定如何通過*綁定*在端點之間通過網路傳輸資料，繫結元素由一系列*繫結元素*組成。 訊息編碼器是由繫結堆疊中的訊息編碼繫結項目所表示。 繫結包含選擇性通訊協定繫結項目 (例如安全性繫結項目或可靠的訊息繫結項目)、必要的訊息編碼繫結項目和必要的傳輸繫結項目。  
  
 訊息編碼繫結項目位在選擇性通訊協定繫結項目之下，在必要的傳輸繫結項目之上。 在傳出端，訊息編碼器會序列化傳出的 <xref:System.ServiceModel.Channels.Message>，並會將它傳遞至傳輸。 在傳入端，訊息編碼器會從傳輸接收 <xref:System.ServiceModel.Channels.Message> 的序列化形式，並會將它傳遞至更高的通訊協定層 (如果有的話)，否則會傳遞至應用程式。  
  
 連接到已存在的用戶端或伺服器時，您可能沒有使用特定訊息編碼的選擇，因為您必須以另一端預期的方式，對訊息進行編碼。 但是，如果要編寫 WCF 服務，則可以通過多個終結點公開服務，每個終結點使用不同的消息編碼。 這會讓用戶端在對它們來說是最佳端點上，選擇最佳編碼方式來與服務交談，而且會提供用戶端彈性來選擇最佳編碼方式。 使用多個端點，也會將不同訊息編碼的好處與其他繫結程序項目結合。  
  
## <a name="system-provided-encoders"></a>系統提供的編碼器  
 WCF 包括三個消息編碼器，由以下三個類表示：  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 即文字訊息編碼器，支援純 XML 編碼方式和 SOAP 編碼方式。 文字訊息編碼器的純 XML 編碼模式稱為 "plain old XML" (POX)，與文字為主的 SOAP 編碼方式有所區別。 若要啟用 POX，請將 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> 屬性設定為 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。 使用文本消息編碼器與非 WCF 終結點交互操作。  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>，二進位消息編碼器，使用緊湊的二進位格式，並針對 WCF 到 WCF 通信進行了優化，因此不可交互操作。 這也是 WCF 提供的所有編碼器中性能最大的編碼器。  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 即繫結項目，會指定以 MTOM 編碼訊息的字元編碼和訊息版本處理。 MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。 MTOM 編碼器會嘗試在效率和互通性之間建立平衡。 MTOM 編碼方式會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成文字)，好讓這些資料最佳化。 在效率方面，在 WCF 提供的編碼器中，MTOM 是文本（最慢）和二進位（速度最快的）之間的中間。  
  
## <a name="how-to-choose-a-message-encoder"></a>如何選擇訊息編碼器  
 下表說明選擇訊息編碼器時的通用因素。 將對您應用程式最重要的因素設定優先權，然後選擇最適合這些因素的訊息編碼器。 請務必考慮表格中所未列出的任何其他因素，以及應用程式可能需要的任何自訂訊息編碼器。  
  
|因數|描述|支援這個因素的編碼器|  
|------------|-----------------|---------------------------------------|  
|支援的字元集。|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>並<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>僅支援 UTF8 和 UTF16 Unicode（*大末點*和小*端*代碼）編碼。 如果不需要如 UTF7 或 ASCII 等其他編碼，則必須使用自訂編碼器。 有關示例自訂編碼器，請參閱[自訂消息編碼器](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder)。|Text|  
|檢閱|檢查是傳輸期間檢查訊息的能力。 不論是否使用 SOAP，文字編碼都會讓許多應用程式檢查及分析訊息，而不需要使用特別工具。 請注意，在訊息或傳輸層級上，傳輸安全性的使用會影響檢查訊息的能力。 機密性會保護訊息不受檢查，而完整性則會保護訊息不受修改。|Text|  
|可靠性|可靠性是編碼器抵抗傳輸錯誤的能力。 此外，也可以在訊息、傳輸或應用程式層提供可靠性。 所有標準 WCF 編碼器都假定另一個層提供可靠性。 編碼器不太能從傳輸錯誤復原。|None|  
|簡單|簡單表示可輕鬆建立某個編碼規格的編碼器和解碼器。 文字編碼對簡單而言特別有利，而且 POX 文字編碼還有不需要支援來處理 SOAP 的額外好處。|文字 (POX)|  
|大小|編碼方式決定了內容所需的負荷量。 編碼訊息的大小與服務作業的最大輸送量直接相關。 二進位編碼通常比文字編碼更為精簡。 當訊息太大時，請考慮在編碼期間一併壓縮訊息內容。 不過，對於訊息傳送者和接收者，壓縮都會增加處理成本。|Binary|  
|串流|資料流可讓應用程式在整個訊息送達之前開始處理訊息。 有效使用資料流，會要求訊息開頭便提供訊息的重要資料，因此接收的應用程式不需要等待訊息送達。 而且，使用資料流處理傳輸的應用程式必須累加組織訊息中的資料，因此內容沒有轉接相依性。 在許多情況下，您必須在資料流內容和擁有內容的最小傳輸大小之間妥協。|None|  
|協力廠商工具支援|編碼方式的支援區域包含開發和診斷。 協力廠商開發人員已經在處理 POX 格式編碼訊息的程式庫和工具組投入大量投資。|文字 (POX)|  
|互通性|此因素是指 WCF 編碼器與非 WCF 服務交互操作的能力。|Text<br /><br /> MTOM (部分)|  
  
注意：使用二進位編碼器時，在建立 XMLReader 期間使用 IgnoreWhitespace 設定將會沒有作用。  例如，如果您在服務作業中執行下列動作：  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
IgnoreWhitespace 設定會遭到忽略。  
  
## <a name="compression-and-the-binary-encoder"></a>壓縮和二進位編碼器

從 WCF 4.5 開始，WCF 二進位編碼器加入壓縮的支援。 這可讓您使用 gzip/Deflate 演算法從 WCF 用戶端傳送壓縮的訊息，同時也從自我裝載的 WCF 服務以壓縮的訊息來回應。 這項功能會在 HTTP 和 TCP 傳輸上啟用壓縮。 藉由設定 IIS 主機伺服器，IIS 所裝載的 WCF 服務就可以永遠啟用傳送壓縮回應。 壓縮型別是透過 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> 屬性來設定。 這個屬性會設定為其中一個 <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> 列舉值︰

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
由於此屬性僅在二進位消息編碼繫結元素上公開，因此您需要創建如下所示的自訂綁定才能使用此功能：

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

用戶端和服務都需要同意發送和接收壓縮消息，因此必須在用戶端和服務上的二進位MessageEncode 元素上配置 compressFormat 屬性。 如果服務或用戶端未設定使用壓縮，但另一方已設定，則會擲回 ProtocolException。啟用壓縮應仔細考慮。 如果網路頻寬形成瓶頸，壓縮多半是有用的。 在 CPU 成為瓶頸所在的情況下，壓縮會減少輸送量。 必須在模擬環境中進行適當測試，以確認這項功能對應用程式有益。  
  
## <a name="see-also"></a>另請參閱

- [綁定](../../../../docs/framework/wcf/feature-details/bindings.md)
