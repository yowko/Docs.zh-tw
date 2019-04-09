---
title: 資料傳輸架構概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: bb903f6d182c7a8be915daf67a4df30475cfae62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127449"
---
# <a name="data-transfer-architectural-overview"></a>資料傳輸架構概觀
Windows Communication Foundation (WCF) 可以視為傳訊基礎結構。 它可以接收訊息、加以處理，然後分派到使用者程式碼執行進一步動作，或是使用使用者程式碼提供的資料建構訊息，然後傳遞到目的地。 此主題將針對進階程式開發人員，描述處理訊息與所包含資料的架構。 如需如何傳送與接收資料的簡化型工作導向檢視，請參閱 [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。  
  
> [!NOTE]
>  本主題討論 WCF 實作詳細資料不會顯示藉由檢查 WCF 物件模型。 關於已記載的實作詳細資料，依序有兩件需要注意的事項。 首先，描述已經過簡化，實際的實作可能會因為最佳化或其他原因而更為複雜。 第二，絕不要依賴特定的實作詳細資料 (即使已記載於文件中)，因為這些詳細資料可能會在不同的版本中 (甚至是在服務版本中) 變更而不另行通知。  
  
## <a name="basic-architecture"></a>基本架構  
 在 WCF 訊息處理功能的核心<xref:System.ServiceModel.Channels.Message>類別中的詳細資料中所述[Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。 WCF 執行階段元件可以分成兩個主要部分： 通道堆疊與服務架構，與<xref:System.ServiceModel.Channels.Message>當做連接點的類別。  
  
 通道堆疊負責在有效 <xref:System.ServiceModel.Channels.Message> 執行個體，以及對應至傳送或接收訊息資料的某些動作之間進行轉換。 在傳送端，通道堆疊會取用有效的 <xref:System.ServiceModel.Channels.Message> 執行個體，然後在經過某些處理後，執行邏輯上對應至傳送訊息的某些動作。 這些動作可能是傳送 TCP 或 HTTP 封包、將訊息存放在訊息佇列中、將訊息寫入資料庫、將訊息儲存在檔案共用，或是任何視實作而定的其他動作。 最常見的動作是透過網路通訊協定傳送訊息。 在接收端，則發生相反的情況—偵測到動作 (可能是 TCP 或 HTTP 封包抵達，或是任何其他動作)，然後在經過處理後，通道堆疊會將這個動作轉換為有效的 <xref:System.ServiceModel.Channels.Message> 執行個體。  
  
 您可以使用 WCF 使用<xref:System.ServiceModel.Channels.Message>類別與通道堆疊直接。 但是，這麼做是很困難並且耗時的。 此外，<xref:System.ServiceModel.Channels.Message>物件會提供不支援中繼資料，因此如果您使用 WCF 以這種方式，您就無法產生強類型的 WCF 用戶端。  
  
 因此，WCF 會包含提供簡單易用程式設計模型，您可以使用它來建構與接收的服務架構`Message`物件。 服務架構會透過服務合約的概念，將服務對應至 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，然後將訊息分派至使用者作業，這個作業是使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 屬性標記的單純 <xref:System.ServiceModel.OperationContractAttribute> 方法 (如需詳細資料，請參閱 [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md))。 這些方法會有參數與傳回值。 在服務端，服務架構會將傳入的 <xref:System.ServiceModel.Channels.Message> 執行個體轉換成參數，然後將傳回值轉換成傳出的 <xref:System.ServiceModel.Channels.Message> 執行個體。 在用戶端，則執行相反的動作。 例如，請考量下列 `FindAirfare` 作業。  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 假設在用戶端呼叫 `FindAirfare` 。 用戶端的服務架構會將 `FromCity` 和 `ToCity` 參數轉換成傳出的 <xref:System.ServiceModel.Channels.Message> 執行個體，並將其傳遞至要傳送的通道堆疊。  
  
 在服務端，當來自通道堆疊的 <xref:System.ServiceModel.Channels.Message> 執行個體抵達時，服務架構會從訊息擷取相關資料以填入 `FromCity` 和 `ToCity` 參數，然後呼叫服務端的 `FindAirfare` 方法。 當方法傳回時，服務架構會取用傳回的整數值以及 `IsDirectFlight` 輸出參數，然後建立包含這項資訊的 <xref:System.ServiceModel.Channels.Message> 物件執行個體。 然後將 `Message` 執行個體傳遞至要傳回用戶端的通道堆疊。  
  
 在用戶端，包含回應訊息的 <xref:System.ServiceModel.Channels.Message> 執行個體會出現在通道堆疊。 服務架構會擷取傳回值以及 `IsDirectFlight` 值，然後將這些傳回給用戶端的呼叫者。  
  
## <a name="message-class"></a>訊息類別  
 <xref:System.ServiceModel.Channels.Message> 類別是要用來當做訊息的抽象表示法，但其設計與 SOAP 訊息有強烈關聯。 <xref:System.ServiceModel.Channels.Message> 包含三段主要的資訊：訊息本文、訊息標頭和訊息屬性。  
  
## <a name="message-body"></a>訊息本文  
 訊息本文是用來表示訊息的實際資料承載。 訊息本文一定會當做 XML Infoset 表示。 這不表示建立，或在 WCF 中收到的所有訊息必須都是 XML 格式。 而是留給通道堆疊決定如何解譯訊息本文。 可能會將本文當做 XML 發出、轉換成某些其他格式，或甚至整個省略。 當然，大部分的 WCF 提供的繫結，與訊息本文會表示為 SOAP envelope 的主體區段中的 XML 內容。  
  
 重點是要了解 `Message` 類別不一定需要包含使用 XML 資料表示本文的緩衝區。 就邏輯上來說， `Message` 會包含 XML Infoset，但是可能會使用動態方式建構這個 Infoset，並且一定不會以實體方式存在記憶體中。  
  
### <a name="putting-data-into-the-message-body"></a>將資料放入訊息本文  
 在將資料放入訊息本文方面並沒有統一的機制。 <xref:System.ServiceModel.Channels.Message> 類別有一個抽象方法， <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>，它會取用 <xref:System.Xml.XmlDictionaryWriter>。 <xref:System.ServiceModel.Channels.Message> 類別的每個子類別會負責覆寫這個方法，然後寫入專屬的內容。 訊息本文邏輯上會包含 `OnWriteBodyContent` 產生的 XML Infoset。 例如，請考量下列 `Message` 子類別。  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 實際上 `AirfareRequestMessage` 執行個體只包含兩個字串 ("fromCity" 和 "toCity")。 但是，邏輯上訊息會包含下列 XML Infoset：  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 當然，通常不會使用這種方式建立訊息，因為您可以使用服務架構從作業合約參數建立像之前的訊息。 此外， <xref:System.ServiceModel.Channels.Message> 類別有靜態 `CreateMessage` 方法，您可以用來搭配內容的一般型別建立訊息：空白訊息、包含使用 <xref:System.Runtime.Serialization.DataContractSerializer>序列化為 XML 之物件的訊息、包含 SOAP 錯誤的訊息，以及包含使用 <xref:System.Xml.XmlReader>表示之 XML 的訊息等等。  
  
### <a name="getting-data-from-a-message-body"></a>從訊息本文取得資料  
 您可以使用兩種主要方法擷取儲存在訊息本文中的資料：  
  
-   您可以藉由呼叫 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> 方法然後傳入 XML 寫入器，一次取得整個訊息本文。 完整的訊息本文會寫至這個寫入器。 一次取得整個訊息本文也稱為「 *寫入訊息*」(Writing a Message)。 當傳送訊息時寫入主要是由通道堆疊完成，通道堆疊的某些部分通常能夠存取整個訊息本文、加以編碼然後傳送。  
  
-   從訊息本文取得資訊的另一種方法，是呼叫 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> 然後取得 XML 讀取器。 然後可以藉由呼叫讀取器上的方法，依需要以循序方式存取訊息本文。 以片段方式取得訊息本文也稱為「 *讀取訊息*」(Reading a Message)。 主要是服務架構會在接收訊息時使用讀取訊息。 例如，當 <xref:System.Runtime.Serialization.DataContractSerializer> 正在使用時，服務架構會透過本文取得 XML 讀取器，並且將其傳遞給還原序列化引擎，然後就會開始逐一讀取訊息項目並建構對應的物件圖形。  
  
 訊息本文只能擷取一次。 就可以使用順向資料流。 例如，您可以寫入 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> 覆寫，以便從 <xref:System.IO.FileStream> 讀取然後使用 XML Infoset 的方式傳回結果。 您永遠不會將需要 「 倒轉 」 至檔案的開頭。  
  
 `WriteBodyContents` 和 `GetReaderAtBodyContents` 方法只會檢查之前從未擷取過訊息本文，然後分別呼叫 `OnWriteBodyContents` 或 `OnGetReaderAtBodyContents`。  
  
## <a name="message-usage-in-wcf"></a>WCF 中的訊息使用方式  
 大部分的訊息都能夠分類為「 *傳出* 」(Outgoing) (由服務架構建立並透過通道堆疊傳送) 或「 *傳入* 」(Incoming) (來自通道堆疊並由服務架構解譯)。 此外，通道堆疊可以在經過緩衝處理或資料流模式中運作。 服務架構可能也會公開經過資料流處理或非資料流處理的程式設計模型。 這種做法會造成下表列出的案例，以及其實作的簡化詳細資料。  
  
|訊息類型|訊息中的本文資料|寫入 (OnWriteBodyContents) 實作|讀取 (OnGetReaderAtBodyContents) 實作|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|傳出，從經過非資料流處理的程式設計模型建立|寫入訊息需要的資料 (例如，物件與需要序列化它的 <xref:System.Runtime.Serialization.DataContractSerializer> 執行個體)*|自訂邏輯以根據儲存資料寫出訊息 (例如，呼叫 `WriteObject` 上的 `DataContractSerializer` (如果這是使用中的序列化程式))*|呼叫 `OnWriteBodyContents`、緩衝處理結果、透過緩衝區傳回 XML 讀取器|  
|傳出，從經過資料流處理的程式設計模型建立|使用要寫入之資料的 `Stream` *|使用 <xref:System.Xml.IStreamProvider> 機制從儲存的資料流寫出資料*|呼叫 `OnWriteBodyContents`、緩衝處理結果、透過緩衝區傳回 XML 讀取器|  
|從資料流通道堆疊傳入|`Stream` 物件，表示透過網路傳入並且搭配 <xref:System.Xml.XmlReader> 的資料|寫出內容從儲存`XmlReader`使用 `WriteNode`|會傳回儲存 `XmlReader`|  
|從非資料流的通道堆疊傳入|包含搭配 `XmlReader` 之本文資料的緩衝區|寫出內容從儲存`XmlReader`使用 `WriteNode`|傳回儲存的 lang|  
  
 \* 這些項目不會直接實作`Message`子類別，但在子類別的<xref:System.ServiceModel.Channels.BodyWriter>類別。 如需 <xref:System.ServiceModel.Channels.BodyWriter>的詳細資訊，請參閱 [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。  
  
## <a name="message-headers"></a>訊息標頭  
 包含標頭的訊息。 標頭邏輯上是由與名稱、命名空間，以及一些其他屬性關聯的 XML Infoset 所組成。 使用 `Headers` 的 <xref:System.ServiceModel.Channels.Message>屬性可以存取訊息標頭。 每個標頭是由 <xref:System.ServiceModel.Channels.MessageHeader> 類別表示。 通常當使用設定的通道堆疊搭配 SOAP 訊息運作時，訊息標頭會對應到 SOAP 訊息標頭。  
  
 將資訊放入訊息標頭以及從中擷取資訊就像使用訊息本文。 因為不支援資料流所以處理序稍微經過簡化。 您可以存取相同標頭的內容一次以上，並且以任意順序存取標頭，以強制一定要緩衝處理標頭。 沒有任何可透過標頭，取得 XML 讀取器的一般用途機制，但沒有`MessageHeader`代表可讀取的標頭，與這類功能的 WCF 內部的子類別。 當使用自訂應用程式標頭的訊息傳入時， `MessageHeader` 的型別是由通道堆疊建立。 這可讓服務架構使用還原序列化引擎 (例如 <xref:System.Runtime.Serialization.DataContractSerializer>) 來解譯這些標頭。  
  
 如需詳細資訊，請參閱 < [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。  
  
## <a name="message-properties"></a>郵件內容  
 訊息會包含屬性。 「 *屬性* 」(Property) 是與字串名稱關聯的任何 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件。 透過 `Properties` 的 `Message`屬性可以存取屬性。  
  
 不像訊息本文和訊息標頭 (通常會分別對應至 SOAP 本文與 SOAP 標頭)，訊息屬性通常不會與訊息一起傳送或接收。 訊息屬性的存在主要是當做通訊機制，將有關訊息的資料在通道堆疊的各個通道之間傳遞，以及在通道堆疊與服務模型之間傳遞。  
  
 例如，HTTP 傳輸通道，WCF 的一部分是能夠產生各種 HTTP 狀態碼，例如 「 404 （找不到） 」 和 「 500 （內部伺服器錯誤），「 當其將回應傳送給用戶端。 在傳送之前的回覆訊息，它會檢查是否`Properties`的`Message`包含一個稱為"httpResponse"，其中包含型別的物件的屬性<xref:System.ServiceModel.Channels.HttpResponseMessageProperty>。 如果找到這類屬性，它會查看 <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> 屬性然後使用該狀態碼。 如果找不到，就會使用預設「200 (確定)」代碼。  
  
 如需詳細資訊，請參閱 < [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。  
  
### <a name="the-message-as-a-whole"></a>整個訊息  
 到目前為止，已經單獨討論過存取訊息各部分的方法。 但是， <xref:System.ServiceModel.Channels.Message> 類別也提供方法與整個訊息一起運作。 例如， `WriteMessage` 方法會將整個訊息寫出至 XML 寫入器。  
  
 為了要能夠這樣做，就必須在整個 `Message` 執行個體與 XML Infoset 之間定義對應。 事實上，存在這類對應：WCF 會使用 SOAP 標準定義這個對應。 當寫出 `Message` 執行個體當做 XML Infoset 時，產生的 Infoset 是包含訊息的有效 SOAP 封套。 因此， `WriteMessage` 通常會執行下列步驟：  
  
1.  寫入 SOAP 封套項目開頭標記。  
  
2.  寫入 SOAP 標頭項目開頭標記、寫出所有的標頭，然後關閉標頭項目。  
  
3.  寫入 SOAP 本文項目開頭標記。  
  
4.  呼叫 `WriteBodyContents` 或對等的方法以寫出本文。  
  
5.  關閉本文與封套項目。  
  
 之前的步驟與 SOAP 標準緊密相關。 因為事實上存在多個 SOAP 版本導致情況變得複雜；例如，可以在不了解使用中之 SOAP 版本的情況下正確寫出 SOAP 封套項目。 同樣地，在某些案例中，可能想要完全關閉這項複雜的 SOAP 特定對應。  
  
 針對這些用途，在 `Version` 會提供 `Message`屬性。 當寫出訊息時可以設定要使用的 SOAP 版本，或是可以設定為 `None` 以避免任何 SOAP 特定對應。 如果 `Version` 屬性設定為 `None`，與整個訊息一起運作的方法會當做訊息只是由其本文所組成；例如， `WriteMessage` 只會呼叫 `WriteBodyContents` 而不是執行上述列出的多個步驟。 預期在傳入訊息上，將會自動偵測 `Version` 並正確設定。  
  
## <a name="the-channel-stack"></a>通道堆疊  
  
### <a name="channels"></a>通道  
 如同之前所述，通道堆疊負責將傳出 <xref:System.ServiceModel.Channels.Message> 執行個體轉換成某些動作 (例如在網路上傳送封包)，或是將某些動作 (例如接收網路封包) 轉換成傳入 `Message` 執行個體。  
  
 通道堆疊是由一或多個依順序排列的通道組成。 傳出 `Message` 執行個體會傳遞至堆疊中的第一個通道 (也稱為「 *最上層通道*」(Topmost Channel))，然後再向下傳遞至堆疊中的下一個通道，以此類推。 訊息會終止在最後一個通道，稱為「 *傳輸通道*」(Transport Channel)。 傳入訊息來自傳輸通道，並且會在堆疊的通道間向上傳遞。 從最上層通道，訊息通常會傳遞至服務架構。 雖然這是應用程式訊息的常見模式，某些通道的運作方式卻有些不同；例如，通道可能會在沒有收到上層通道所傳遞訊息的情況下，傳送專屬的基礎結構訊息。  
  
 當訊息在堆疊內傳遞時，通道可能會在訊息上以各種方式作業。 最常見的作業是將標頭新增至傳出訊息，然後讀取傳入訊息上的標頭。 例如，通道可能會計算訊息的數位簽章，然後將其新增當做標頭。 通道也會在傳入訊息上檢查這個數位簽章標頭，然後封鎖沒有有效簽章的訊息避免在通道堆疊向上傳遞。 通道通常也會設定或檢查訊息屬性。 訊息本文通常是未修改，雖然允許這麼做，例如，WCF 安全性通道能夠加密訊息本文。  
  
### <a name="transport-channels-and-message-encoders"></a>傳輸通道與訊息編碼器  
 堆疊中的最底層通道負責將傳出 <xref:System.ServiceModel.Channels.Message>(其他通道已修改過) 實際轉換為某些動作。 在接收端，這是將某些動作轉換為讓其他通道處理之 `Message` 的通道。  
  
 如同之前所述，動作可能有很多種：經由各種通訊協定傳送或接收網路封包、在資料庫中讀取或寫入訊息，或是在訊息佇列中新增或清除佇列訊息，以提供為數不多的範例。 所有這些動作都有一個共通： 它們需要 WCF 之間轉換`Message`執行個體和實際位元組，可以傳送、 接收、 讀取、 寫入，群組排入佇列，或從佇列中清除。 將 `Message` 轉換為位元組群組的程序稱為「 *編碼*」(Encoding)，而從位元組群組建立 `Message` 的反向程序稱為「 *解碼*」(Decoding)。  
  
 大部分的傳輸通道會使用稱為「 *訊息編碼器* 」(Message Encoder) 的元件以完成編碼與解碼工作。 訊息編碼器是 <xref:System.ServiceModel.Channels.MessageEncoder> 類別的子類別。 `MessageEncoder` 包含各種`ReadMessage`並`WriteMessage`之間進行轉換的方法多載`Message`和位元組群組。  
  
 在傳送端，緩衝處理的傳輸通道會將從上一層通道接收到的 `Message` 物件傳遞到 `WriteMessage`。 它會取回位元組陣列，然後用來執行其動作 (例如將這些位元組封裝成有效 TCP 封包，然後將它們傳送至正確的目的地)。 資料流傳輸通道會先建立 `Stream` (例如，透過傳出 TCP 連線)，然後同時傳遞需要傳送的 `Stream` 和 `Message` 至適當 `WriteMessage` 多載以寫出訊息。  
  
 在接收端，緩衝處理的傳輸通道會將傳入位元組 (例如，從傳入 TCP 封包) 擷取至陣列中，然後呼叫 `ReadMessage` 以取得能夠在通道堆疊進一步向上傳遞的 `Message` 物件。 資料流傳輸通道會建立 `Stream` 物件 (例如，經由傳入 TCP 連線的網路資料流)，然後將其傳遞至 `ReadMessage` 以取回 `Message` 物件。  
  
 傳輸通道與訊息編碼器之間的分隔並不是強制性的；可以寫入不使用訊息編碼器的傳輸通道。 但是，這項分隔的優點是容易撰寫。 只要傳輸通道使用的基底<xref:System.ServiceModel.Channels.MessageEncoder>，它可以搭配任何 WCF 或協力廠商訊息編碼器。 同樣地，相同的編碼器通常能夠在任何傳輸通道中使用。  
  
### <a name="message-encoder-operation"></a>訊息編碼器作業  
 若要描述編碼器的一般作業，考量下列四種案例會有幫助。  
  
|運算|註解|  
|---------------|-------------|  
|編碼，經過緩衝處理|在經過緩衝處理模式中，編碼器通常會建立大小會變動的緩衝區，然後在緩衝區建立 XML 寫入器。 然後它會在要編碼的訊息上呼叫 <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> 以寫出標頭，然後本文會使用 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>，如同本主題中說明有關 `Message` 的之前章節。 然後就會傳回緩衝區的內容 (以位元組陣列表示) 以便讓傳輸通道使用。|  
|編碼，經過資料流處理|在經過資料流處理模式中，作業類似上述說明，但是更為簡單。 不需要緩衝區。 XML 寫入器會以一般方式在資料流上建立，然後在 <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> 上呼叫 `Message` 以寫出至這個寫入器。|  
|解碼，經過緩衝處理|當在經過緩衝處理模式中進行解碼時，通常會建立包含經過緩衝處理資料的特殊 `Message` 子類別。 會讀取訊息的標頭，然後建立位於訊息本文上的 XML 讀取器。 這是會跟 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>一起傳回的讀取器。|  
|解碼，經過資料流處理|當在經過資料流處理模式中進行解碼時，通常會建立特別訊息子類別。 資料流的進階程度剛好足以讀取所有標頭並位於訊息本文上。 然後會在資料流上建立 XML 讀取器。 這是會跟 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>一起傳回的讀取器。|  
  
 編碼器也能夠執行其他功能。 例如，編碼器能夠集區 XML 讀取器和寫入器。 有需要就建立新的 XML 讀取器或寫入器是很昂貴的。 因此，編碼器通常會使用可設定的大小，維護讀取器的集區以及寫入器的集區。 中的先前所述的編碼器作業說明，每當的片語 「 建立 XML 讀取器/寫入器 」 會使用，這通常表示 「 從集區取用一個，或建立一個，如果其中一個無法使用 」。 編碼器 (和解碼時所建立的 `Message` 子類別) 包含邏輯，在不再需要使用讀取器和寫入器時 (例如，當 `Message` 已關閉) 將其傳回至集區。  
  
 WCF 會提供三種訊息編碼器，雖然您可以建立額外的自訂型別。 提供的類型為文字、二進位以及訊息傳輸最佳化機制 (MTOM)。 在 [Choosing a Message Encoder](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)中會詳細描述這些類型。  
  
### <a name="the-istreamprovider-interface"></a>IStreamProvider 介面  
 將含有經過資料流處理之本文的傳出訊息寫入至 XML 寫入器時， <xref:System.ServiceModel.Channels.Message> 將會在其 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> 實作中使用類似下面一連串的呼叫：  
  
-   在資料流前面寫入任何必要的資訊，(例如，開頭 XML 標記)。  
  
-   寫入資料流。  
  
-   在資料流後面寫入任何資訊，(例如，結束 XML 標記)。  
  
 這很適合用在類似文字 XML 編碼方式的編碼。 但是，有些編碼並不會將 XML Infoset 資訊 (例如，XML 項目的開頭及結束標記) 與包含在項目內的資料放在一起。 例如，在 MTOM 編碼中，訊息會分割為多個部分。 其中一個部分會包含 XML Infoset，而這其中可能會包含實際項目內容之其他部分的參考。 XML Infoset 通常會比資料流處理後的內容還要小，因此合理的做法是先緩衝處理 Infoset，再將它寫出，然後以資料流的處理方式寫入內容。 這表示在寫入結尾項目標記以前，應該還沒有寫出資料流。  
  
 為此，這時會使用 <xref:System.Xml.IStreamProvider> 介面。 這個介面具有可以傳回要寫入之資料流的 <xref:System.Xml.IStreamProvider.GetStream> 方法。 寫出 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> 中已由資料流處理之訊息本文的正確方式如下所示：  
  
1.  在資料流前面寫入任何必要的資訊，(例如，開頭 XML 標記)。  
  
2.  配合傳回要寫入之資料流的 `WriteValue` 實作，在接受 <xref:System.Xml.XmlDictionaryWriter> 的 <xref:System.Xml.IStreamProvider>上呼叫 `IStreamProvider` 多載。  
  
3.  在資料流後面寫入任何資訊，(例如，結束 XML 標記)。  
  
 透過這種方式，XML 寫入器就可以選擇呼叫 <xref:System.Xml.IStreamProvider.GetStream> 以及寫出經過資料流處理之資料的時機。 例如，文字及二進位 XML 寫入器將立即呼叫此方法，並在開始與結束標記之間寫出資料流處理內容。 MTOM 寫入器則可能會決定於稍後準備好要寫入訊息的適當部分時，再呼叫 <xref:System.Xml.IStreamProvider.GetStream> 。  
  
## <a name="representing-data-in-the-service-framework"></a>在服務架構中表示資料  
 本主題的 「 基本架構 」 一節所述，「 服務 」 架構是 WCF，以及其他項目，是負責將訊息資料的方便使用的程式設計模型之間的轉換，但實際的部分`Message`執行個體。 通常訊息交換在服務架構中會表示為使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 屬性標記的 <xref:System.ServiceModel.OperationContractAttribute> 方法。 方法可以取用某些參數然後傳回值或輸出參數 (或兩者皆是)。 在服務端，輸入參數代表傳入訊息，而傳回值與輸出參數代表傳出訊息。 在用戶端，則是反向作業。 在 [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)中會詳細描述使用參數與傳回值之描述訊息的程式設計模型。 但是，這個章節將提供簡短的概觀。  
  
## <a name="programming-models"></a>程式設計模型  
 WCF 服務架構支援五個不同的程式設計模型以描述訊息：  
  
### <a name="1-the-empty-message"></a>1.空訊息  
 這是最單純的案例。 若要描述空的傳入訊息，請不要使用任何輸入參數。  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 若要描述空的傳出訊息，請使用 void 傳回值並且不要使用任何輸出參數：  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 請注意這與單向作業合約不同：  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 在 `SetDesiredTemperature` 範例中，會描述雙向訊息交換模式。 訊息會從作業傳回，但是訊息為空的。 可以從作業傳回錯誤。 在 "Set Lightbulb" 範例中，訊息交換模式是單向的，所以沒有需要描述的傳出訊息。 在此例中服務無法將任何狀態傳回用戶端。  
  
### <a name="2-using-the-message-class-directly"></a>2.直接使用訊息類別  
 可以在作業合約中直接使用 <xref:System.ServiceModel.Channels.Message> 類別 (或是其中一個子類別)。 在此例中，服務架構只會在不進行任何處理的情況下把作業的 `Message` 傳遞給通道堆疊 (反之亦然)。  
  
 直接使用 `Message` 有兩個主要的使用案例。 當沒有任何其他程式設計模型能提供足夠的彈性以描述訊息時，您可以在進階案例使用它。 例如，您可能想要使用磁碟上的檔案描述訊息，將檔案的屬性變成訊息標頭，而檔案的內容變成訊息本文。 然後可以建立類似下列的項目。  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 第二種在作業合約中常見的 `Message` 使用方式，是當服務不在意特定的訊息內容，並且將訊息當做黑箱進行作業時。 例如，您可能會有將訊息轉寄給多個其他收件者的服務。 合約寫入方式可以如下所示。  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 動作 ="*"列實際上會關閉訊息分派，並可確保所有訊息都傳送給`IForwardingService`合約到手`ForwardMessage`作業。 （一般來說，發送器會檢查訊息的"Action"標頭，來判斷要讓哪些作業。 動作 ="\*"表示"的動作標頭的所有可能值"。)動作的組合 ="\*」 與使用 Message 當做參數稱為 「 通用合約 」，因為它能夠接收所有可能的訊息。 若要能夠傳送所有可能的訊息，使用 Message 當做傳回值，並設定`ReplyAction`到 「\*"。 這會避免服務架構新增專屬的 Action 標頭，讓您能夠使用傳回的 `Message` 物件控制這個標頭。  
  
### <a name="3-message-contracts"></a>3.訊息合約  
 WCF 會提供宣告式程式設計模型以描述訊息，稱為*訊息合約*。 這個模型在 [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)中有更詳細的說明。 整個訊息在本質上是由使用像是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 之屬性的單一 <xref:System.ServiceModel.MessageHeaderAttribute> 型別表示，以描述訊息合約類別與訊息之間的對應方式。  
  
 訊息合約提供對產生的 `Message` 執行個體提供許多控制 (雖然很明顯地不像直接使用 `Message` 類別一樣能夠提供那麼多的控制)。 例如，訊息本文通常是由多段資訊所組成，每段資訊以專屬的 XML 項目表示。 這些項目可能會直接發生在本文中 (「*不包裝* 」(Bare) 模式)，或是可能「 *包裝* 」(Wrapped) 在內含 XML 項目中。 使用訊息合約程式設計模型能夠讓您決定要使用不包裝或包裝模式，然後控制包裝函式與命名空間名稱。  
  
 下列訊息合約的程式碼範例示範這些功能。  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 標記為要序列化的項目 (使用 <xref:System.ServiceModel.MessageBodyMemberAttribute>、 <xref:System.ServiceModel.MessageHeaderAttribute>或其他相關屬性) 必須可序列化，才能參與訊息合約。 如需詳細資訊，請參閱本主題稍後的 < 序列化 > 一節。  
  
### <a name="4-parameters"></a>4.參數  
 想要描述作業而在多個資料片段執行作業的程式開發人員，通常不需要訊息合約提供的控制等級。 例如，當建立新的服務時，人們通常不想決定要使用不包裝或包裝模式，以及決定包裝函式項目的名稱。 做這些決定通常需要深入了解 Web 服務與 SOAP。  
  
 WCF 服務架構可以自動挑選最佳與最互通的 SOAP 表示法傳送或接收多個相關的片段的詳細資訊，而不需要使用者上強制套用這些選項。 只要描述這些資訊片段當做作業合約的參數或傳回值，就可以完成這個動作。 例如，請考量下列作業合約。  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 服務架構會自動決定將所有三項資訊片段 (`customerID`、 `item`和 `quantity`) 放入訊息本文，然後將其包裝在名為 `SubmitOrderRequest`的包裝函式項目中。  
  
 建議方法是將要傳送或接收的資訊描述當做作業合約參數的簡單清單，除非有特殊原因必須使用更複雜的訊息合約或 `Message`架構的程式設計模型。  
  
### <a name="5-stream"></a>5.資料流  
 在作業合約中使用 `Stream` 或其中一個子類別，或是當做訊息合約中的單獨訊息本文部分，可以視為與上述不同的程式設計模型。 以這種方式使用 `Stream` 是確保合約能夠用在經過資料流處理方式的唯一辦法，除非寫入專屬的與資料流相容之 `Message` 子類別。 如需詳細資訊，請參閱 < [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。  
  
 當以這種方式使用 `Stream` 或其中一個子類別時，就不會叫用序列化程式。 針對傳出訊息會建立特殊的資料流 `Message` 子類別，然後會如同 <xref:System.Xml.IStreamProvider> 介面上章節中所述寫出資料流。 針對傳入訊息，服務架構會在傳入訊息上建立 `Stream` 子類別，然後將其提供給作業使用。  
  
## <a name="programming-model-restrictions"></a>程式設計模型限制  
 上述的程式設計模型不能任意組合。 例如，如果作業接受訊息合約類型，訊息合約必須是其唯一的輸入參數。 此外，然後作業必須傳回空訊息 (屬於 void 的傳回型別) 或另一個訊息合約。 這些程式設計模型限制是以每個特定的程式設計模型的主題所述：[使用訊息合約](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)， [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)，以及[Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。  
  
## <a name="message-formatters"></a>訊息格式器  
 藉由將名為「 *訊息格式器* 」(Message Formatter) 的元件插入服務架構可以支援上述程式設計模型。 訊息格式器所實作的型別<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>或<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>介面，或兩者，以用於用戶端和服務 WCF 用戶端，分別。  
  
 通常是藉由行為插入訊息格式器。 例如， <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 會插入資料合約訊息格式器。 可以藉由在服務端的 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> 方法中將 <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> 設定為正確的格式器，或是藉由在用戶端的 <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> 方法中將 <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> 設定為正確的格式器以達到此目的。  
  
 下表列出訊息格式器可能會實作的方法。  
  
|介面|方法|動作|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|將傳入 `Message` 轉換成作業參數|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|從作業傳回值/輸出參數建立傳出 `Message`|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|從作業參數建立傳出 `Message`|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|將傳入 `Message` 轉換為傳回值/輸出參數|  
  
## <a name="serialization"></a>序列化  
 當您使用訊息合約或參數描述訊息內容時，必須使用序列化在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別與 XML Infoset 表示法之間進行轉換。 例如，使用在其他位置，在 WCF 中，序列化<xref:System.ServiceModel.Channels.Message>有個泛型<xref:System.ServiceModel.Channels.Message.GetBody%2A>可用來還原序列化訊息的整個主體讀入物件的方法。  
  
 WCF 支援序列化和還原序列化參數及訊息部分的 「 現成 」 的兩種序列化技術：<xref:System.Runtime.Serialization.DataContractSerializer>而`XmlSerializer`。 此外，您可以撰寫自訂序列化程式。 不過，WCF 的其他部分 (例如泛型`GetBody`方法或 SOAP 錯誤序列化) 可能會受限於只能使用<xref:System.Runtime.Serialization.XmlObjectSerializer>子類別 (<xref:System.Runtime.Serialization.DataContractSerializer>並<xref:System.Runtime.Serialization.NetDataContractSerializer>，而非<xref:System.Xml.Serialization.XmlSerializer>)，或甚至被硬式編碼為只使用<xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 `XmlSerializer` 是在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務中使用的序列化引擎。 `DataContractSerializer` 是了解新資料合約程式設計模型的新序列化引擎。 `DataContractSerializer` 是預設選擇，並選擇来使用`XmlSerializer`可根據每個作業使用<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A>屬性。  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 並<xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>負責作業行為插入訊息格式器，如`DataContractSerializer`而`XmlSerializer`分別。 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 行為實際上能夠與任何衍生自 <xref:System.Runtime.Serialization.XmlObjectSerializer>的序列化程式共同運作，其中包含 <xref:System.Runtime.Serialization.NetDataContractSerializer> (在「使用獨立序列化」中會詳細描述)。 行為會呼叫其中一個 `CreateSerializer` 虛擬方法多載以取得序列化程式。 若要插入不同的序列化程式，請建立新的 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 子類別，然後同時覆寫 `CreateSerializer` 多載。  
  
## <a name="see-also"></a>另請參閱

- [指定服務合約中的資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
