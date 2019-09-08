---
title: 通道模型概觀
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 362a7392d9dbaedb1942280a6c3b6c8f2139afe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795896"
---
# <a name="channel-model-overview"></a>通道模型概觀
Windows Communication Foundation （WCF）通道堆疊是一種分層通訊堆疊，其中包含一或多個處理訊息的通道。 堆疊底部為傳輸通道，其負責針對基礎傳輸進行調整 (例如，TCP、HTTP、SMTP 和其他的傳輸類型)。 通道會提供低階的程式設計模型來傳送及接收訊息。 這個程式設計模型依賴數個介面和其他類型，統稱為 WCF 通道模型。 本主題將討論通道形狀、建構基本通道接聽程式 (在服務上) 以及通道處理站 (在用戶端上)。  
  
## <a name="channel-stack"></a>通道堆疊  
 WCF 端點會使用稱為通道堆疊的通訊堆疊與世界通訊。 下列圖表比較通道堆疊與其他的通訊堆疊，例如 TCP/IP。  
  
 ![通道模型](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 首先，相似之處：在這兩種情況下，堆疊的每個層級都會在該層的下方提供一些抽象概念，並只向其上方的層公開該抽象化。 每一層只會使用其下方一層的抽象概念。 此外，在這兩種情況下，當兩個堆疊通訊時，每一層都會與另一個堆疊中的對應層進行通訊，例如 IP 層會與 IP 層通訊，而 TCP 層則與 TCP 層通訊，以此類推。  
  
 現在的差異如下：雖然 TCP 堆疊的設計目的是要提供實體網路的抽象概念，但通道堆疊的設計目的是要提供不僅傳遞訊息的方式，也就是傳輸，還有其他功能，例如訊息中的內容或通訊協定是用來進行通訊，包括傳輸，但遠多於這種情況。 例如，可靠工作階段繫結項目就屬於通道堆疊的一部分，但其並不在傳輸下層，也不是傳輸本身。 要求堆疊中的底部通道將基礎的傳輸通訊協定調整為通道堆疊架構，接著依賴堆疊中的上一個通道提供通訊功能，例如可靠性保證和安全性，便可完成這個抽象概念。  
  
 訊息會以 <xref:System.ServiceModel.Channels.Message> 物件的狀態流經通訊堆疊。 如上圖所示，底部通道稱為傳輸通道。 這就是負責與其他端點來回傳送及接收訊息的通道。 這個通道的責任包括將 <xref:System.ServiceModel.Channels.Message> 物件來回轉換為與其他端點進行通訊時所使用的格式。 傳輸通道上方可以有任意數目的通訊協定通道，而其中每個通道都負責提供一項通訊功能，例如可靠的傳遞保證。 通訊協定通道會針對以 <xref:System.ServiceModel.Channels.Message> 物件格式流經其中的訊息執行動作。 這些通道通常會轉換訊息 (例如，以新增標頭或將內文加密的方式)，或是傳送及接收它們自己的通訊協定控制訊息 (例如，回條認可)。  
  
## <a name="channel-shapes"></a>通道形狀  
 每個通道都會實作一個或多個介面，而這些介面即稱為通道形狀介面或通道形狀。 這些通道形狀會提供通訊導向的方法，例如，通道所實作以及通道使用者所呼叫的傳送及接收或是要求及回覆。 「通道」圖形的基底是<xref:System.ServiceModel.Channels.IChannel>介面，它是`GetProperty` \<提供 T > 方法的介面，以做為分層機制來存取堆疊中的通道所公開的任意功能。 延伸自 <xref:System.ServiceModel.Channels.IChannel> 的五種通道形狀為：  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 此外，其中每一個形狀都有延伸自 <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> 而可支援工作階段的對等形狀。 這些是：  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 通道形狀會仿效現有傳輸通訊協定所支援的某些基本訊息交換模式來建立模式。 例如，單向<xref:System.ServiceModel.Channels.IInputChannel>訊息對應至一/ <xref:System.ServiceModel.Channels.IOutputChannel>組，要求-回復會對應<xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IRequestChannel> /至配對，而雙向雙工通訊則對應至<xref:System.ServiceModel.Channels.IDuplexChannel>（這會擴充<xref:System.ServiceModel.Channels.IInputChannel>和<xref:System.ServiceModel.Channels.IOutputChannel>）。  
  
## <a name="programming-with-the-channel-stack"></a>使用通道堆疊進行程式設計  
 通道堆疊通常是使用處理站模式所建立，在此種模式中，繫結程序會建立通道堆疊。 在傳送端上，繫結會用來建置 <xref:System.ServiceModel.ChannelFactory>，而此處理站會接著建置通道堆疊，並傳回在堆疊中頂端通道的參考。 應用程式可以接著使用這個通道來傳送訊息。 如需詳細資訊，請參閱[用戶端通道層級的程式設計](client-channel-level-programming.md)。  
  
 在接收端上，繫結會用來建置 <xref:System.ServiceModel.Channels.IChannelListener>，而此接聽項會接聽傳入訊息。 <xref:System.ServiceModel.Channels.IChannelListener> 會透過建立通道堆疊並將應用程式參考傳遞至頂端通道的方式，來提供訊息給接聽應用程式。 應用程式可以接著使用這個通道來接收傳入訊息。 如需詳細資訊，請參閱[服務通道層級的程式設計](service-channel-level-programming.md)。  
  
## <a name="the-channel-object-model"></a>通道物件模型  
 通道物件模型是在實作通道、通道接聽程式和通道處理站時所需要的介面核心集。 同時也提供了一些可協助進行自訂實作的基底類別 (Base Class)。  
  
 通道接聽程式負責接聽傳入訊息，並接著透過此通道接聽程式所建立的通道，將這些訊息傳遞至上一層。  
  
 通道處理站負責建立的通道會用於傳送訊息，以及用於關閉在通道處理站關閉時所建立的所有通道。  
  
 <xref:System.ServiceModel.ICommunicationObject> 為核心介面，它會定義所有通訊物件所實作的基本狀態機器。 <xref:System.ServiceModel.Channels.CommunicationObject> 會提供此核心介面的實作，這樣其他通道類別就可以從這個實作衍生，而不需重新實作該介面。 但是，這不並是規定方式。自訂通道可以直接實作 <xref:System.ServiceModel.ICommunicationObject>，而不用從 <xref:System.ServiceModel.Channels.CommunicationObject> 繼承。 圖 3 中的所有類別都不是通道模型的一部分；這些類別是想要建置通道之自訂通道實作器可使用的協助程式。  
  
 ![通道模型](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 下列主題會說明通道物件模型，以及有助於建置自訂通道的各種開發區域。  
  
|主題|描述|  
|-----------|-----------------|  
|[維護通道接聽程式和通道](service-channel-listeners-and-channels.md)|說明通道接聽程式，此接聽項會接聽服務應用程式中的傳入通道。|  
|[台通道處理站和通道](client-channel-factories-and-channels.md)|說明通道處理站，此處理站會建立可連接至服務應用程式的通道。|  
|[了解狀態變更](understanding-state-changes.md)|說明 <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> 介面模型狀態在通道中的變更方式。|  
|[選擇訊息交換模式](choosing-a-message-exchange-pattern.md)|說明通道可支援的六種基本訊息交換模式。|  
|[處理例外狀況和失敗](handling-exceptions-and-faults.md)|說明如何處理在自訂通道中的錯誤和例外狀況。|  
|[組態與中繼資料支援](configuration-and-metadata-support.md)|說明如何支援從應用程式模型使用自訂通道，以及如何使用繫結和繫結項目來匯出及匯入中繼資料。|
