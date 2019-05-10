---
title: 大型資料與資料流
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 55001904557efa1c3136a4f619348296681986ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585031"
---
# <a name="large-data-and-streaming"></a>大型資料與資料流
Windows Communication Foundation (WCF) 是一種以 XML 為基礎的通訊基礎結構。 因為 XML 資料通常編碼中定義的標準文字格式[XML 1.0 規格](https://go.microsoft.com/fwlink/?LinkId=94838)、 已連線系統開發人員和架構設計人員通常會關心傳送訊息的網路使用量 （或大小） 之間網路和以文字為基礎的編碼 XML 帶來的特殊挑戰的二進位資料的傳輸效率。  
  
## <a name="basic-considerations"></a>基本考量  
 若要提供 WCF 的下列資訊的背景資訊，本節會重點說明一些一般性的問題和考量的編碼、 二進位資料，且資料流，通常套用至連線的系統基礎結構。  
  
### <a name="encoding-data-text-vs-binary"></a>資料編碼：文字與。二元  
 常見的開發人員問題包括：由於開始標記和結束標記的重複性質，因此與二進位格式相比，XML 的額外負荷相當大；一般認為數值的編碼會龐大很多，因為它們是以文字值來表示；而二進位資料無法有效地表示，因為它必須進行特殊編碼才能內嵌在文字格式中。  
  
 雖然上述許多問題和類似問題的確存在，但是 XML Web Service 環境中的 XML 文字編碼訊息和舊版遠端程序呼叫 (RPC) 環境中的二進位編碼訊息之間的實際差異常常不如最初所想的那麼顯著。  
  
 XML 文字編碼訊息是透明化且為「人們可讀取的」，而二進位訊息相較之下常常十分模糊，而且沒有工具很難解碼。 這種在可讀性方面的差異很容易讓人忽略，二進位訊息也常常在承載中包含內嵌中繼資料，這和 XML 文字訊息一樣會增加額外負荷。 特別是二進位格式，目的是提供有彈性及動態的叫用功能。  
  
 然而，二進位格式通常會將此類描述性的中繼資料資訊包含在「標頭」中，其中也會宣告下列資料記錄的資料配置。 然後承載便會遵循這個通用的中繼資料區塊宣告，讓後續的額外負荷減至最小。 相反地，XML 會將各個資料項目封入項目或屬性中，讓各個序列化的承載物件重複包含封入的中繼資料。 因此，雖然在比較文字與二進位表示法時，因為有些描述性中繼資料必須對這兩者做表示，所以單一序列化承載物件的大小十分類似，但是二進位格式可以獲得因整體額外負荷較低而傳輸之各個額外承載物件的共用中繼資料描述的好處。  
  
 對於特定的資料型別 (例如數字)，使用固定大小的二進位數值表示法 (例如，128 位元的十進位類型而非純文字) 仍然可能會有缺點，因為純文字表示法可能會減少數個位元組。 文字資料也可能會從一般較為彈性的 XML 文字編碼方式獲得大小方面的好處，因為有些二進位格式可能會預設為 16 位元或甚至 32 位元的 Unicode，而不適用於 .NET 二進位 XML 格式。  
  
 因此，文字與二進位之間的選擇並不如假設二進位訊息永遠小於 XML 文字訊息那樣容易。  
  
 XML 文字訊息有一項無庸置疑的優點，就是它們是以標準為基礎，並提供最廣泛的互通性選項和平台支援。 如需詳細資訊，請參閱本主題稍後的 「 編碼方式 」 一節。  
  
### <a name="binary-content"></a>二進位內容  
 就結果訊息大小方面，有一個部分是二進位編碼優於文字編碼的，即為大型二進位資料項目 (例如必須在服務和其取用者之間交換的圖片、視訊、音訊剪輯，或任何其他形式的不透明二進位資料)。 若要讓資料的這些型別符合 XML 文字，常用的方法是使用 Base64 編碼方式進行編碼。  
  
 在以 Base64 編碼的字串中，每個字元代表原始 8 位元資料中的 6 位元，造成 Base64 的 4:3 編碼與額外負荷比率，且不計算通常由慣例新增的額外格式設定字元 (歸位/換行字元)。 雖然 XML 和二進位編碼之間的差別大小要視案例而定，但是在傳輸 500 MB 承載時得到超過 33% 的大小通常是無法接受的。  
  
 為避免這項編碼額外負荷，訊息傳輸最佳化機制 (MTOM) 標準允許外顯化 (Externalizing) 包含在訊息中的大型資料項目，並在不使用任何特殊編碼的情況下以二進位資料包含在訊息中。 使用 MTOM，在類似含有附件或內嵌的內容 （圖片和其他內嵌的內容;） 的 Simple Mail Transfer Protocol (SMTP) 電子郵件訊息的方式交換訊息MTOM 訊息會封裝為 multipart/related MIME 順序，其中根部分在實際的 SOAP 訊息。  
  
 MTOM SOAP 訊息是從其未編碼的版本修改，讓參照個別 MIME 部分的特殊項目標記取代包含二進位資料之訊息中的原始項目。 因此，SOAP 訊息會指向與其一起傳送的 MIME 部分，來參照二進位內容，否則就只會包含 XML 文字資料。 由於這個模型與已建立的 SMTP 模型非常接近，因此有廣泛的工具支援可在許多平台上編碼及解碼 MTOM 訊息，讓它具有極大的互通性選擇。  
  
 同樣的，如同 Base64，MTOM 也有一些 MIME 格式的必要額外負荷，因此只有在二進位資料項目的大小超過約 1 KB 時，才會看到使用 MTOM 的優點。 由於額外負荷之故，如果二進位承載保持在該臨界值之下，以 MTOM 編碼的訊息可能會大於使用 Base64 編碼二進位資料的訊息。 如需詳細資訊，請參閱本主題稍後的 「 編碼方式 」 一節。  
  
### <a name="large-data-content"></a>大型資料內容  
 除了網路使用量以外，先前提到的 500 MB 承載也會為服務和用戶端帶來很大的本機挑戰。 根據預設，WCF 處理中的訊息*緩衝的模式*。 這表示在傳送之前或接收之後，訊息的整個內容都會存在於記憶體中。 雖然這對大部分的案例都是一個很好的策略，而且對於訊息功能 (例如數位簽章和可靠的傳遞) 是必要的，但是大型訊息可能會很容易耗盡系統的資源。  
  
 處理大型承載的策略是資料流。 雖然訊息 (特別是以 XML 表示的訊息) 通常都被視為相當精簡的資料套件，但是一個訊息的大小可能會有數 GB，且類似連續資料流而非資料套件。 當在資料流模式而非緩衝模式中傳輸資料時，傳送者會以資料流的格式讓接收者可以使用訊息本文的內容，而訊息基礎結構會持續將變成可用的資料從傳送者轉寄給接收者。  
  
 發生此類大型資料內容傳輸的最常見案例就是下列二進位資料物件的傳輸：  
  
- 無法輕易分成訊息序列。  
  
- 必須及時傳遞。  
  
- 當初始化傳輸時，無法完整提供使用。  
  
 對於沒有這些條件約束的資料，通常比一個大型訊息更能夠在一個工作階段的範圍內傳送訊息的序列。 如需詳細資訊，請參閱本主題稍後的 「 資料流資料 」 一節。  
  
 傳送大量資料時您必須設定`maxAllowedContentLength`IIS 設定 (如需詳細資訊，請參閱[設定 IIS 要求限制](https://go.microsoft.com/fwlink/?LinkId=253165)) 和`maxReceivedMessageSize`繫結設定 (例如[System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A)或<xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>)。 `maxAllowedContentLength`屬性預設為 28.6 M，`maxReceivedMessageSize`屬性預設為 64 KB。  
  
## <a name="encodings"></a>編碼方式  
 *編碼*定義一組有關如何在網路上呈現訊息的規則。 *編碼器*實作這類編碼，並負責在寄件者端，開啟 記憶體中<xref:System.ServiceModel.Channels.Message>成位元組資料流或可透過網路傳送的位元組緩衝區。 在接收者端，編碼器會將位元組序列變成記憶體中的訊息。  
  
 WCF 包含三種編碼器，並可讓您撰寫及插入您自己的編碼器，如有必要。  
  
 根據預設，每個標準繫結都包括預先設定的編碼器，讓前置詞為 Net* 的繫結使用二進位編碼器 (藉由包含 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> 類別)，而 <xref:System.ServiceModel.BasicHttpBinding> 和 <xref:System.ServiceModel.WSHttpBinding> 類別則使用文字訊息編碼器 (藉由 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 類別)。  
  
|編碼器繫結項目|描述|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|文字訊息編碼器是所有 HTTP 繫結的預設編碼器，以及所有優先考量互通性之自訂繫結的適當選擇。 此編碼器不需特別處理二進位資料，即可讀取及撰寫標準 SOAP 1.1/SOAP 1.2 文字訊息。 如果<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>訊息的屬性設定為<xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>、 SOAP 信封包裝函式會從輸出中省略，而且只有訊息本文內容序列化。|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|MTOM 訊息編碼器是實作二進位資料特殊處理的文字編碼器，根據預設，它並非用於任何標準繫結中，因為它完全是依個案執行的最佳化公用程式。 如果訊息包含達到 MTOM 編碼可產生功效之臨界值的二進位資料，資料便會在訊息封套之後外顯化為 MIME 部分。 請參閱本節稍後的「啟用 MTOM」。|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|二進位訊息編碼器是 Net * 繫結和適當的選擇的預設編碼器，每當通訊雙方以 WCF 為基礎。 二進位訊息編碼器是使用 .NET 二進位 XML 格式，這是 XML 資訊設定 (Infoset) 的 Microsoft 特定二進位表示法，通常會產生比同等的 XML 1.0 表示法更小的使用量，並將二進位資料編碼為位元組資料流。|  
  
 文字訊息編碼通常是所有需要互通性之通訊路徑的最佳選擇，而二進位訊息編碼則是其他通訊路徑的最佳選擇。 與單一訊息的文字相比，二進位訊息編碼通常會產生較小的訊息大小，而在通訊工作階段的持續期間，訊息大小甚至會逐漸變得更小。 與文字編碼不同的是，二進位編碼不必對二進位資料使用特殊處理，例如使用 Base64 而將位元組表示為位元組。  
  
 如果您的方案不需要互通性，但您還是想要使用 HTTP 傳輸，可以將 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> 撰寫為使用 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 類別傳輸的自訂繫結。 如果您的服務有許多用戶端需要互通性，建議您公開平行端點，其中每個端點都已啟用適合個別用戶端的傳輸和編碼選擇。  
  
### <a name="enabling-mtom"></a>啟用 MTOM  
 當互通性成為一項需求且必須傳送大型二進位資料時，MTOM 訊息編碼是可以在標準 <xref:System.ServiceModel.BasicHttpBinding> 或 <xref:System.ServiceModel.WSHttpBinding> 繫結程序上啟用的替代編碼策略，方法是將個別 `MessageEncoding` 屬性設定為 <xref:System.ServiceModel.WSMessageEncoding.Mtom> 或將 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 撰寫為 <xref:System.ServiceModel.Channels.CustomBinding>。 下列範例程式碼，擷取自[MTOM 編碼](../../../../docs/framework/wcf/samples/mtom-encoding.md)範例示範如何在組態中啟用 MTOM。  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <wsHttpBinding>  
        <binding name="ExampleBinding" messageEncoding="Mtom"/>  
      </wsHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 如同先前所述，使用 MTOM 編碼的決定要視所傳送的資料磁碟區而定。 同時，由於 MTOM 是在繫結層級啟用的，因此啟用 MTOM 會影響指定端點上的所有作業。  
  
 由於不論二進位資料最後是否外顯化，MTOM 編碼器永遠會發出以 MTOM 編碼的 MIME/多部分訊息，因此您通常只要為與超過 1 KB 之二進位資料交換訊息的端點啟用 MTOM。 同時，如果可能的話，設計用來與啟用 MTOM 之端點一起使用的服務合約應限制為指定此類資料傳輸作業。 相關的控制功能應位於獨立的合約上。 這項「僅限 MTOM」規則只適用於透過啟用 MTOM 之端點傳送的訊息；MTOM 編碼器也可以解碼並剖析傳入的非 MTOM 訊息。  
  
 使用 MTOM 編碼器會符合所有其他的 WCF 功能。 請注意，您可能無法在所有的情況中都看到這項規則，例如當需要工作階段支援時。  
  
### <a name="programming-model"></a>程式設計模型  
 不論您在應用程式中使用這三種內建編碼器的哪一種，程式設計的操作和傳輸二進位資料時完全相同。 不同之處在於了 WCF 如何處理其資料類型所依據的資料。  
  
```  
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}   
```  
  
 當使用 MTOM 時，會根據下列規則序列化前面的資料合約：  
  
- 如果 `binaryBuffer` 不是 `null`，且當與 Base64 編碼相比時，分別包含足以證明 MTOM 外顯化額外負荷 (MIME 標頭等等) 的資料，資料便會外顯化並包含在訊息中做為二進位 MIME 部分。 如果未超過臨界值，資料便會編碼為 Base64。  
  
- 不論大小，字串 (以及所有其他不是二進位的型別) 在訊息本文內永遠會表示為字串。  
  
 不論您是否使用明確的資料合約 (如前例中所述)，在作業中使用參數清單、具備巢狀資料合約，或傳輸集合內的資料合約物件，這在 MTOM 編碼上的作用都是相同的。 位元組陣列永遠是最佳化的候選項目，如果達到最佳化臨界值，則它就是最佳選擇。  
  
> [!NOTE]
>  您不應在資料合約內使用 <xref:System.IO.Stream?displayProperty=nameWithType> 衍生型別。 資料流資料應使用資料流模型進行通訊，下面的「資料流資料」一節中將有說明。  
  
## <a name="streaming-data"></a>資料流資料  
 您有大量的資料傳輸，在 WCF 中的資料流傳輸模式時，緩衝處理與在完整的記憶體內處理訊息的預設行為是可行替代方案。  
  
 如同先前所述，如果資料無法分段、如果訊息必須及時傳遞，或是如果資料在初始化傳輸時尚未完全可供使用，只對大型訊息 (含有文字或二進位內容) 啟用資料流。  
  
### <a name="restrictions"></a>限制  
 啟用資料流時，您無法使用大量的 WCF 功能：  
  
- 無法執行訊息本文的數位簽章，因為它們需要計算整個訊息內容的雜湊。 使用資料流時，由於內容在建構及傳送訊息標頭時尚未完全可供使用，因此無法計算數位簽章。  
  
- 加密是依賴數位簽章來確認資料已正確地重新建構。  
  
- 如果訊息在傳輸中遺失，可靠工作階段必須緩衝用戶端上已傳送的訊息以供重新傳遞，且在將訊息傳遞至服務實作之前，必須將它們保存在服務上來保留訊息順序，以防收到不依順序的訊息。  
  
 由於這些功能條件約束之故，您對資料流只能使用傳輸層級安全性選項，且無法開啟可靠工作階段。 資料流只能用於下列系統定義的繫結：  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 由於 <xref:System.ServiceModel.NetTcpBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 的基礎傳輸具有固有的可靠傳遞和連線工作階段支援，因此和 HTTP 不同的是，這兩種繫結實際上只受到這些條件約束很小的影響。  
  
 資料流無法用於訊息佇列 (MSMQ) 傳輸，因此也無法搭配 <xref:System.ServiceModel.NetMsmqBinding> 或 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 類別使用。 訊息佇列傳輸只支援訊息大小受限制的緩衝資料傳輸，而所有其他傳輸對於大部分的案例都沒有任何實際的訊息大小限制。  
  
 當使用對等通道傳輸時，資料流也無法使用，因此無法用於 <xref:System.ServiceModel.NetPeerTcpBinding>。  
  
#### <a name="streaming-and-sessions"></a>資料流與工作階段  
 使用工作階段架構繫結對呼叫進行資料流處理時，可能會遇到未預期的行為。 即使使用的繫結已設定為使用工作階段，所有資料流處理呼叫還是會透過不支援工作階段的單一通道 (資料包通道) 來進行。 如果多個用戶端透過工作階段架構繫結對同一個服務物件進行資料流處理呼叫，而且服務物件的並行模式已設為單一且其執行個體內容模式已設為 PerSession，則所有呼叫必須經過資料包通道，所以一次只能處理一個呼叫。 一或多個用戶端可能會因此逾時。您可以將服務物件的執行個體內容模式設為 PerCall 或是將並行模式設為 Multiple 來解決這個問題。  
  
> [!NOTE]
>  此時 MaxConcurrentSessions 沒有作用，因為只有一個可用的「工作階段」。  
  
### <a name="enabling-streaming"></a>啟用資料流  
 您可以使用下列方法來啟用資料流：  
  
- 在資料流模式中傳送及接受要求，而在緩衝模式中接受及傳回回應 (<xref:System.ServiceModel.TransferMode.StreamedRequest>)。  
  
- 在緩衝模式中傳送及接受要求，而在資料流模式中接受及傳回回應 (<xref:System.ServiceModel.TransferMode.StreamedResponse>)。  
  
- 在資料流模式中雙向傳送和接收要求與回應。 (<xref:System.ServiceModel.TransferMode.Streamed>)  
  
 您可以將傳輸模式設定為 <xref:System.ServiceModel.TransferMode.Buffered> (這是所有繫結上的預設設定)，以停用資料流。 下列程式碼顯示如何在組態中設定傳輸模式。  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streamed"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 當您在程式碼中產生您的繫結時，必須將繫結的個別 `TransferMode` 屬性 (或是如果您正在撰寫自訂繫結，則為傳輸繫結項目) 設定為前述其中一個值。  
  
 您可以單獨在通訊方的任一端為要求和回覆或雙向開啟資料流，而不影響功能。 然而，您應該永遠假設傳輸資料大小太過龐大，因此在通訊連結的兩個端點上要調整啟用資料流。 其中一個端點未實作與 WCF 的跨平台通訊，使用資料流的能力取決於平台的資料流功能。 另一個少見的例外狀況可能是記憶體消耗導向的案例，其中用戶端或服務必須將工作集減至最小，且只能負荷小量的緩衝區大小。  
  
### <a name="enabling-asynchronous-streaming"></a>啟用非同步資料流處理  
 若要啟用非同步資料流，請將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> 端點行為加入至服務主機，並將其 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> 屬性設定為 `true`。 我們還加入了在傳送端進行真實非同步資料流處理的功能。 在將訊息串流至多個用戶端，但部分用戶端可能因為網路擁塞或完全不讀取而造成讀取速度緩慢的情節中，這項功能可以提升服務的延展性。 在這些情節中，目前不會針對用戶端封鎖服務上的個別執行緒。 這樣可確保服務可以處理更多的用戶端，從而提升服務的延展性。  
  
### <a name="programming-model-for-streamed-transfers"></a>資料流傳輸的程式設計模型  
 資料流的程式設計模型是很直接的。 如果要接收資料流資料，請指定具有單一 <xref:System.IO.Stream> 型別輸入參數的作業合約。 如果要傳回資料流資料，請傳回 <xref:System.IO.Stream> 參照。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamedService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
    [OperationContract]  
    Stream RequestInfo(string query);  
    [OperationContract(OneWay=true)]  
    void ProvideInfo(Stream data);  
}  
```  
  
 前例中的作業 `Echo` 接收並傳回資料流，因此應該用於使用 <xref:System.ServiceModel.TransferMode.Streamed> 的繫結上。 對於作業 `RequestInfo`，<xref:System.ServiceModel.TransferMode.StreamedResponse> 是最適合的，因為它只傳回 <xref:System.IO.Stream>。 單向作業最適合 <xref:System.ServiceModel.TransferMode.StreamedRequest>。  
  
 請注意，將第二個參數新增至下列 `Echo` 或 `ProvideInfo` 作業會造成服務模型還原到緩衝策略，並使用資料流的執行階段序列化表示法。 只有具備單一輸出資料流參數的作業與端對端要求資料流相容。  
  
 這項規則同樣適用於訊息合約。 如同下列訊息合約所示，您在做為資料流的訊息合約中只能有單一本文成員。 如果您希望與資料流進行其他資訊的通訊，此資訊必須包含在訊息標頭中。 訊息本文是專為資料流內容保留的。  
  
```  
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}   
```  
  
 當資料流到達檔案結尾 (EOF) 時，資料流傳輸會結束且訊息會關閉。 傳送訊息時 （傳回值或叫用作業），您可以傳遞<xref:System.IO.FileStream>和 WCF 基礎結構之後的所有資料會從都提取該資料流直到資料流已完全讀取並到達 eof 為止。 如果要傳輸來源中沒有此類預先建立之 <xref:System.IO.Stream> 衍生類別的資料流資料，請建構此類別，將該類別覆疊在您的資料流來源上，然後用來做為引數或傳回值。  
  
 當接收訊息，WCF 會建構資料流的 Base64 編碼的訊息內文內容 （或如果使用 MTOM 的個別 MIME 部分），並在讀取內容資料流到達 EOF。  
  
 雖然傳輸層的資料流也會使用任何其他的訊息合約類型 (參數清單、資料合約引數和明確的訊息合約)，但是由於此類型別訊息的序列化和還原序列化需要序列化程式的緩衝處理，因此並不建議使用此類合約變數。  
  
### <a name="special-security-considerations-for-large-data"></a>大型資料的特殊安全性考量  
 所有的繫結都可讓您限制傳入訊息的大小，以防止阻絕服務攻擊。 <xref:System.ServiceModel.BasicHttpBinding>，例如，會公開[System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A)屬性可以繫結的內送的訊息大小，並且因此也會限定的可存取的記憶體數量上限處理訊息時。 這個單位的設定是位元組，預設值是 65,536 位元組。  
  
 大型資料流案例特定的安全性威脅會造成資料在接收者預期進行資料流處理時，進行緩衝處理，引起阻絕服務。 例如，WCF 一定會緩衝處理訊息的 SOAP 標頭，因此攻擊者可能會建構包含標頭，以強制進行緩衝處理資料的大型惡意訊息。 當啟用資料流時，`MaxReceivedMessageSize` 可能會設定為極大值，因為接收者絕對不會預期在記憶體中一次緩衝處理整個訊息。 如果緩衝處理訊息，WCF 會強制執行，就會發生記憶體溢位。  
  
 因此，在這種情況中，限制傳入訊息大小上限是不夠的。 `MaxBufferSize`屬性才能限制該 WCF 緩衝區的記憶體。 重要的是在資料流處理時，將它設定為安全值 (或保留為預設值)。 例如，假設您的服務必須接收大小高達 4 GB 的檔案，然後儲存在本機磁碟上。 也請假設您的記憶體受到一次只能緩衝處理 64 KB 資料的限制。 然後您會將 `MaxReceivedMessageSize` 設定為 4 GB，而將 `MaxBufferSize` 設定為 64 KB。 同時，在您的服務實作中，必須確保您只從 64 KB 區塊的傳入資料流讀取，而且在前一個區塊寫入磁碟並從記憶體捨棄之前，不會讀取下一個區塊。  
  
 它也務必要了解這個配額只限制 WCF 所完成的緩衝並無法防止您執行您自己的服務或用戶端實作中的任何緩衝。 如需額外的安全性考量的詳細資訊，請參閱 <<c0> [ 資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。  
  
> [!NOTE]
>  使用緩衝或資料流傳輸是由端點處決定。 如果是 HTTP 傳輸，傳輸模式不會在連線上傳播，或是在 Proxy 伺服器與其他媒介之間進行傳播。 設定傳輸模式不會反映在服務介面的描述中。 之後產生 WCF 用戶端至服務，您必須編輯組態檔來設定模式，搭配資料流傳輸使用的服務。 如果是 TCP 和具名管道傳輸，會傳播傳輸模式做為原則判斷提示。  
  
## <a name="see-also"></a>另請參閱

- [如何：啟用資料流](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
