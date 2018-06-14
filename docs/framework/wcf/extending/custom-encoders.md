---
title: 自訂編碼器
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: ae3904af83452dd76723abb78a7a06fdb0f798cc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809273"
---
# <a name="custom-encoders"></a>自訂編碼器
本主題討論如何建立自訂編碼器。  
  
 在 Windows Communication Foundation (WCF) 中，使用*繫結*來指定如何跨網路在端點之間傳輸資料。 繫結由一系列所組成*繫結項目*。 繫結包含選擇性通訊協定繫結項目，例如安全性、 必要*訊息編碼器*繫結項目和必要的傳輸繫結項目。 訊息編碼器是由訊息編碼繫結項目表示。 在 WCF 中包含三種訊息編碼器： 二進位、 訊息傳輸最佳化機制 (MTOM) 和文字。  
  
 訊息編碼繫結項目會序列化傳出的 <xref:System.ServiceModel.Channels.Message> 並將它傳遞至傳輸，或者從傳輸接收序列化形式的訊息，如果有通訊協定層，就將訊息傳遞給它，如果不存在，則傳遞給應用程式。  
  
 訊息編碼器會進行 <xref:System.ServiceModel.Channels.Message> 執行個體與網路傳輸表示之間的相互轉換。 雖然一般描述編碼器在通道堆疊中的位置是在傳輸層之上，但卻是在傳輸層之內。 傳輸 (例如，HTTP) 會根據傳輸標準的需求將訊息格式化。 編碼器 (例如，文字 XML) 則只是對訊息進行編碼。  
  
 當連接到已經存在的用戶端或伺服器時，可能由不得您選擇使用特定的訊息編碼。 不過，WCF 服務可透過多個端點，各有不同的訊息編碼器。 當單一編碼器的輸送量無法涵蓋服務的整個使用群時，請考慮透過多個端點公開您的服務。 然後，用戶端應用程式便可以選擇最適用的端點。 使用多個端點可讓您將各種不同訊息編碼器的優點與其他繫結項目相結合。  
  
## <a name="system-provided-encoders"></a>系統提供的編碼器  
 WCF 提供數種系統提供繫結為配合一些最常見的應用程式案例所設計。 這些繫結程序中的每一個都結合了傳輸、訊息編碼器和其他選項 (例如，安全性)。 本主題說明如何擴充`Text`， `Binary`，和`MTOM`訊息編碼器會包含在 WCF 中，或建立您自己的自訂編碼器。 文字訊息編碼器同時支援純 XML 編碼及 SOAP 編碼。 文字訊息編碼器的純 XML 編碼模式稱為 POX ("Plain Old XML") 編碼器，與文字為主的 SOAP 編碼有所區別。  
  
 如需系統提供的繫結所提供的繫結項目組合的詳細資訊，請參閱中的對應區段[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。  
  
## <a name="how-to-work-with-system-provided-encoders"></a>如何使用系統提供的編碼器  
 您可以使用衍生自 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 的類別，將編碼方式加入至繫結。  
  
 WCF 會提供下列類型的繫結項目衍生自<xref:System.ServiceModel.Channels.MessageEncodingBindingElement>可以提供文字、 二進位和訊息傳輸最佳化機制 (MTOM) 編碼的類別：  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>：互通性最佳、但效率最差的 XML 訊息編碼器。 Web 服務或 Web 服務用戶端通常可以瞭解文字 XML。 不過，將大型二進位資料區塊當做文字來傳輸是沒有效率的。  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>：表示繫結項目，這個繫結項目會指定用於二進位 XML 訊息的字元編碼和訊息版本處理。 這是最有效率的編碼方式的選項，但至少有互通的因為它只支援由 WCF 端點。  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>： 表示繫結項目，指定的字元編碼和訊息版本處理，用於使用訊息傳輸最佳化機制 (MTOM) 編碼的訊息。 MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。 MTOM 編碼器會嘗試在效率和互通性之間保持平衡。 MTOM 編碼方式會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成文字)，好讓這些資料最佳化。  
  
 繫結項目會建立二進位、MTOM 或文字的 <xref:System.ServiceModel.Channels.MessageEncoderFactory>。 處理站會建立二進位、MTOM 或文字的 <xref:System.ServiceModel.Channels.MessageEncoderFactory> 執行個體。 一般而言，只會有一個執行個體。 不過，如果是使用工作階段，就可以提供不同的編碼器給每個工作階段。 二進位編碼器會利用這種方式來協調動態字典 (請參閱＜XML 基礎結構＞)。  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> 和 <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> 方法是編碼器的核心。 這些方法會提供從資料流或 <xref:System.Byte> 陣列讀取訊息的功能。 當傳輸在緩衝模式中運作時，會使用位元組陣列。 訊息一定會寫入資料流。 如果傳輸必須緩衝訊息，就會提供執行緩衝處理的資料流。  
  
 其他成員則會使用支援內容、媒體類型和 <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>。 傳輸會呼叫這些編碼器方法來測試是否可以藉此解碼傳入的訊息，或者判斷傳出的訊息是否對此編碼器為有效。  
  
 這三個編碼器實作中的每一個都會新增與特定編碼有關的屬性，而且是完全可設定的。 這些編碼器也會公開具有安全預設值的讀取器配額。 如需配額的詳細討論，請參閱＜XML 基礎結構＞。  
  
## <a name="features-of-system-provided-encoders"></a>系統提供之編碼器的功能  
 系統提供的編碼器具有許多功能。  
  
### <a name="pooling"></a>Pooling  
 每個編碼器實作都會盡可能嘗試集中共用。 減少配置是改善 Managed 程式碼效能的主要方法。 為了達成這種共用，這些實作會使用 `SynchronizedPool` 類別。 C# 檔案包含這個類別使用的其他最佳化方法的描述。  
  
 為了避免替每一個訊息配置新的 `XmlDictionaryReader` 和 `XmlDictionaryWriter` 執行個體，編碼器會共用並重新初始化這些執行個體。 對於讀取器，會在呼叫 `OnClose` 時由 `Close()` 回呼取回讀取器。 編碼器也會回收建構訊息時使用的某些訊息狀態物件。 您可以在三個衍生自 `MaxReadPoolSize` 的每一個類別上，透過其 `MaxWritePoolSize` 和 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 屬性來設定這些集區的大小。  
  
### <a name="binary-encoding"></a>二進位編碼方式  
 當二進位編碼使用工作階段時，必須將動態字典字串傳達至訊息的接收者。 做法是在訊息前面加上動態字典字串。 接收者會剝取這些字串，然後將它們加入至工作階段，再處理訊息。 為了正確傳遞字典字串，傳輸需要獲得緩衝。  
  
 內部的 `AddSessionInformationToMessage` 方法會將字串附加至訊息。 它會將 UTF-8 格式的字串新增到訊息前頭並加上這些字串的長度， 然後在整個字典標頭前面加上其資料的長度。 內部的 `ExtractSessionInformationFromMessage` 方法則會執行反向作業。  
  
 除了處理動態字典索引鍵之外，還會以獨特的方式來接收緩衝的工作階段訊息。 二進位編碼器並非在文件上建立讀取器，然後加以處理，而是使用內部的 `MessagePatterns` 類別來拆解二進位資料流。 這個概念是，大部分的訊息有特定的一組以特定順序由 WCF 所產生時顯示的標頭。 模式系統會根據其需求分解訊息。 如果分解成功，這個系統就會將 <xref:System.ServiceModel.Channels.MessageHeaders> 物件初始化，而不剖析 XML。 如果失敗，則退而求其次，使用標準的方法。  
  
### <a name="mtom-encoding"></a>MTOM 編碼方式  
 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> 類別具有其他組態屬性呼叫 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`。MaxBufferSize %2a >。 這個屬性可以設定允許繫結項目在讀取訊息過程中緩衝資料數量的上限。 可能需要將 XML 資訊集 (Infoset) 或其他 MIME 部分加以緩衝，才能將所有 MIME 部分重組成單一訊息。  
  
 為能搭配 HTTP 而正常運作，內部 MTOM 訊息編碼器類別提供了一些適用於 `GetContentType` (同樣是內部的) 和 `WriteMessage` (公用的且可覆寫) 的內部 API。 編碼器必須進行更多的通訊，才能確保 HTTP 標頭中的值與 MIME 標頭中的值一致。  
  
 就內部而言，MTOM 訊息編碼器會使用 WCF 的文字讀取器，並與文字編碼器相似。 但是有所不同，主要差異在於最佳化大型二進位區塊 (即「二進位大型物件」(BLOB)) 的方式；在這些區塊嵌入至訊息位元組之前，MTOM 訊息編碼器並不會將它們轉換為 Base-64 編碼， 而是讓這些 BLOB 繼續以未經壓縮的狀態存在，並且將它們當做 MIME 附件來參考。  
  
## <a name="writing-your-own-encoder"></a>撰寫您自己的編碼器  
 若要實作您自己的自訂訊息編碼器，您必須提供下列抽象基底類別的自訂實作：  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 訊息由「記憶體中」表示變成「可寫入至資料流」表示的轉換功能是封裝在 <xref:System.ServiceModel.Channels.MessageEncoder> 類別中，這個類別可以當做支援特定類型 XML 編碼之 XML 讀取器和 XML 寫入器的處理站使用。  
  
-   在這個類別中，您必須加以覆寫的主要方法如下：  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>，這個方法會接受 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 物件，並將它寫入至 <xref:System.IO.Stream> 物件。  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>，這個方法會接受 <xref:System.IO.Stream> 物件和最大標頭大小，然後傳回 <xref:System.ServiceModel.Channels.Message> 物件。  
  
 在處理標準傳輸通訊協定與自訂編碼之間轉換的這些方法中，它就是您要撰寫的程式碼。  
  
 接下來，您必須針對建立自訂編碼器的處理站類別編寫程式碼。 覆寫 <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A>，以傳回自訂 <xref:System.ServiceModel.Channels.MessageEncoder> 的執行個體。  
  
 最後，覆寫 <xref:System.ServiceModel.Channels.MessageEncoderFactory> 方法以傳回這個處理站的執行個體，讓自訂的 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> 連接到用於設定服務或用戶端的繫結項目堆疊。  
  
 有兩個範例使用 WCF 提供可說明此程序範例程式碼：[自訂訊息編碼器： 自訂文字編碼器](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md)和[自訂訊息編碼器： 壓縮編碼器](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [資料傳輸架構概觀](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [選擇訊息編碼器](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
