---
title: 選擇訊息交換模式
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 7dcbea30b53142ed68db9ac138f8c7a665ca1729
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797299"
---
# <a name="choosing-a-message-exchange-pattern"></a>選擇訊息交換模式
撰寫自訂傳輸的第一個步驟，是決定您要開發的通道需要哪些*訊息交換模式*（或 mep）。 本主題會說明可用的選項，並討論各種需求。 這是[開發通道](developing-channels.md)中所述的通道開發工作清單中的第一個工作。  
  
## <a name="six-message-exchange-patterns"></a>六種訊息交換模式  
 您可以從三個 MEP 中選擇：  
  
- 資料包 (<xref:System.ServiceModel.Channels.IInputChannel> 和 <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     使用資料包 MEP 時，用戶端會使用火災來傳送訊息，*而*不會發出交換。 射後不理交換是一種需要以超出範圍之外的方式確認傳遞成功的交換。 訊息可能會在傳輸時遺失而永遠無法抵達服務。 即使傳送作業在用戶端已成功完成，也無法保證遠端端點已接收到該訊息。 資料包是訊息的基本建置組塊，您可以在資料包的最上層建立自己的通訊協定，其中包括可靠的通訊協定和安全的通訊協定。 用戶端資料包通道會實作 <xref:System.ServiceModel.Channels.IOutputChannel> 介面，服務資料包通道則會實作 <xref:System.ServiceModel.Channels.IInputChannel> 介面。  
  
- 要求-回應 (<xref:System.ServiceModel.Channels.IRequestChannel> 和 <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     在此 MEP 中，會傳送訊息，而且會接收回覆。 此模式是由要求-回應組合所構成。 遠端程序呼叫 (Remote Procedure Call，RPC) 與瀏覽器 GET 要求就是要求-回應呼叫的例子。 這個模式又稱為半雙工。 在此 MEP 中，用戶端通道會實作 <xref:System.ServiceModel.Channels.IRequestChannel>，服務通道則會實作 <xref:System.ServiceModel.Channels.IReplyChannel>。  
  
- 雙工 (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     雙工 MEP 會允許用戶端傳送任意數目的訊息，並以任何順序接收這些訊息。 雙工 MEP 就像是電話交談，談話中說出的每個字都是一則訊息。 由於兩端都可以透過此種 MEP 來傳送和接收訊息，所以由用戶端和服務通道所實作的介面會是 <xref:System.ServiceModel.Channels.IDuplexChannel>。  
  
 ![選擇訊息交換模式](./media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
三個基本訊息交換模式。 從上到下：資料包、要求-回應及雙工。  
  
 這些 Mep 中的每一個也可以支援*會話*。 工作階段 (以及 <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> 型別的 <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType> 實作) 會使在通道中傳送與接收的所有訊息相互關聯。 要求-回應模式是獨立的兩個訊息工作階段，因為要求與回覆是相互關聯的。 相較之下，支援工作階段的要求-回應模式，則表示在通道上的所有要求/回應組合都與彼此相互關聯。 這樣您就可以從總計六個的 MEP 中進行選擇：  
  
- 資料包  
  
- 要求-回應  
  
- 雙工  
  
- 搭配工作階段的資料包  
  
- 搭配工作階段的要求-回應  
  
- 搭配工作階段的雙工  
  
> [!NOTE]
> 若是 UDP 傳輸，唯一支援的 MEP 是資料包，因為 UDP 原本就是射後不理 (Fire and Forget) 通訊協定。  
  
## <a name="sessions-and-sessionful-channels"></a>工作階段和工作階段通道  
 在網路世界中有連線導向的通訊協定 (例如 TCP)，以及無連線的通訊協定 (例如 UDP)。 WCF 使用「會話」一詞來表示類似連接的邏輯抽象概念。 工作階段 WCF 通訊協定類似連線導向的網路通訊協定，而無工作階段的 WCF 通訊協定類似無連線的網路通訊協定。  
  
 在通道物件模型中，每個邏輯工作階段都會顯示為工作階段通道的執行個體。 因此，由用戶端建立並由服務接受的每個新工作階段，都會對應到每一端上的新工作階段通道。 下圖的最上方顯示出無工作階段通道的結構，而下方則顯示工作階段通道的結構。  
  
 ![選擇訊息交換模式](./media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 用戶端會建立新的工作階段通道並傳送訊息。 在服務端上，通道接聽程式會接收此訊息，並偵測到該訊息屬於新的工作階段，因此它會建立新的工作階段通道，並會將其交給應用程式 (以回應在通道接聽程式上呼叫 AcceptChannel 的應用程式)。 接著，應用程式便會接收此訊息，以及所有透過該相同工作階段通道傳送的後續訊息。  
  
 另一個用戶端 (或是相同的用戶端) 會建立新的工作階段並傳送訊息。 通道接聽程式會偵測出此訊息是存在於新的工作階段並建立新的工作階段通道，並重複這個程序。  
  
 若是沒有工作階段，通道與工作階段之間就不會有任何相互關聯。 因此，通道接聽程式只會建立一個所有已接收訊息都要透過其中以傳遞到應用程式的通道。 由於沒有用來維持訊息順序的工作階段，所以，這時並不進行訊息排序。 上圖的最上方說明了無工作階段的訊息交換。  
  
## <a name="starting-and-terminating-sessions"></a>啟動和終止工作階段  
 只要建立新的工作階段通道，即可在用戶端上啟動工作階段。 當服務接收到在新工作階段中傳送的訊息時，這些工作階段便會在服務上啟動。 同樣的，關閉或中止工作階段通道便會使工作階段終止。  
  
 這種情況的例外是 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>，這種通道會用來在雙工的工作階段通訊模式中同時傳送和接收訊息。 有時會出現某一端希望停止傳送訊息但繼續接收訊息的情況，這時若是使用 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 便可提供一個機制，讓您能夠關閉輸出工作階段以表示您將不會傳送任何訊息，但是又使輸入工作階段維持開啟來讓您繼續接收訊息。  
  
 一般而言，工作階段是在傳出端上被關閉，而不是在傳入端上。 也就是說，工作階段輸出通道可以被關閉，並進而正常地終止工作階段。 關閉工作階段輸出通道，會造成對應的工作階段輸入通道將 null 傳回給在 <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 的應用程式。  
  
 不過，除非 <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 傳回 null 以表示工作階段已關閉，否則，應該不要關閉工作階段輸入通道。 如果 <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 沒有傳回 null，這時關閉工作階段輸入通道時可能會擲回例外狀況，因為該通道可能會在關閉時收到未預期的訊息。 如果接收端希望在傳送端終止工作階段之前先行終止，它就應該在輸入通道上呼叫 <xref:System.ServiceModel.ICommunicationObject.Abort%2A>，如此就會立即終止該工作階段。  
  
## <a name="writing-sessionful-channels"></a>撰寫工作階段通道  
 身為工作階段通道作者，您的通道必須進行一些動作才能提供工作階段。 在傳送端上，您的通道必須執行下列動作：  
  
- 對於每個新通道，建立新的工作階段，並使這個工作階段與屬於唯一字串的新工作階段識別碼產生關聯。 或是從堆疊中低於您的工作階段通道中，取得新的工作階段。  
  
- 對於使用這個通道傳送的每則訊息，如果工作階段是由您的通道建立 (而非從低於您的通道層中取得此工作階段)，您就需要使訊息與此工作階段產生關聯。 若是通訊協定通道，通常是新增 SOAP 標頭來做到這點。 若是傳輸通道，通常是建立新傳輸連線、或是將工作階段資訊新增到框架處理通訊協定來做到這點。  
  
- 對於使用這個通道傳送的每則訊息，您必須提供上述的傳遞保證。 如果您是依賴在您之下的通道來提供工作階段，該通道也將會提供傳遞保證。 如果您是自己提供工作階段，您就必須實作這些保證以做為通訊協定的一部分。 一般而言，如果您要撰寫假設兩端都有 WCF 的通訊協定通道，您可能會需要 TCP 傳輸或可信賴傳訊通道，並依賴其中一種來提供工作階段。  
  
- 當某一端在您的通道上呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> 時，執行必要的工作來關閉使用指定或預設逾時的工作階段。 這點就像在您以下的通道呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A> (如果只從其中取得工作階段)、傳送特殊的 SOAP 訊號，或是關閉傳輸連線一樣簡單。  
  
- 當某一端在您的通道上呼叫 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> 時，立即終止工作階段而不執行 I/O。 這可能表示不進行任何動作，或是牽涉到中止網路連線或其他一些資源。  
  
 在接收端上，您的通道必須執行下列動作：  
  
- 對於每則傳入訊息，通道接聽程式都必須偵測其所屬於的工作階段。 如果這是工作階段中的第一則訊息，通道接聽程式就必須建立新的通道，並從對 <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> 的呼叫將其傳回。 否則，通道接聽程式就必須找到對應至該工作階段的現有通道，並透過該通道傳遞訊息。  
  
- 如果您的通道會提供工作階段 (以及必要的傳遞保證)，接收端就可能需要執行一些動作，像是重新排列訊息或傳送認可。  
  
- 當某一端在您的通道上呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A> 時，執行必要的工作來關閉使用指定或預設逾時的工作階段。 如果通道在等候關閉逾時到期的期間收到訊息，這時可能會造成例外狀況。 這是因為通道在收到訊息時將是處於 Closing 狀態，所以可能會擲回例外狀況。  
  
- 當某一端在您的通道上呼叫 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> 時，立即終止工作階段而不執行 I/O。 同樣地，這可能表示不進行任何動作，或是牽涉到中止網路連線或其他一些資源。  
  
## <a name="see-also"></a>另請參閱

- [通道模型概觀](channel-model-overview.md)
