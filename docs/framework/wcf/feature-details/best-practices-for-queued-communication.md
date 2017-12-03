---
title: "佇列通訊的最佳做法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15de43cc83e92b781e44da703353bec98dbc2c6a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-for-queued-communication"></a>佇列通訊的最佳做法
此主題為 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的佇列通訊提供建議的做法。 下列各節由案例的觀點來討論建議的做法。  
  
## <a name="fast-best-effort-queued-messaging"></a>快速、最佳的佇列傳訊  
 在需要佇列傳訊提供分離、且以最佳保證提供快速、高效能的傳訊案例中，使用非交易式佇列並且將 <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> 屬性設定為 `false`。  
  
 此外，您可以透過將 <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> 屬性設定為 `false`，來選擇不要造成磁碟寫入的成本。  
  
 安全性隱含對效能的影響。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][效能考量](../../../../docs/framework/wcf/feature-details/performance-considerations.md)。  
  
## <a name="reliable-end-to-end-queued-messaging"></a>可靠的端對端佇列傳訊  
 下列各節描述需要端對端可靠傳訊的案例之建議做法。  
  
### <a name="basic-reliable-transfer"></a>基本可靠傳輸  
 對於端對端可靠性，將 <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> 屬性設定為 `true` 以確保傳輸。 視您的需要將 <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> 屬性設定為 `true` 或 `false` (預設為 `true`)。 一般而言，<xref:System.ServiceModel.MsmqBindingBase.Durable%2A> 屬性設定為 `true` 以作為端對端可靠性的一部分。 危害是一種效能成本，但會使訊息成為永久性的訊息，因此佇列管理員中止時，不會遺失訊息。  
  
### <a name="use-of-transactions"></a>使用交易  
 您必須使用交易來確保端對端的可靠性。 `ExactlyOnce` 保證只能夠確保訊息傳送到目標佇列。 若要確保收到訊息，請使用交易。 如果沒有使用交易，在服務中止時，您會遺失實際上正在傳遞給應用程式的訊息。  
  
### <a name="use-of-dead-letter-queues"></a>使用寄不出的信件佇列  
 寄不出的信件佇列確保在訊息無法傳遞至目標時通知您。 灺可以使用系統提供的寄不出的信件佇列，或自訂的寄不出的信件佇列。 一般而言，使用自訂的寄不出的信件佇列是最佳選擇，因為它可以讓您將寄不出的信件訊息從某個應用程式傳送到單一寄不出的信件佇列中。 否則，針對在系統上執行的所有應用程式產生的所有寄不出的信件訊息會傳遞到單一佇列。 然後每個應用程式必須搜尋整個寄不出的信件佇列，以尋找和該應用程式相關的寄不出的信件訊息。 有時使用自訂的寄不出的信件佇列不可行，例如在使用 MSMQ 3.0 時。  
  
 不建議關閉用於端對端可靠通訊的寄不出的信件佇列。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][使用寄不出信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。  
  
### <a name="use-of-poison-message-handling"></a>使用有害訊息處理  
 有害訊息處理提供從失敗中復原的能力以處理訊息。  
  
 使用有害訊息處理功能時，請確定 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 屬性已設定為適當的值。 設定為 <xref:System.ServiceModel.ReceiveErrorHandling.Drop> 表示資料遺失。 另一方面，當偵測到有害訊息時，將它設定為 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> 會導致服務主機發生錯誤。 使用 MSMQ 3.0 時，<xref:System.ServiceModel.ReceiveErrorHandling.Fault> 是避免資料遺失與移走有害訊息的最佳選項。 使用 MSMQ 4.0 時，<xref:System.ServiceModel.ReceiveErrorHandling.Move> 是建議的處理方式。 <xref:System.ServiceModel.ReceiveErrorHandling.Move> 會將有害訊息移出佇列，讓服務可以繼續處理新訊息。 然後有害訊息服務可以個別處理有害訊息。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)。  
  
## <a name="achieving-high-throughput"></a>達到高輸送量  
 若要在單一端點上達到高輸送量，可以使用下列幾項：  
  
-   交易的批次處理。 交易的批次處理確保可以在單一交易中讀取多則訊息。 這樣可以最佳化交易認可，因此增加了整體效能。 批次處理的代價在於，如果批次內的一則訊息中發生失敗，整個批次都要復原，而且必須一次處理一則訊息，直到再度對批次而言是安全的為止。 在大部分情況中，傾向於使用批次處理增加系統效能，特別是當您有參與異動的其他資源管理員時。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][在交易中批次處理訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)。  
  
-   並行。 並行可以增加輸送量，但也會影響對共用資源的爭用。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][並行](../../../../docs/framework/wcf/samples/concurrency.md)。  
  
-   節流。 為了得到最佳效能，控制在發送器管線中的訊息數目。 如需如何執行此動作的範例，請參閱[節流](../../../../docs/framework/wcf/samples/throttling.md)。  
  
 使用批次處理時，注意轉換為並行批次的並行與節流。  
  
 若要達到更高的輸送量和可用性，可以使用自佇列讀取的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務陣列。 這樣做需要所有這些服務在相同的端點上公開相同的合約。 陣列方法最適合有高訊息產生速率的應用程式，因為它對所有來自相同佇列的讀取啟用多種服務。  
  
 使用陣列時，注意 MSMQ 3.0 不支援遠端交易的讀取。 MSMQ 4.0 不支援遠端交易的讀取。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][在交易中批次處理訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)和[Windows Vista、 Windows Server 2003 和 Windows XP 中的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)。  
  
## <a name="queuing-with-unit-of-work-semantics"></a>有工作單元語意的佇列  
 在有些案例中，可能與佇列中的訊息群組有關，因此這些訊息的排序非常重要。 在這類案例中，將相關訊息群組視為單一單元而加以處理：全部都成功處理或全部都未成功處理。 若要實作這類行為，請使用有佇列的工作階段。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][在工作階段中群組佇列的訊息](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)。  
  
## <a name="correlating-request-reply-messages"></a>相關的要求回覆訊息  
 雖然佇列都是單向的，在有些案例中，您可能想要將收到的回覆與之前傳送的要求相互關聯。 如果您需要這類關聯，建議您套用自己的 SOA 訊息標頭，此標題包含與訊息關聯的資訊。 一般來說，寄件者將此標頭附加在訊息中，而處理訊息並以回覆佇列上的新訊息回覆的接收者附加包含關聯資訊的傳送者訊息標頭，因此傳送者可以透過要求訊息來識別回覆訊息。  
  
## <a name="integrating-with-non-wcf-applications"></a>整合非 WCF 應用程式  
 使用 `MsmqIntegrationBinding` 整合 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或用戶端與非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或用戶端時。 非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式可能是使用 System.Messaging、COM+、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 C++ 撰寫的 MSMQ 應用程式。  
  
 使用 `MsmqIntegrationBinding` 時，請注意下列各點：  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息本文和 MSMQ 訊息本文不相同。 使用佇列繫結傳送 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息本文放置在 MSMQ 訊息內。 MSMQ 基礎結構未注意到此額外資訊，它只看到 MSMQ 訊息。  
  
-   `MsmqIntegrationBinding` 支援常見的序列化類型。 根據序列化類型、泛型訊息的本文類型、<xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>，採用不同類型的參數。 例如，<xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> 需要 `MsmqMessage\<byte[]>`，而 <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> 需要 `MsmqMessage<Stream>`。  
  
-   使用 XML 序列化，您可以指定已知型別使用`KnownTypes`屬性[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目，然後用來判斷如何還原序列化的 XML 訊息。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [如何： Exchange 佇列與 WCF 端點的訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [如何： 與 WCF 端點交換訊息和訊息佇列應用程式](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [工作階段中群組佇列訊息](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [在交易中批次處理訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [使用寄不出信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [在 Windows Vista、 Windows Server 2003 和 Windows XP 中的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [使用傳輸安全性保障訊息](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [使用訊息安全性保護訊息](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [佇列訊息的疑難排解](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
