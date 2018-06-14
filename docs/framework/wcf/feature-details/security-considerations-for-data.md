---
title: 資料的安全性考量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 077d6b3527119f00ecec3014778fecf0dd1a4bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509071"
---
# <a name="security-considerations-for-data"></a>資料的安全性考量
處理資料時 Windows Communication Foundation (WCF) 中，您必須考慮一些威脅類別。 下表列出與資料處理有關的最重要威脅類別。 WCF 會提供可減輕這些威脅的工具。  
  
 阻絕服務  
 當收到不受信任的資料時，這些資料可能會因漫長的計算而造成接收端存取不當比例的各種資源量，例如記憶體、執行緒、可用連線或處理器循環。 針對伺服器的阻絕服務攻擊可能會造成伺服器當機，或無法處理來自其他合法用戶端的訊息。  
  
 惡意程式碼執行  
 傳入的不受信任資料造成接收端執行原本不想執行的程式碼。  
  
 資訊洩漏  
 遠端攻擊者強制接收端回應其要求，造成洩露比原本要提供的更多資訊。  
  
## <a name="user-provided-code-and-code-access-security"></a>使用者提供的程式碼和程式碼存取安全性  
 某個執行由使用者所提供的程式碼的 Windows Communication Foundation (WCF) 基礎結構中的小數位數。 例如， <xref:System.Runtime.Serialization.DataContractSerializer> 序列化引擎可能會呼叫使用者提供的屬性 `set` 存取子和 `get` 存取子。 WCF 通道基礎結構可能也會呼叫使用者提供的衍生類別<xref:System.ServiceModel.Channels.Message>類別。  
  
 程式碼作者有責任要確保沒有安全性弱點的存在。 例如，如果您以型別整數的資料成員屬性來建立資料合約類型，並在 `set` 存取子實作中根據屬性值來配置陣列，如果惡意訊息包含此資料成員的極大值，您便有可能會遭到阻絕服務攻擊。 一般來說，請避免以傳入資料為基礎所做的任何配置，或是使用者提供之程式碼中的漫長處理 (特別是如果小量的傳入資料可能會造成的漫長處理)。 當執行使用者提供之程式碼的安全性分析時，請確定同時考慮所有的失敗情況 (也就是擲回例外狀況的所有程式碼分支)。  
  
 使用者提供之程式碼的最終範例為您在各個作業之服務實作內的程式碼。 您服務實作的安全性是您的責任。 很容易就會不小心建立可能會造成阻絕服務弱點的不安全作業實作。 例如，採用字串並從名稱以該字串開頭的資料庫傳回客戶清單的作業。 如果您是使用大型資料庫，且傳遞的字串只是單一字母，您的程式碼可能會嘗試建立大於所有可用記憶體的訊息，而造成整個服務失敗 ( <xref:System.OutOfMemoryException> 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中是不可復原的，且一定會造成應用程式終止)。  
  
 您應該要確保各種擴充點中均未插入惡意程式碼。 這對於在部分信任下執行、從部分信任組件處理類型，或是建立無法由部分信任程式碼使用的元件時，特別有關係。 如需詳細資訊，請參閱本主題稍後的「部分信任威脅」。  
  
 請注意，在部分信任中執行時，資料合約序列化基礎結構只支援資料合約程式設計模型的有限子集 - 例如，使用不支援 <xref:System.SerializableAttribute> 屬性的私用資料成員或型別。 如需詳細資訊，請參閱[部分信任](../../../../docs/framework/wcf/feature-details/partial-trust.md)。  
  
## <a name="avoiding-unintentional-information-disclosure"></a>避免意外的資訊洩漏  
 當設計具有安全性的可序列化型別時，可能要考量資訊洩漏的問題。  
  
 請考慮下列各點：  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> 程式設計模型允許在序列化期間，在型別或組件以外公開私用和內部資料。 此外，型別的形式可能會在結構描述匯出期間公開。 請確定了解您型別的序列化規劃。 如果您不希望公開任何內容，請停用序列化 (例如，如果是資料合約，請不要套用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性)。  
  
-   請注意，相同型別可能會有多種序列化規劃，視使用中的序列化程式而定。 相同型別可能會在搭配 <xref:System.Runtime.Serialization.DataContractSerializer> 使用時公開一組資料，而在搭配 <xref:System.Xml.Serialization.XmlSerializer>使用時公開另一組資料。 意外使用錯誤的序列化程式可能會導致資訊洩漏。  
  
-   在舊版遠端程序呼叫 (RPC)/已編碼模式中使用 <xref:System.Xml.Serialization.XmlSerializer> ，可能會意外對接收端公開傳送端上物件圖形的形狀。  
  
## <a name="preventing-denial-of-service-attacks"></a>防止阻絕服務攻擊  
  
### <a name="quotas"></a>配額  
 造成接收端配置大量的記憶體是一種潛在的阻絕服務攻擊。 當此區段專注於由大型訊息所引起的記憶體消耗問題之時，可能會發生其他攻擊。 例如，訊息可能會使用不當比例的處理時間量。  
  
 通常是使用配額來降低阻絕服務攻擊。 當超過配額時，通常會擲回 <xref:System.ServiceModel.QuotaExceededException> 例外狀況。 如果沒有配額，惡意訊息可能會導致存取所有的可用記憶體，造成 <xref:System.OutOfMemoryException> 例外狀況，或存取所有的可用堆疊，造成 <xref:System.StackOverflowException>。  
  
 超過配額的情況是可復原的；如果是在執行中的服務中遇到，會捨棄目前正在處理的訊息，而服務會繼續執行並處理之後的訊息。 然而，記憶體不足和堆疊溢位狀況在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中任何地方都是不可復原的，如果遇到此類例外狀況，服務便會終止。  
  
 在 WCF 中的配額不會涉及任何的預先配置。 例如，如果 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> 配額 (在各種不同類別上) 設定為 128 KB，不表示會為各個訊息自動配置 128 KB。 實際的配置量要視實際的傳入訊息大小而定。  
  
 傳輸層有許多的配額。 這些是由使用中的特定傳輸通道 (HTTP、TCP 等等) 所強制執行的配額。 這些配額在 [Transport Quotas](../../../../docs/framework/wcf/feature-details/transport-quotas.md)中有詳細的說明，而本主題只討論其中一部分。  
  
### <a name="hashtable-vulnerability"></a>Hashtable 弱點  
 若資料合約包含 Hashtable 或集合，會有弱點。 如果大量的值插入 Hashtable，而其中大部分的值產生相同的雜湊值，就會發生問題。 這可以當做 DOS 攻擊使用。  可藉由設定 MaxRecievedMessageSize 繫結配額減少弱點。 為了防止此類攻擊而設定這種配額時，請務必小心。 此配額會對 WCF 訊息的大小設定上限。 此外，請避免在您的資料合約中使用 Hashtable 或集合。  
  
## <a name="limiting-memory-consumption-without-streaming"></a>不使用資料流來限制記憶體消耗  
 大型訊息的安全性模型要視是否正在使用資料流而定。 在基本、未經資料流處理的情況中，訊息會進入緩衝記憶體中。 在這種情況中，請在 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> 上或系統提供的繫結上使用 <xref:System.ServiceModel.Channels.TransportBindingElement> 配額，藉由限制存取的訊息大小上限來防止大型訊息。 請注意，服務可能會同時處理多個訊息，此時它們都將會在記憶體中。 請使用節流功能來降低這個威脅。  
  
 同時也請注意，雖然 `MaxReceivedMessageSize` 不會對每個訊息的記憶體消耗設定上限，但會限制在常數係數之內。 例如，如果 `MaxReceivedMessageSize` 是 1 MB，且收到 1-MB 的訊息後還原序列化，則會需要額外的記憶體來包含已還原序列化物件圖形，而造成總記憶體消耗超過 1 MB。 因此，請避免建立可序列化的型別，防止沒有太多傳入資料，卻造成大量的記憶體消耗。 例如，"M"與 50 個選擇性資料成員欄位和額外 100 私用欄位無法使用 XML 建構具現化的資料合約 」\<m / >"。 此 XML 會造成存取的記憶體用在 150 個欄位上。 請注意，根據預設，資料成員是選擇性的。 當此類型別是陣列的一部分時，問題是複合性的。  
  
 只有`MaxReceivedMessageSize` 不足以防止所有的阻絕服務攻擊。 例如，傳入的訊息可能會強制還原序列化程式要還原序列化深度巢狀的物件圖形 (包含的物件中還包含另一個物件的物件)。 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 都會以巢狀方式呼叫方法，以還原序列化此類圖形。 深度巢狀的方法呼叫可能會造成無法復原的 <xref:System.StackOverflowException>。 這項威脅可以藉由設定 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> 配額以限制 XML 巢狀的層級來降低，如同本主題中稍後的＜安全使用 XML＞一節中所述。  
  
 當使用二進位 XML 編碼時，將其他配額設定為 `MaxReceivedMessageSize` 特別重要。 使用二進位編碼與壓縮有些相同：傳入訊息中的一小群位元組可代表許多資料。 因此，即使訊息符合 `MaxReceivedMessageSize` 限制，仍可能以完整展開的形式佔用太多記憶體。 如果要降低此類 XML 特定的威脅，必須正確設定所有的 XML 讀取器配額，如同本主題中稍後的＜安全使用 XML＞一節中所述。  
  
## <a name="limiting-memory-consumption-with-streaming"></a>使用資料流來限制記憶體消耗  
 當進行資料流處理時，您可能會使用小的 `MaxReceivedMessageSize` 設定來防止阻絕服務攻擊。 然而，使用資料流可能會有更複雜的情況。 例如，檔案上載服務會接受大於所有可用記憶體的檔案。 在這種情況中，請將 `MaxReceivedMessageSize` 設定為極大值，如此應該幾乎不會有資料進入緩衝記憶體，且訊息會直接串流至磁碟。 如果要緩衝處理資料，而不是在此情況下，資料流處理的惡意訊息可以強制 WCF`MaxReceivedMessageSize`不再防止訊息存取所有可用的記憶體。  
  
 為降低此威脅，特定的配額設定存在於不同的 WCF 資料處理元件該限制緩衝處理。 其中最重要的是各種傳輸繫結項目和標準繫結上的 `MaxBufferSize` 屬性。 當進行資料流處理時，應在設定此配額時考慮您願意配置給每個訊息的最大記憶體量。 如同 `MaxReceivedMessageSize`，此設定不會設定記憶體消耗的絕對上限，而只會將其限制在常數係數之內。 同時，如同 `MaxReceivedMessageSize`，請注意同時處理多個訊息的可能性。  
  
### <a name="maxbuffersize-details"></a>MaxBufferSize 詳細資料  
 `MaxBufferSize`屬性會限制任何大量緩衝的 wcf。 例如，WCF 一定會緩衝處理 SOAP 標頭和 SOAP 錯誤，以及找到不依照自然讀取順序中的訊息傳輸最佳化機制 (MTOM) 訊息的 MIME 部分。 這個設定會限制上述所有情況中的緩衝處理量。  
  
 WCF 可完成此作業藉由傳遞`MaxBufferSize`可能會緩衝處理的各種元件的值。 例如， <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> 類別的一些 <xref:System.ServiceModel.Channels.Message> 多載會接受 `maxSizeOfHeaders` 參數。 WCF 會傳遞`MaxBufferSize`給這個參數，以限制 SOAP 標頭緩衝的量值。 當直接使用 <xref:System.ServiceModel.Channels.Message> 類別時，設定這個參數是很重要的。 一般情況下，當採用配額參數的 WCF 中使用的元件，務必了解這些參數的安全性含意並正確加以設定。  
  
 MTOM 訊息編碼器也有 `MaxBufferSize` 設定。 當使用標準繫結時，這會自動設定為傳輸層的 `MaxBufferSize` 值。 然而，如果使用 MTOM 訊息編碼器繫結項目來建構自訂繫結，在使用資料流時將 `MaxBufferSize` 屬性設定為安全值是很重要的。  
  
## <a name="xml-based-streaming-attacks"></a>XML 資料流攻擊  
 `MaxBufferSize` 單獨不足以確保 WCF 不會強制進入緩衝區預期的資料流時。 例如，WCF XML 讀取器一定會緩衝處理整個 XML 項目開始標記時開始讀取新的項目。 完成這項操作才能正確處理命名空間和屬性。 如果 `MaxReceivedMessageSize` 設定為大型 (例如，如果要啟用直接到磁碟的大型檔案資料流案例)，可能會建構惡意訊息，其中整個訊息本文為大型 XML 項目開始標記。 嘗試讀取會造成 <xref:System.OutOfMemoryException>。 這是許多可能 XML 阻絕服務攻擊的所有可減輕使用 XML 讀取器配額，< 安全使用 XML > 一節所述在本主題稍後的其中一個。 當進行資料流處理時，設定所有這些配額特別重要。  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>混合資料流及緩衝程式撰寫模型  
 許多可能的攻擊都是由於在同一個服務中混合資料流和非資料流程式撰寫模型所引起。 假設服務合約有兩個作業：一個採用 <xref:System.IO.Stream> ，另一個採用某種自訂型別的陣列。 另外假設 `MaxReceivedMessageSize` 設定為一個很大的值，讓第一個作業可以處理大型資料流。 但是，這表示大型訊息現在可以也傳送到第二個作業，而還原序列化程式會在呼叫作業之前，將記憶體中的資料當做陣列緩衝處理。 這是一種潛在的阻絕服務攻擊： `MaxBufferSize` 配額沒有限制訊息本文的大小，這也是還原序列化程式所使用的。  
  
 因此，請避免在同一個合約中混合資料流和非資料流的作業。 如果您一定要混合這兩種程式撰寫模型，請使用下列預防措施：  
  
-   將 <xref:System.Runtime.Serialization.IExtensibleDataObject> 的 <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> 屬性設定為 <xref:System.ServiceModel.ServiceBehaviorAttribute> ，以關閉 `true`功能。 如此可確保只會還原序列化屬於合約一部分的成員。  
  
-   將 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> 的 <xref:System.Runtime.Serialization.DataContractSerializer> 屬性設定為安全值。 這個配額也可在 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性上或透過組態取得。 這個配額會限制在一個還原序列化事件中還原序列化的物件數目。 一般而言，訊息合約中每個作業參數或訊息本文部分都會在一個事件中還原序列化。 當還原序列化陣列時，會將每個陣列項目視為個別的物件。  
  
-   將所有的 XML 讀取器配額設定為安全值。 請注意 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>、 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>和 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> ，並避免非資料流作業中的字串。  
  
-   請檢閱已知類型的清單，記住可以隨時產生其中任何一個 (請參閱本主題稍後的＜防止載入非預期的類型＞一節)。  
  
-   請勿使用實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別，該介面會緩衝處理大量資料。 請勿將此種型別新增至已知類型的清單。  
  
-   請勿使用 <xref:System.Xml.XmlElement>、 <xref:System.Xml.XmlNode> 陣列、 <xref:System.Byte> 陣列或實作合約中 <xref:System.Runtime.Serialization.ISerializable> 的型別。  
  
-   請勿使用 <xref:System.Xml.XmlElement>、 <xref:System.Xml.XmlNode> 陣列、 <xref:System.Byte> 陣列或實作已知類型清單中的 <xref:System.Runtime.Serialization.ISerializable> 的型別。  
  
 上述預防措施適用於當非資料流的作業使用 <xref:System.Runtime.Serialization.DataContractSerializer>時。 如果您是使用 <xref:System.Xml.Serialization.XmlSerializer>，請絕對不要在同一個服務上混合資料流和非資料流程式設計模型，因為它沒有 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> 配額的保護。  
  
### <a name="slow-stream-attacks"></a>慢速資料流攻擊  
 資料流阻絕服務攻擊的類別不包含記憶體消耗。 相反地，攻擊包含資料的慢速傳送者或接收者。 在等候傳送或接收資料時，如執行緒和可用連線等資源會用盡。 這種情況可能是由於惡意攻擊或慢速網路連線上的合法傳送者/接收者所引起。  
  
 如果要降低這些攻擊，請正確設定傳輸逾時。 如需詳細資訊，請參閱[傳輸配額](../../../../docs/framework/wcf/feature-details/transport-quotas.md)。 其次，絕對不要使用同步`Read`或`Write`WCF 中的資料流處理時的作業。  
  
## <a name="using-xml-safely"></a>安全使用 XML  
  
> [!NOTE]
>  雖然本節主要與 XML 有關，但其中的資訊也適用於「JavaScript 物件標記法」(JSON) 文件。 使用 [Mapping Between JSON and XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)時，配額的工作方式類似。  
  
### <a name="secure-xml-readers"></a>安全的 XML 讀取器  
 XML Infoset 會形成 WCF 中的所有訊息處理的基礎。 接受來自不受信任來源的 XML 資料時，會有許多必須降低之拒絕服務攻擊的可能性。 WCF 提供了特殊、 安全的 XML 讀取器。 使用其中一種標準編碼 （文字、 二進位或 MTOM） 的 WCF 中時，會自動建立這些讀取器。  
  
 這些讀取器上有些安全性功能永遠在使用中。 例如，讀取器絕對不會處理文件類型定義 (DTD)，它是阻絕服務攻擊的潛在來源，絕對不得出現在合法的 SOAP 訊息中。 其他的安全性功能包括必須設定的讀取器配額，在下節中將加以說明。  
  
 當直接使用 XML 讀取器 (例如當撰寫您自己的自訂編碼器或直接使用<xref:System.ServiceModel.Channels.Message>類別)，可能使用不受信任的資料時，一律使用 WCF 安全讀取器。 請呼叫 <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>類別上 <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>、 <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> 或 <xref:System.Xml.XmlDictionaryReader> 的其中一個靜態處理站方法多載，以建立安全的讀取器。 當建立讀取器時，請傳入安全的配額值。 請勿呼叫 `Create` 方法多載。 它們不會建立 WCF 讀取器。 相反地，它們會建立不受本節所述之安全性功能保護的讀取器。  
  
### <a name="reader-quotas"></a>讀取器配額  
 安全的 XML 讀取器有五個可設定的配額。 這些通常是使用編碼繫結項目或標準繫結上之 `ReaderQuotas` 屬性來設定的，或是使用在建立讀取器時傳遞的 <xref:System.Xml.XmlDictionaryReaderQuotas> 物件來設定。  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 這個配額會限制當讀取項目開始標記和其屬性時，在單一 `Read` 作業中讀取的位元組數目 (在非資料流處理的情況中，項目名稱本身不會納入配額的計數)。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> 十分重要的原因如下：  
  
-   當讀取項目名稱和其屬性時，它們一定會進入緩衝記憶體。 因此，在資料流處理模式中正確設定此配額是很重要的，以防止在應該進行資料流處理時有過度的緩衝處理。 如需有關會發生之實際緩衝處理量的資訊，請參閱 `MaxDepth` 配額一節。  
  
-   使用太多 XML 屬性可能會耗盡不當比例的處理時間，因為必須檢查屬性名稱的唯一性。 `MaxBytesPerRead` 可降低這個威脅。  
  
#### <a name="maxdepth"></a>MaxDepth  
 這個配額會限制 XML 項目的最大巢狀結構深度。 例如，文件 」\<A >\<B >\<C / >\</B > \< /A > 「 巢狀深度為三個。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> 十分重要的原因如下：  
  
-   `MaxDepth` 會與 `MaxBytesPerRead`互動：由於讀取器永遠會為目前項目和其所有祖系將資料保存在記憶體中，因此讀取器的最大記憶體消耗與這兩個設定的產品是成比例的。  
  
-   當還原序列化深度巢狀物件圖形時，會強制還原序列化程式存取整個堆疊並擲回無法復原的 <xref:System.StackOverflowException>。 在 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer>兩者的 XML 巢狀結構和物件巢狀結構之間有直接的相互關聯。 請使用 `MaxDepth` 來降低這個威脅。  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 這個配額會限制讀取器的「 *名稱表格*」(Nametable) 大小。 名稱表格包含會在處理 XML 文件時遇到的特定字串 (例如命名空間和前置詞)。 當這些字串在緩衝記憶體中時，請設定這個配額，以防止在應該進行資料流處理時有過度緩衝處理。  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 這個配額會限制 XML 讀取器傳回的字串大小上限。 這個配額不會限制 XML 讀取器本身的記憶體消耗，但會限制正在使用讀取器之元件中的記憶體消耗。 例如，當 <xref:System.Runtime.Serialization.DataContractSerializer> 使用以 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>保護的讀取器時，它不會還原序列化大於這個配額的字串。 當直接使用 <xref:System.Xml.XmlDictionaryReader> 類別時，不是所有的方法都會使用這個配額，而是只有特別設計來讀取字串的方法，例如 <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> 方法。 由於讀取器上的 <xref:System.Xml.XmlReader.Value%2A> 屬性不會受到這個配額影響，因此不應在需要這個配額所提供的保護時使用。  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 這個配額會限制 XML 讀取器將會傳回之基本陣列的大小上限，包括位元組陣列。 這個配額不會限制 XML 讀取器本身的記憶體消耗，但會限制正在使用讀取器之任何元件中的記憶體消耗。 例如，當 <xref:System.Runtime.Serialization.DataContractSerializer> 使用以 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>保護的讀取器時，它不會還原序列化大於這個配額的位元組陣列。 當嘗試在單一合約中混合資料流和緩衝處理的程式撰寫模型時，設定這個配額是很重要的。 請記住，當直接使用 <xref:System.Xml.XmlDictionaryReader> 類別時，只有特別設計來讀取特定基本型別之任意大小之陣列的方法 (例如 <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>) 會使用這個配額。  
  
## <a name="threats-specific-to-the-binary-encoding"></a>二進位編碼特定的威脅  
 二進位 XML 編碼 WCF 支援包含*字典字串*功能。 只要使用幾個位元組就可以編碼大型字串。 這雖然可以獲得可觀的效能，但也會引入必須降低的新阻絕服務威脅。  
  
 字典有兩種：「 *靜態* 」(Static) 和「 *動態*」(Dynamic)。 靜態字典是內建的長字串清單，可使用二進位編碼中的簡短程式碼來表示。 當讀取器建立且無法修改時，這份字串清單是固定的。 預設會使用 WCF 的靜態字典中的字串都大到足以引起嚴重的阻絕服務威脅，雖然它們可能仍會用於字典展開攻擊。 在您提供自己的靜態字典之進階狀況中，在引入大型字典字串時請小心。  
  
 動態字典功能可讓訊息定義自己的字串，並與簡短程式碼建立關聯。 在整個通訊工作階段期間，這些字串與程式碼的對應會保存在記憶體中，讓後續的訊息不必重新傳送字串，並且可以使用已經定義的程式碼。 這些字串可能有任意長度，因而引起比靜態字典中更嚴重的威脅。  
  
 第一個必須降低的威脅是動態字典 (字串與程式碼的對應表格) 變得太大的可能性。 這個字典可能會展開至數個訊息，所以 `MaxReceivedMessageSize` 配額無法提供保護，因為它只能分別套用至各個訊息。 因此， <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> 上有獨立的 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> 屬性，限制字典的大小。  
  
 與其他大部分配額不同的是，這個配額也適用於撰寫訊息時。 如果在讀取訊息時超過這個配額，便會如往常般擲回 `QuotaExceededException` 。 如果在撰寫訊息時超過這個配額，就會依原狀寫入造成超過配額的字串，而不需使用動態字典功能。  
  
### <a name="dictionary-expansion-threats"></a>字典展開威脅  
 二進位特定攻擊的一個顯著類別是由於字典展開所引起的。 如果廣泛利用字串字典功能，使用二進位形式的小型訊息可能會變成使用完整展開之文字形式的超大型訊息。 動態字典字串的展開因數會受到 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> 配額的限制，因為動態字典字串不會超過整個字典的大小上限。  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>、 `MaxStringContentLength`和 `MaxArrayLength` 屬性只限制記憶體消耗。 通常不需要它們來降低非資料流使用中的威脅，因為記憶體使用已經受到 `MaxReceivedMessageSize`的限制。 然而， `MaxReceivedMessageSize` 會計算預先展開的位元組。 當二進位編碼正在使用中時，記憶體消耗有可能會超過 `MaxReceivedMessageSize`，其只受到 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>因數的限制。 因此，當使用二進位編碼時，永遠設定所有的讀取器配額 (特別是 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) 是很重要的。  
  
 當搭配使用二進位編碼和 <xref:System.Runtime.Serialization.DataContractSerializer>時， `IExtensibleDataObject` 介面可能會誤用來掛接字典展開攻擊。 這個介面基本上是為不屬於合約之任意資料提供無限制的儲存區。 如果無法將配額設定得夠低，讓 `MaxSessionSize` 乘以 `MaxReceivedMessageSize` 不會引起問題，當使用二進位編碼時，請停用 `IExtensibleDataObject` 功能。 請將 `IgnoreExtensionDataObject` 屬性 (Attribute) 上的 `true` 屬性 (Property) 設定為 `ServiceBehaviorAttribute` 。 或者，請不要實作 `IExtensibleDataObject` 介面。 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
### <a name="quotas-summary"></a>配額摘要  
 下表為有關配額的指引摘要。  
  
|條件|要設定的重要配額|  
|---------------|-----------------------------|  
|沒有資料流或資料流處理小型訊息、文字或 MTOM 編碼|`MaxReceivedMessageSize`、 `MaxBytesPerRead`和 `MaxDepth`|  
|沒有資料流或資料流處理小型訊息、二進位編碼|`MaxReceivedMessageSize`、 `MaxSessionSize`和所有的 `ReaderQuotas`|  
|資料流處理大型訊息、文字或 MTOM 編碼|`MaxBufferSize` 和所有的 `ReaderQuotas`|  
|資料流處理大型訊息、二進位編碼|`MaxBufferSize`、 `MaxSessionSize`和所有的 `ReaderQuotas`|  
  
-   當資料流正在使用中時，不論是否正在資料流處理大型或小型訊息，永遠必須設定傳輸層逾時且不得使用同步讀取/寫入。  
  
-   如果對配額有問題，請將它設定為安全值，而不要將其保留為開放。  
  
## <a name="preventing-malicious-code-execution"></a>防止惡意程式碼執行  
 威脅的下列一般類別可以執行程式碼並造成非預期的影響：  
  
-   還原序列化程式會載入惡意、不安全或安全性敏感的型別。  
  
-   傳入訊息會造成還原序列化程式以具有非預期結果的方式，來建構通常是安全之型別的執行個體。  
  
 下列各節將進一步說明威脅的這些類別。  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (如需有關 <xref:System.Xml.Serialization.XmlSerializer> 的安全性資訊，請參閱相關文件)。<xref:System.Xml.Serialization.XmlSerializer> 的安全性模型與 <xref:System.Runtime.Serialization.DataContractSerializer> 的類似，而差異大部分是在細節方面。 例如， <xref:System.Xml.Serialization.XmlIncludeAttribute> 屬性是用於型別內含而不是 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。 然而，本主題稍後將說明 <xref:System.Xml.Serialization.XmlSerializer> 的一些專有威脅。  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>防止載入非預期的型別  
 載入非預期的型別可能會有重大的影響，不論此型別是否為惡意或只是有安全性敏感的副作用。 型別可能含有可利用的安全性弱點、在其建構函式或類別建構函式中執行安全性敏感的動作、具有加速阻絕服務攻擊的大型記憶體使用量，或是擲回不可復原的例外狀況。 型別可能會具有類別建構函式，會在載入型別時及建立執行個體之前立刻執行。 因此，控制還原序列化程式可能會載入的這組型別十分重要。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> 會以有彈性的方式來還原序列化。 它絕對不會從傳入資料讀取 Common Language Runtime (CLR) 型別和組件名稱。 雖然這與 <xref:System.Xml.Serialization.XmlSerializer>的行為類似，但是與 <xref:System.Runtime.Serialization.NetDataContractSerializer>、 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>的行為不同。 有彈性的結合可增加某種程度的安全性，因為遠端攻擊者無法只藉由在訊息中命名該型別，來指出要載入的任意型別。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> 永遠可以載入根據合約目前應載入的型別。 例如，如果資料合約有型別 `Customer`的資料成員， <xref:System.Runtime.Serialization.DataContractSerializer> 就可以在還原序列化此資料成員時載入 `Customer` 型別。  
  
 此外， <xref:System.Runtime.Serialization.DataContractSerializer> 支援多型。 雖然資料成員可宣告為 <xref:System.Object>，但是傳入資料可能會包含 `Customer` 執行個體。 這只有在 `Customer` 型別已透過下列其中一種機制，成為還原序列化程式的「已知」型別時，才有可能發生：  
  
-   套用至型別的<xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。  
  
-   指定傳回型別清單之方法的`KnownTypeAttribute` 屬性。  
  
-   `ServiceKnownTypeAttribute` 屬性。  
  
-   `KnownTypes` 組態區段。  
  
-   如果直接使用序列化程式，已知類型的清單會在建構期間明確傳遞至 <xref:System.Runtime.Serialization.DataContractSerializer> 。  
  
 上述各機制都會引入更多還原序列化程式可以載入的型別，以增加表面區域。 請控制上述各機制，以確保不會將惡意或非預期的類型新增至已知類型清單。  
  
 只要已知類型在範圍內，就可以隨時載入，而且即使合約禁止實際使用它，仍可以建立此類型的執行個體。 例如，假設使用上述其中一個機制將類型 "MyDangerousType" 新增至已知類型清單。 這表示：  
  
-   `MyDangerousType` 已載入且其類別建構函式正在執行。  
  
-   即使在還原序列化含有字串資料成員的資料合約時，惡意訊息仍然可能會造成建立 `MyDangerousType` 的執行個體。 `MyDangerousType`中的程式碼 (例如屬性 setter) 可能會執行。 完成這項操作之後，還原序列化程式會嘗試將這個執行個體指派給字串資料成員，然後失敗並有例外狀況。  
  
 當撰寫傳回已知類型清單的方法時，或將清單直接傳遞至 <xref:System.Runtime.Serialization.DataContractSerializer> 建構函式時，請確保準備清單的程式碼是安全的，並且只在受信任的資料上作業。  
  
 如果在組態中指定已知類型，請確保組態檔是安全的。 請永遠在組態中使用強式名稱 (藉由指定型別所在之已簽署組件的公開金鑰)，但不指定要載入之型別的版本。 型別載入器會自動選取最新版本 (如果可能)。 如果在組態中指定特定版本，就會有下列風險：型別可能會有在未來版本中可能會修正的安全性弱點，但有弱點的版本仍將會載入，因為它在組態中已明確指定。  
  
 已知類型太多會有另一種結果： <xref:System.Runtime.Serialization.DataContractSerializer> 會在應用程式定義域中建立序列化/還原序列化程式碼的快取，以及必須序列化和還原序列化之各個型別的項目。 只要應用程式定義域在執行中，便永遠不會清除這個快取。 因此，知道應用程式使用許多已知類型的攻擊者可以造成所有這些類型的還原序列化，導致快取使用不當比例的大量記憶體。  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>防止型別處於非預期的狀態  
 型別可能會有必須強制執行的內部一致性條件約束。 請務必小心，避免在還原序列化期間違反這些條件約束。  
  
 下面的型別範例代表太空船上氣閘的狀態，並強制執行不得同時開啟內門和外門的條件約束。  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 攻擊者可能會傳送類似這樣的惡意訊息，避開條件約束並讓物件處於無效狀態，這可能會有無法預期的結果。  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 注意下列各點可以避免這種情況：  
  
-   當 <xref:System.Runtime.Serialization.DataContractSerializer> 還原序列化大部分的類別時，建構函式不會執行。 因此，請勿依賴在建構函式中完成的任何狀態管理。  
  
-   請使用回呼來確保物件處於有效狀態中。 以 <xref:System.Runtime.Serialization.OnDeserializedAttribute> 屬性標示的回呼特別有用，因為它是在還原序列化完成之後執行，並有機會檢查和更正整體狀態。 如需詳細資訊，請參閱[版本相容序列化回呼](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)。  
  
-   請勿將資料合約類型設計為依賴呼叫 setter 屬性必須遵守的特定順序。  
  
-   請小心使用以 <xref:System.SerializableAttribute> 屬性標示的舊版型別。 其中許多都是設計來使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 遠端處理，只用於受信任的資料。 以此屬性標示之現有型別的設計可能尚未考慮到狀態安全性。  
  
-   就狀態安全性而言，請勿依賴 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性 (Attribute) 的 `DataMemberAttribute` 屬性 (Property) 來保證資料的存在。 資料可能永遠是 `null`、`zero` 或 `invalid`。  
  
-   在沒有先驗證之前，絕對不要信任從不受信任的資料來源還原序列化的物件圖形。 每個個別物件可能處於一致性狀態，但是整個物件圖形可能不是。 此外，即使物件圖形保留模式已停用，已還原序列化圖形仍可能有相同物件的多個參照，或是有循環參照。 如需詳細資訊，請參閱[序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。  
  
### <a name="using-the-netdatacontractserializer-securely"></a>安全使用 NetDataContractSerializer  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> 是對型別使用緊密結合的序列化引擎。 這與 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>很類似。 也就是說，它會從傳入資料讀取 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 組件和型別名稱，以判斷要產生何種型別。 雖然它是 WCF 的一部分，沒有提供插入此序列化引擎的方法必須撰寫自訂程式碼。 `NetDataContractSerializer`提供主要是為了簡化從移轉[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]遠端處理與 WCF。 如需詳細資訊，請參閱中相關的章節[序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。  
  
 由於訊息本身可能會指出可以載入的任何型別，因此 <xref:System.Runtime.Serialization.NetDataContractSerializer> 機制原本就是不安全的，且只應搭配受信任的資料使用。 藉由撰寫安全、型別有限制的型別繫結器，且該繫別器只允許載入安全型別 (使用 <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> 屬性)，有可能保護它的安全。  
  
 即使和受信任的資料一起使用，傳入資料仍可能不足以指定要載入的型別，特別是如果 <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> 屬性設定為 <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>時。 任何可以存取應用程式目錄或全域組件快取的人，都可以使用應載入的型別來取代惡意型別。 請正確設定權限，永遠確保應用程式目錄和全域組件快取的安全性。  
  
 一般而言，如果您允許部分信任的程式碼存取您的 `NetDataContractSerializer` 執行個體，或是控制代理選取器 (<xref:System.Runtime.Serialization.ISurrogateSelector>) 或序列化繫結器 (<xref:System.Runtime.Serialization.SerializationBinder>)，則程式碼會在序列化/還原序列化處理上行使廣大的控制力。 例如，它會插入任意型別、導致資訊洩漏、竄改結果物件圖形或序列化資料，或溢位結果序列化資料流。  
  
 `NetDataContractSerializer` 的另一個安全性問題是阻絕服務，而不是惡意程式碼執行威脅。 當使用 `NetDataContractSerializer`時，請永遠將 <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> 配額設定為安全值。 建構配置大小只受此配額限制之物件陣列的小型惡意訊息十分簡單。  
  
### <a name="xmlserializer-specific-threats"></a>XmlSerializer 特定的威脅  
 <xref:System.Xml.Serialization.XmlSerializer> 安全性模型與 <xref:System.Runtime.Serialization.DataContractSerializer>的很類似。 然而，有一些威脅是 <xref:System.Xml.Serialization.XmlSerializer>專有的。  
  
 <xref:System.Xml.Serialization.XmlSerializer> 會在執行階段產生「 *序列化組件* 」(Serialization Assembly)，其中包含實際序列化和還原序列化的程式碼；這些組件是在暫存檔目錄中建立的。 如果其他處理序或使用者具有該目錄的存取權，他們可能會使用任意程式碼來覆寫序列化/還原序列化程式碼。 然後 <xref:System.Xml.Serialization.XmlSerializer> 會使用其安全性內容來執行此程式碼，而不是序列化/還原序列化程式碼。 請確定暫存檔目錄上的權限設定是正確的，以防止這種情況發生。  
  
 <xref:System.Xml.Serialization.XmlSerializer> 也有使用預先產生之序列化組件的模式，而非在執行階段產生它們。 每當 <xref:System.Xml.Serialization.XmlSerializer> 可以找到合適的序列化組件時，就會觸發這個模式。 <xref:System.Xml.Serialization.XmlSerializer> 會檢查序列化組件是否由相同金鑰所簽署，此金鑰用於簽署含有正在序列化之型別的組件。 這會提供保護，不受偽裝成序列化組件的惡意組件所攻擊。 然而，如果含有可序列化型別的組件未簽署， <xref:System.Xml.Serialization.XmlSerializer> 就無法執行這項檢查，而會使用任何有正確名稱的組件。 如此便可能會執行惡意程式碼。 請永遠簽署含有可序列化型別的組件，或緊密控制應用程式目錄和全域組件快取的存取權，以防止引入惡意組件。  
  
 <xref:System.Xml.Serialization.XmlSerializer> 可能會受限於阻絕服務攻擊。 <xref:System.Xml.Serialization.XmlSerializer> 沒有 `MaxItemsInObjectGraph` 配額 (如同 <xref:System.Runtime.Serialization.DataContractSerializer>上所提供)。 因此，它會還原序列化任意的物件量，只受訊息大小的限制。  
  
### <a name="partial-trust-threats"></a>部分信任威脅  
 請注意下列與使用部分信任執行之程式碼有關的威脅問題。 這些威脅包括惡意的部分信任程式碼，以及惡意的部分信任程式碼與其他攻擊案例的組合 (例如，建構特定字串後再還原序列化的部分信任程式碼)。  
  
-   當使用任何序列化元件時，即使整個序列化狀況都在您的判斷提示範圍內，而且您並未處理任何不受信任的資料或物件，也絕對不要在這類使用之前判斷提示任何權限。 這類使用可能會造成安全性弱點。  
  
-   當部分信任的程式碼已控制序列化處理，無論是透過擴充點 (Surrogate)、序列化的型別，或透過其他方式，部分信任的程式碼會造成序列化程式將大量的資料輸出到序列化資料流，而對這個資料流的接收者造成阻絕服務 (DoS)。 如果您所序列化的資料是提供給對 DoS 威脅敏感的目標使用，則請勿序列化部分信任的類型，或者讓部分信任的程式碼控制序列化。  
  
-   如果您允許部分信任的程式碼存取您<xref:System.Runtime.Serialization.DataContractSerializer>執行個體，或是控制[資料合約 Surrogate](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)，它可能會執行更多的控制序列化/還原序列化程序。 例如，它會插入任意型別、導致資訊洩漏、竄改結果物件圖形或序列化資料，或溢位結果序列化資料流。 在「安全使用 NetDataContractSerializer Securely」一節中會說明等同的 <xref:System.Runtime.Serialization.NetDataContractSerializer> 威脅。  
  
-   如果 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至型別 (或標示為 `[Serializable]` 但不是 `ISerializable`的型別)，即使所有的建構函式都是非公用或依要求受到保護的，還原序列化程式仍然可以建立此型別的執行個體。  
  
-   絕對不要信任還原序列化的結果，除非已還原序列化資料受到信任，而且確定所有已知類型都是您信任的類型。 請注意，在部分信任中執行時，已知類型不會從應用程式組態檔載入 (而是從電腦組態檔載入)。  
  
-   如果您以新增的 Surrogate 將 `DataContractSerializer` 執行個體傳遞至部分信任的程式碼，則程式碼會變更該 Surrogate 上任何可修改的設定。  
  
-   對於已還原序列化物件，如果 XML 讀取器 (或其中的資料) 來自部分信任程式碼，請將結果的已還原序列化物件視為不受信任的資料。  
  
-   事實上， <xref:System.Runtime.Serialization.ExtensionDataObject> 型別沒有 Public 成員不表示其中的資料是安全的。 例如，如果您從有權限的資料來源還原序列化至部分資料所在的物件中，然後將該物件傳遞至部分信任程式碼，部分信任程式碼就可以序列化此物件，以讀取 `ExtensionDataObject` 中的資料。 當從有權限的資料來源還原序列化至稍後將傳遞至部分信任程式碼的物件中時，請考慮將 <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> 設定為 `true` 。  
  
-   在完全信任的情況下，<xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> support the serialization of private, protected, internal, 和 public members in full trust. 不過，在部分信任的情況下，只能序列化公用成員。 如果應用程式嘗試序列化非公用成員，就會擲回 `SecurityException` 。  
  
     在部分信任的情況下，若要允許內部或受保護內部成員進行序列化，請使用 `System.Runtime.CompilerServices.InternalsVisibleTo` 組件屬性。 這個屬性會允許組件宣告只有某些其他組件能夠看見其內部成員。 在此情況下，想要序列化其內部成員的組件就會宣告 System.Runtime.Serialization.dll 能夠看見其內部成員。  
  
     這種方法的優點在於不需要更高的程式碼產生路徑。  
  
     同時，也有兩個主要缺點。  
  
     第一個缺點是， `InternalsVisibleTo` 屬性 (Attribute) 的 opt-in 屬性 (Property) 屬於組件範圍。 也就是說，您無法指定只有特定類別能夠序列化其內部成員。 當然，您仍然可以選擇不要序列化特定內部成員，只要不將 `DataMember` 屬性加入至該成員即可。 同樣地，只要稍微考量可視性，開發人員也可以選擇將成員設定為內部而非私用或受保護。  
  
     第二個缺點是，這種方法仍然不支援私用或受保護成員。  
  
     為了在部分信任的情況下說明 `InternalsVisibleTo` 屬性的使用方式，請考慮下列程式：  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     在上述範例中， `PermissionsHelper.InternetZone` 會對應至部分信任的 `PermissionSet` 。 此時，如果沒有 `InternalsVisibleToAttribute`，應用程式就會失敗，並擲回 `SecurityException` ，表示在部分信任的情況下，無法序列化非公用成員。  
  
     不過，如果我們將下列程式碼加入至原始程式檔，此程式就會順利執行。  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>其他的狀態管理問題  
 其他有一些與物件狀態管理有關的問題值得您注意：  
  
-   當搭配使用資料流程式設計模型與資料流傳輸時，訊息的處理會發生在訊息到達時。 訊息的傳送者可能會在資料流處理期間中止傳送作業，如果預期還有更多內容，會讓程式碼處於無法預測的狀態中。 一般而言，請勿依賴正完成中的資料流，也不要執行如果中止資料流時無法回復的資料流作業中的任何工作。 這也適用於資料流處理本文之後可能會有格式錯誤的訊息 (例如，可能會遺失 SOAP 信封的結束標記或可能有第二個訊息本文)。  
  
-   使用 `IExtensibleDataObject` 功能可能會造成發生敏感性資料。 如果您正接受來自不受信任的來源資料進入含有 `IExtensibleObjectData` 的資料合約，然後再重新發出到簽署訊息的安全通道上，就是可能在對您完全不了解的資料提供保證。 甚至，如果您在帳戶中納入已知和未知的資料，正在傳送的整體狀態可能會變成無效。 請將延伸資料屬性選擇性地設定為 `null` ，或選擇性地停用 `IExtensibleObjectData` 功能，以避免這種情況。  
  
## <a name="schema-import"></a>結構描述匯入  
 一般來說，將匯入結構描述以產生型別的處理序只會發生在設計階段 (例如，當在 Web 服務上使用 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 來產生用戶端類別)。 然而，在更進階的情況中，您可能會在執行階段處理結構描述。 請注意，這樣做可能會讓您遭到阻絕服務攻擊。 有些結構描述可能要花很長的時間匯入。 如果結構描述有可能來自不受信任的來源，請絕對不要在這種情況中使用 <xref:System.Xml.Serialization.XmlSerializer> 結構描述匯入元件。  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>ASP.NET AJAX 整合特定的威脅  
 當使用者實作<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>或<xref:System.ServiceModel.Description.WebHttpBehavior>，WCF 會公開可接受 XML 和 JSON 訊息的端點。 但是，只有一組讀取器配額是由 XML 讀取器和 JSON 讀取器使用。 有些配額設定可能適用一個讀取器，但對於其他讀取器而言過大。  
  
 實作 `WebScriptEnablingBehavior`時，使用者可以選擇在端點公開 JavaScript Proxy。 必須考量下列安全問題：  
  
-   服務的相關資訊 (作業名稱、參數名稱等) 可透過檢查 JavaScript Proxy 取得。  
  
-   使用 JavaScript 端點時，敏感與私用的資訊可在用戶端 Web 瀏覽器快取中取得。  
  
## <a name="a-note-on-components"></a>元件注意事項  
 WCF 是有彈性且可自訂系統。 大部分的內容，本主題的焦點放在最常見的 WCF 使用案例。 不過，它可能會撰寫許多不同的方式提供 WCF 元件。 了解使用各個元件的安全性含意是很重要的。 特別之處在於：  
  
-   當您必須使用 XML 讀取器時，請使用 <xref:System.Xml.XmlDictionaryReader> 類別提供的讀取器，而非其他的讀取器。 安全的讀取器是使用 <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>、 <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>或 <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> 方法建立的。 請勿使用 <xref:System.Xml.XmlReader.Create%2A> 方法。 請永遠使用安全的配額來設定讀取器。 WCF 中的序列化引擎是使用安全的 XML 讀取器從 WCF 使用時，才安全。  
  
-   當使用 <xref:System.Runtime.Serialization.DataContractSerializer> 來還原序列化可能不受信任的資料時，請永遠設定 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> 屬性。  
  
-   當建立訊息時，如果 `maxSizeOfHeaders` 沒有提供足夠的保護，請設定 `MaxReceivedMessageSize` 參數。  
  
-   當建立編碼器時，請永遠設定相關配額，例如 `MaxSessionSize` 和 `MaxBufferSize`。  
  
-   當使用 XPath 訊息篩選條件時，請設定 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> 以限制篩選條件所瀏覽的 XML 節點的量。 請勿使用 XPath 運算式，它可能會花太長時間計算而沒有瀏覽許多節點。  
  
-   一般來說，當使用接受配額的元件時，請了解它的安全性含意並設定為安全值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [資料合約已知類型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
