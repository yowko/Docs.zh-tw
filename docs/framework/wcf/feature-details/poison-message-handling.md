---
title: 有害訊息處理
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: b860e239d001a03da191d73de2f7b53e7073c7a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496464"
---
# <a name="poison-message-handling"></a>有害訊息處理
A*有害訊息*是超過嘗試傳遞至應用程式的最大數目的訊息。 這種情形可能會在佇列架構的應用程式因為錯誤而無法處理訊息時發生。 為了符合可靠性的需求，佇列的應用程式會在交易中接收訊息。 若中止了接收佇列訊息的交易，則會讓訊息留在佇列中，而訊息將會在新的交易中重試。 如果造成交易中止的問題未予以更正，則接收的應用程式可能會卡在接收及中止相同訊息的迴圈中，直到超過傳遞嘗試次數的上限為止，因而形成有害訊息。  
  
 訊息變成有害訊息的原因有許多種。 最常見的原因是在應用程式中所發生的特定原因。 例如，如果應用程式從佇列讀取訊息，並且執行某些資料庫處理，應用程式可能因為無法在該資料庫上取得鎖定，而造成中止交易。 由於資料庫交易中止，訊息會留在佇列中，造成應用程式再次讀取該訊息，並重新嘗試取得資料庫鎖定。 如果訊息包含無效的資訊，則也可能變成有害的。 例如，採購單可能包含無效的客戶編號。 在這些情況下，應用程式可能自動中止交易，而迫使訊息成為有害訊息。  
  
 在鮮少的情況下，訊息可能會無法分派至應用程式。 Windows Communication Foundation (WCF) 層可能會發現問題的訊息中，例如，如果訊息有錯誤的框架，無效的訊息附加的認證，或是無效的動作標頭。 在這些情況中，應用程式絕不會接收該訊息，不過，訊息仍然可能會變成有害訊息，並且以手動方式處理。  
  
## <a name="handling-poison-messages"></a>處理有害訊息  
 在 WCF 中，有害訊息處理會提供機制來處理無法分派至應用程式的訊息或訊息分派至應用程式，但其無法處理因為特定的應用程式接收的應用程式原因。 有害訊息處理是由每個可用佇列繫結中的以下屬性所設定：  
  
-   `ReceiveRetryCount`。 整數值，表示從應用程式佇列傳遞至應用程式的訊息重試次數上限。 預設值為 5。 這個值對於立即重試即可修正問題的情況來說就已足夠，例如資料庫上發生暫時死結時。  
  
-   `MaxRetryCycles`。 整數值，表示重試週期的上限。 重試週期包含從應用程式佇列將訊息傳輸至重試子佇列，然後在經過一段可設定的延遲之後，再從重試子佇列傳回應用程式佇列，重新嘗試傳遞。 預設值為 2。 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，訊息最多會嘗試 (`ReceiveRetryCount` +1) * (`MaxRetryCycles` + 1) 次。 在 `MaxRetryCycles` 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上則會忽略 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
-   `RetryCycleDelay`。 重試週期之間的時間延遲。 預設值為 30 分鐘。 `MaxRetryCycles` 和 `RetryCycleDelay` 會一起提供解決問題的機制，透過定期延遲之後的重試，進行問題的修正。 例如，這個機制會處理 SQL Server 中所設定等待交易認可的鎖定資料列。  
  
-   `ReceiveErrorHandling`。 列舉型別，指出要針對達到重試次數上限之後，而導致傳遞失敗的訊息所採取的動作。 這個值可以是 Fault、Drop、Reject 和 Move。 預設選項為 Fault。  
  
-   Fault： 這個選項會將錯誤傳送至造成 `ServiceHost` 失敗的接聽項。 訊息必須藉由某種外部機制從應用程式佇列中移除，應用程式才能繼續處理佇列中的訊息。  
  
-   Drop： 這個選項會捨棄有害訊息，而且該訊息永遠不會傳遞至應用程式。 如果訊息的 `TimeToLive` 屬性此時已過期，那麼訊息便可能會出現在傳送者寄不出的信件佇列中。 如果未過期的話，訊息不會出現在任何位置。 這個選項表示，使用者尚未指定訊息遺失時的做法。  
  
-   Reject： 這個選項只在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上提供。 這個選項會指示 Message Queuing (MSMQ) 將負值通知傳回傳送的佇列管理員，說明應用程式無法接收訊息。 訊息會放在傳送的佇列管理員寄不出的信件佇列中。  
  
-   Move： 這個選項只在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上提供。 這個選項會將有害訊息移到有害訊息佇列，以便之後讓有害訊息處理應用程式進行處理。 有害訊息佇列是應用程式佇列的子佇列。 有害訊息處理應用程式可以是從有害佇列中讀取訊息的 WCF 服務。 有害佇列是應用程式佇列的子佇列，並可以定址為 net.msmq://\<*機器名稱*>/*applicationQueue*; poison，其中*電腦名稱*是佇列所在的電腦名稱和*applicationQueue*是應用程式專屬佇列的名稱。  
  
 以下為訊息的嘗試傳遞次數上限：  
  
-   在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上為 ((ReceiveRetryCount+1) * (MaxRetryCycles + 1))。  
  
-   在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上為 (ReceiveRetryCount + 1)。  
  
> [!NOTE]
>  成功傳遞的訊息不會有任何重試次數。  
  
 為了持續追蹤嘗試讀取訊息的次數，[!INCLUDE[wv](../../../../includes/wv-md.md)] 會保留一個計算中止計數之永久訊息屬性，以及另一個移動計數屬性，此屬性會計算訊息在應用程式佇列和子佇列之間移動的次數。 WCF 通道會使用這些屬性計算接收重試次數和重試週期數。 在[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]和[!INCLUDE[wxp](../../../../includes/wxp-md.md)]，中止計數維持在記憶體中的 WCF 通道和應用程式失敗時，會重設。 此外，WCF 通道可以保存在記憶體中的最多 256 個訊息的中止計數在任何時間。 如果讀取第 257 個訊息，那麼最舊訊息的中止計數就會重設。  
  
 中止計數和移動計數屬性可透過作業內容提供給服務作業。 以下程式碼範例將說明如何存取這兩個屬性。  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF 提供兩個標準的佇列繫結：  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]適合用來與其他 WCF 端點的佇列通訊的繫結。  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. 此繫結適合用來與現有的訊息佇列應用程式進行通訊。  
  
> [!NOTE]
>  您可以變更這些 WCF 服務的需求為基礎的繫結中的屬性。 對於接收應用程式而言，整個有害訊息處理機制是在本機上進行的。 傳送應用程式看不到這個程序，除非接收應用程式最後停止並且將負值通知傳回至傳送者。 在這種情況下，訊息會移到傳送者寄不出的信件佇列中。  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>最佳做法：處理 MsmqPoisonMessageException  
 當服務判定訊息是有害時，佇列的傳輸便會擲回 <xref:System.ServiceModel.MsmqPoisonMessageException>，其中包含有害訊息的 `LookupId`。  
  
 接收應用程式可實作 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 介面，以處理應用程式所需的任何錯誤。 如需詳細資訊，請參閱[擴充控制透過錯誤處理和報告](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)。  
  
 應用程式可能需要以某種自動處理的方式將有害訊息移至有害訊息序列，讓服務能夠存取佇列中其餘的訊息。 唯一會使用錯誤處理常式機制接聽有害訊息例外狀況的情況，是在 <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> 設定設為 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> 的時候。 Message Queuing 3.0 的有害訊息範例會示範這種行為。 以下將說明處理有害訊息時所採取的步驟，包括最佳做法：  
  
1.  請確認您的有害設定能反映您應用程式的需求。 處理設定時，務必確實了解 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上訊息佇列功能之間的差異。  
  
2.  如有需要，請實作 `IErrorHandler` 來處理有害訊息錯誤。 由於將 `ReceiveErrorHandling` 設為 `Fault` 時需要使用手動機制將有害訊息從佇列中移出，或更正外部相關的問題，因此通常的使用方式是在 `IErrorHandler` 設為 `ReceiveErrorHandling` 時實作 `Fault`，如下列程式碼中所示。  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  建立服務行為可使用的 `PoisonBehaviorAttribute`。 這個行為會在發送器上安裝 `IErrorHandler`。 請參閱以下程式碼範例。  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  確認您的服務已加上有害行為屬性的註解。  
  
  
  
 此外，如果 `ReceiveErrorHandling` 設為 `Fault`，則 `ServiceHost` 會在遇到有害訊息時發生錯誤。 您可以連結到發生錯誤的事件並關閉服務、採取更正的動作，然後重新啟動。 例如，可以標註傳播至 `LookupId` 的 <xref:System.ServiceModel.MsmqPoisonMessageException> 中的 `IErrorHandler`，當服務主機發生錯誤時，您就可以使用 `System.Messaging` API 接收來自佇列的訊息 (使用 `LookupId` 移除佇列中的訊息)，以及將訊息保存在某些外部儲存區或另一個佇列中。 然後您可以重新啟動 `ServiceHost` 並繼續進行正常處理。 [有害訊息處理 MSMQ 4.0 中](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md)示範此行為。  
  
## <a name="transaction-time-out-and-poison-messages"></a>異動逾時及有害訊息  
 佇列傳輸通道和使用者程式碼之間可能會發生一種類別的錯誤。 這些錯誤可能會在中間的各層中偵測到，例如訊息安全層或服務分派邏輯。 例如，在 SOAP 安全層中偵測到遺失了 X.509 憑證，以及遺失的動作就是訊息會被分派至應用程式的情況。 發生這類情況時，服務模型會捨棄訊息。 由於訊息是在交易中讀取，而且不會提供交易的結果，因此交易最後會逾時、中止，而訊息則會放回佇列中。 換言之，針對特定類別的錯誤，交易不會立即中止，而是會等待直到交易逾時。您可以使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 修改服務的交易逾時。  
  
 若要能在電腦上通用的原則下變更交易逾時，請修改 machine.config 檔案，並且設定適當的交易逾時。要注意的是，交易最後會根據所設定的逾時而中止，並回到佇列中，並且會遞增其中止計數。 最後，訊息會變成有害，並且根據使用者的設定進行正確的處置。  
  
## <a name="sessions-and-poison-messages"></a>工作階段及有害訊息  
 工作階段如同單一訊息一樣，會進行相同的重試和有害訊息處理程序。 先前所列出的有害訊息屬性會套用到整個工作階段。 這表示會重試整個工作階段，而且如果訊息遭拒絕，將移至最後的有害訊息佇列或傳送者寄不出的信件佇列。  
  
## <a name="batching-and-poison-messages"></a>批次處理及有害訊息  
 如果訊息變成有害訊息，而且是批次的一部分，那麼整個批次都會復原，而通道會回到一次讀取一個訊息的狀態。 如需批次處理的詳細資訊，請參閱[異動中批次處理的訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>有害佇列中之訊息的有害訊息處理  
 當訊息放入有害訊息佇列時，有害訊息處理就不會結束。 有害訊息佇列中的訊息必須繼續讀取和處理。 您可以在最終有害子佇列中讀取訊息時，使用有害訊息處理設定的子集。 適當的設定為 `ReceiveRetryCount` 和 `ReceiveErrorHandling`。 您可以將 `ReceiveErrorHandling` 設定為 Drop、Reject 或 Fault。 如果 `MaxRetryCycles` 設為 Move，則會忽略 `ReceiveErrorHandling` 並且擲回例外狀況。  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista、Windows Server 2003 及 Windows XP 的差異  
 如之前所述，並非所有有害訊息處理設定都適用於 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]。 下列 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上之訊息佇列間的主要差異，都與有害訊息處理相關：  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的訊息佇列支援子佇列，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 則不支援子佇列。 子佇列是在有害訊息處理中使用。 重試佇列和有害佇列都是應用程式佇列的子佇列，應用程式佇列是根據有害訊息處理設定而建立的。 `MaxRetryCycles` 會指示要建立多少重試子佇列。 因此，當在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上執行時，會略過 `MaxRetryCycles` 並且不允許 `ReceiveErrorHandling.Move`。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的訊息佇列支援負值通知，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 則不支援。 來自接收佇列管理員的負認可會造成傳送佇列管理員將拒絕的訊息放在寄不出的信件佇列中。 因此，`ReceiveErrorHandling.Reject` 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 不可使用 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的訊息佇列支援能夠保留嘗試傳遞訊息之計數的訊息屬性 這個中止計數屬性無法在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上使用。 WCF 會維護記憶體中，中止計數，因此它是這個屬性可能不包含精確的值相同的訊息讀取的伺服陣列中的多個 WCF 服務時。  
  
## <a name="see-also"></a>另請參閱  
 [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [指定及處理合約與服務中的錯誤](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
