---
title: 使用寄不出的信件佇列來處理訊息傳輸失敗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: b8dae094655e7bf2a52848d449a5f604f846e052
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497088"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>使用寄不出的信件佇列來處理訊息傳輸失敗
佇列訊息可能會傳遞失敗。 這些失敗的訊息都會記錄在寄不出的信件佇列中。 造成傳遞失敗的原因可能是網路失敗、佇列已刪除、佇列已滿、驗證失敗，或是未能準時傳遞。  
  
 如果接收應用程式未及時讀取佇列中的訊息，佇列的訊息可能會長時間停留於佇列中。 這項行為對於時間緊急的訊息可能會不適當。 時間緊急訊息的佇列繫結會設定「訊息存留時間」(TTL) 屬性，此屬性會指示該訊息在過期前可於佇列中停留多久。 過期訊息會傳送至稱為「寄不出的信件佇列」的特殊佇列。 訊息也可能會因為其他原因而放入寄不出的信件佇列中，例如超過佇列配額或發生驗證失敗。  
  
 一般而言，應用程式都會撰寫補償邏輯來讀取寄不出的信件佇列中的訊息和失敗原因。 補償邏輯會依據失敗原因而有不同。 例如，在驗證失敗的情況下，您可以修正附加在訊息中的憑證，並且重新傳送訊息。 如果是因為到達目標佇列配額而導致傳遞失敗，您可以在解決配額問題之後重新嘗試傳遞。  
  
 大多數佇列系統都有整個系統的寄不出的信件佇列，而該系統的所有失敗訊息都會儲存於其中。 訊息佇列 (MSMQ) 提供兩種整個系統的寄不出的信件佇列，一個是整個系統的異動式寄不出的信件佇列，其中會儲存無法傳遞到異動式佇列的訊息，另一個是整個系統的非異動式寄不出的信件佇列，其中會儲存無法傳遞到非異動式佇列的訊息。 如果兩個用戶端會將訊息傳送至兩個不同的服務，因此在 WCF 中的不同佇列共用相同 MSMQ 服務以傳送，則可以在系統的寄不出信件佇列中有混合的訊息。 這種處理不一定是最佳做法。 在幾種情況下 (例如，考量安全性的情況下)，您可能不想讓某個用戶端從寄不出的信件佇列中讀取到另一個用戶端的訊息。 共用的寄不出的信件佇列也會要求用戶端瀏覽整個佇列來尋找自己所傳送的訊息，而根據寄不出的信件佇列中的訊息數目，這樣可能會極為耗費資源。 因此，在 WCF`NetMsmqBinding`，`MsmqIntegrationBinding,`上的 MSMQ 和[!INCLUDE[wv](../../../../includes/wv-md.md)]提供自訂的寄不出信件佇列 （有時候稱為 「 應用程式特定之寄不出信件佇列 」）。  
  
 自訂的寄不出的信件佇列會隔離共用相同 MSMQ 服務以傳送訊息的用戶端。  
  
 在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]和[!INCLUDE[wxp](../../../../includes/wxp-md.md)]，Windows Communication Foundation (WCF) 提供所有已排入佇列的用戶端應用程式的整個系統寄不出信件佇列。 在  [!INCLUDE[wv](../../../../includes/wv-md.md)]，WCF 會提供每個已排入佇列的用戶端應用程式中的寄不出信件佇列。  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>指定寄不出的信件佇列的使用方式  
 寄不出的信件佇列是位於傳送應用程式的佇列管理員中。 它會儲存已過期的訊息或是無法傳輸或傳遞的訊息。  
  
 繫結具有下列寄不出的信件佇列屬性：  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>從寄不出的信件佇列讀取訊息  
 讀取的應用程式佇列，除了下列的細微差異的 WCF 服務應用程式，以讀取從寄不出信件佇列的訊息如下：  
  
-   為了從系統的異動式寄不出的信件佇列讀取訊息，統一資源識別元 (URI) 必須採用 net.msmq://localhost/system$;DeadXact 的格式。  
  
-   為了從系統的非異動式寄不出的信件佇列讀取訊息，URI 必須採用 net.msmq://localhost/system$;DeadLetter 的格式。  
  
-   若要從自訂的寄不出信件佇列讀取訊息，URI 必須是表單 net.msmq: //localhost/private/<\<*自訂 dlq 名稱*> 位置*自訂 dlq 名稱*是自訂名稱寄不出信件佇列。  
  
 如需如何位址佇列的詳細資訊，請參閱[服務端點與佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)。  
  
 WCF 堆疊在接收者上的比對訊息上的位址，此服務會接聽位址。 如果這些位址相符，便發送該訊息，否則，就不發送該訊息。 這種做法在從寄不出的信件佇列讀取訊息時會發生問題，因為寄不出的信件佇列中的訊息通常是定位傳送給該服務，而不定位傳送給寄不出的信件佇列服務。 因此，從寄不出的信件佇列讀取的服務必須安裝位址篩選 `ServiceBehavior`，這個行為會指示堆疊比對佇列中的所有訊息，而不管收訊者為何。 具體來說，您必須在從寄不出的信件佇列讀取訊息的服務中新增含有 `ServiceBehavior` 參數的 <xref:System.ServiceModel.AddressFilterMode.Any>。  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>從寄不出的信件佇列處理有害訊息  
 在一些條件前提下，寄不出的信件佇列會提供有害訊息處理的功能。 由於您無法從系統佇列建立子佇列，所以在從系統的寄不出的信件佇列讀取時，`ReceiveErrorHandling` 無法設定為 `Move`。 請注意，如果是從自訂的寄不出的信件佇列讀取，您就可建立子佇列，因此，`Move` 會是有效處置有害訊息的方式。  
  
 當 `ReceiveErrorHandling` 設定為 `Reject`，從自訂的寄不出的信件佇列讀取時，有害訊息將會放到系統的寄不出的信件佇列中。 如果是從系統的寄不出的信件佇列讀取，該訊息就會被捨棄 (清除)。 在 MSMQ 中，由系統的寄不出的信件佇列傳回 Reject 時，便會捨棄 (清除) 訊息。  
  
## <a name="example"></a>範例  
 下列範例會示範如何建立寄不出的信件佇列，以及如何使用該佇列來處理過期的訊息。 此範例為基礎的範例[How to:與 WCF 端點交換佇列訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)。 下列範例會示範如何撰寫訂單處理服務的用戶端程式碼，該服務會分別針對每個應用程式使用寄不出的信件佇列。 這個範例也會示範如何處理寄不出的信件佇列中的訊息。  
  
 下列是用戶端的程式碼，此用戶端會針對每個應用程式指定寄不出的信件佇列。  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 下列是用戶端組態檔的程式碼。  
  
  
  
 下列是服務的程式碼，此服務會處理寄不出的信件佇列中的訊息。  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 下列是寄不出的信件佇列服務組態檔的程式碼。  
  
  
  
## <a name="see-also"></a>另請參閱
- [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [如何：與 WCF 端點交換佇列訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
