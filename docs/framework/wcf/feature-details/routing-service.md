---
title: 路由服務
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 905c84d801a27e588e2c539f987d6280aae7b994
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129437"
---
# <a name="routing-service"></a>路由服務
「路由服務」是一種泛型 SOAP 媒介，可做為訊息路由器。 路由服務的核心功能是可根據訊息內容傳送訊息的能力，這可讓訊息根據訊息 (不論是標頭或訊息本文) 內部本身的值轉送至用戶端端點。  
  
 <xref:System.ServiceModel.Routing.RoutingService>實作為 Windows Communication Foundation (WCF) 服務中<xref:System.ServiceModel.Routing>命名空間。 路由服務會公開一個或多個接收訊息的服務端點，然後將每則訊息根據訊息內容傳送至一個或多個用戶端端點。 服務提供下列功能：  
  
-   以內容為基礎的路由  
  
    -   服務彙總  
  
    -   服務版本控制  
  
    -   優先權路由  
  
    -   動態組態  
  
-   通訊協定橋接  
  
-   SOAP 處理  
  
-   進階的錯誤處理  
  
-   備份端點  
  
 雖然您可以建立媒介服務來完成一或多項上述目標，但是這類實作經常與特定案例或方案關係密切，而且無法輕易套用至新應用程式。  
  
 路由服務提供的泛型、 可動態設定、 可外掛式 SOAP 媒介，與 WCF 服務和通道模型相容，並可讓您執行的 SOAP 架構訊息內容型路由。  
  
> [!NOTE]
>  路由服務目前不支援 WCF REST 服務的路由。  若要路由傳送 REST 呼叫，請考慮使用<xref:System.Web.Routing>或是[應用程式要求路由](https://go.microsoft.com/fwlink/?LinkId=164589)。  
  
## <a name="content-based-routing"></a>內容架構路由  
 內容架構路由是根據訊息內包含的一個或多個值路由傳送訊息的能力。 路由服務會檢查每一個訊息，並且根據訊息內容和您建立的路由邏輯，將訊息路由傳送至目的端點。 以內容為基礎的路由會提供服務彙總、服務版本控制和優先權路由的基礎。  
  
 為了實作以內容為基礎的路由，路由服務需依靠 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作，該實作是用來比對要傳送之訊息內的特定值。 如果**MessageFilter**訊息，訊息會路由傳送至目的地端點相關聯的相符項目**MessageFilter**。  訊息篩選會群組至篩選資料表中 (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) 以建構複雜路由邏輯。 例如，篩選資料表可能包含五個相互為獨佔的訊息篩選條件，這些篩選條件會導致訊息僅傳送至五個目的地端點的其中之一。  
  
 路由服務可讓您設定用來執行以內容為基礎之路由的邏輯，以及在執行階段動態更新路由邏輯。  
  
 將訊息篩選條件群組為篩選資料表，可建構路由邏輯，讓您處理多個路由案例，例如：  
  
-   服務彙總  
  
-   服務版本控制  
  
-   優先權路由  
  
-   動態組態  
  
 如需有關訊息篩選條件和篩選資料表的詳細資訊，請參閱[路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)並[訊息篩選條件](../../../../docs/framework/wcf/feature-details/message-filters.md)。  
  
### <a name="service-aggregation"></a>服務彙總  
 透過使用以內容為基礎的路由，您就可以公開從外部用戶端應用程式接收訊息的端點，然後根據訊息內的值，將每個訊息路由傳送至適當的內容端點。 這項益處相當實用，可提供一個特定端點給各種不同的後端應用程式，以及對客戶呈現一個應用程式端點，同時將應用程式重構至各種不同服務。  
  
### <a name="service-versioning"></a>服務版本控制  
 當您轉換新版方案時，可能需要保留舊版，以便同時對現有客戶提供服務。 在這種情況下，經常會要求連接至較新版本的用戶端與方案進行通訊時，必須使用不同的位址。 路由服務可讓您根據訊息中包含的版本專屬資訊，將訊息路由傳送至適當的方案，藉此公開一個同時對兩個方案版本提供服務的服務端點。 如需這類實作的範例，請參閱[How To:服務版本設定](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)。  
  
### <a name="priority-routing"></a>優先權路由  
 為多個用戶端提供服務時，您可能與某些夥伴有服務等級協定 (SLA)，該協定會要求來自這些夥伴的所有資料與其他用戶端的資料分開處理。 透過使用尋找訊息內所包含客戶專屬資訊的篩選，您就可以輕鬆將特定夥伴的訊息路由傳送至專為符合其 SLA 需求所建立的端點。  
  
## <a name="dynamic-configuration"></a>動態組態  
 為了支援重要的運作系統，訊息的處理過程不能有任何服務中斷，因此您必須能在執行階段於系統內修改元件組態。 為了支援這項需求，路由服務提供 <xref:System.ServiceModel.IExtension%601> 實作，也就是 <xref:System.ServiceModel.Routing.RoutingExtension>，可讓路由服務組態在執行階段進行動態更新。  
  
 如需路由服務的動態組態的詳細資訊，請參閱[路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)。  
  
## <a name="protocol-bridging"></a>通訊協定橋接  
 媒介案例的其中一項挑戰，就是內部端點的傳輸或 SOAP 版本需求可能與接收訊息所在的端點不同。 為了支援此案例，路由服務可以橋接通訊協定，包括將 SOAP 訊息處理至目的端點所需的 <xref:System.ServiceModel.Channels.MessageVersion>。 透過這種方式，就可以將一個通訊協定用於內部通訊，同時將另一個通訊協定用於外部通訊。  
  
 為了支援端點間使用不同傳輸的訊息傳送，路由服務會使用系統提供的繫結，讓服務能夠橋接不同的通訊協定。 當路由服務所公開的服務端點，使用與用戶端端點 (訊息傳送的位置) 不同的通訊協定時，此情形便會自動發生。  
  
## <a name="soap-processing"></a>SOAP 處理  
 使用不同 SOAP 需求在端點間路由訊息是一項常見的傳送需求。 若要支援這項需求，路由服務提供<xref:System.ServiceModel.Routing.SoapProcessingBehavior>，可自動建立新**MessageVersion**之前將訊息路由至符合的目的地端點需求。 此行為也會建立新**MessageVersion**任何回應訊息，然後再回到提出要求的用戶端應用程式，以確保**MessageVersion**回應符合原始的要求。  
  
 如需有關 SOAP 處理的詳細資訊，請參閱 <<c0> [ 路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)。  
  
## <a name="error-handling"></a>錯誤處理  
 在由依賴網路通訊之分散式服務所組成的系統中，確定系統內部通訊不會發生暫時性網路故障是相當重要的。  路由服務會實作錯誤處理，讓您能夠處理許多可能會導致服務中斷的通訊故障案例。  
  
 如果路由服務在嘗試傳送訊息時發生 <xref:System.ServiceModel.CommunicationException> 情況，錯誤處理便會開始。  這些例外狀況通常表示，嘗試與定義的用戶端端點 (如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>) 進行通訊時發生問題。  錯誤處理程式碼也會攔截並嘗試重新傳送的時機**TimeoutException**發生時，這是另一個常見的例外狀況不衍生自**CommunicationException**。  
  
 如需有關錯誤處理的詳細資訊，請參閱[路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)。  
  
## <a name="backup-endpoints"></a>備份端點  
 除了篩選資料表中與每個篩選定義關聯的目的地用戶端端點之外，您也可以建立備份端點清單，在傳輸失敗時傳送訊息至該端點。 如果錯誤發生且備份清單是用於篩選項目，路由服務便會嘗試將訊息傳送至已在清單中定義的第一個端點。 如果此次傳輸失敗，服務會嘗試下一個端點並繼續此程序，直到傳輸成功、傳回非傳輸相關的錯誤，或備份清單中的所有端點已傳回傳輸錯誤。  
  
 如需有關備份端點的詳細資訊，請參閱 <<c0> [ 路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)並[訊息篩選條件](../../../../docs/framework/wcf/feature-details/message-filters.md)。  
  
## <a name="streaming"></a>資料流  
 如果您將繫結設定為支援資料流，路由服務就可以成功地串流處理訊息。  不過，在某些情況下，您可能必須緩衝處理訊息：  
  
-   多點傳送 (緩衝處理以建立其他訊息複本)  
  
-   容錯移轉 (如果訊息必須傳送至備份，則緩衝處理)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly 為 false (緩衝處理以呈現含有 MessageBuffer 的 MessageFilterTable，讓篩選能夠檢查本文)  
  
-   動態組態  
  
## <a name="see-also"></a>另請參閱

- [路由簡介](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
- [路由合約](../../../../docs/framework/wcf/feature-details/routing-contracts.md)
- [訊息篩選](../../../../docs/framework/wcf/feature-details/message-filters.md)
