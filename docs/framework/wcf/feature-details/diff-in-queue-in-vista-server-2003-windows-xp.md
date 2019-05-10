---
title: Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: 694d7af8e6e869a7a21a3414be6c69cf9f5e7c8f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627001"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異
本主題摘要說明在 Windows Communication Foundation (WCF) 佇列功能之間的差異[!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，和[!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
## <a name="application-specific-dead-letter-queue"></a>應用程式特定之寄不出的信件佇列  
 如果接收應用程式沒有及時讀取佇列訊息，則佇列訊息可以無限期保留在佇列中。 如果是時間緊急的訊息，這個行為並不合適。 時間緊急的訊息會在佇列繫結中設定 `TimeToLive` 屬性。 這個屬性指出訊息在到期前可在佇列中停留的時間長度。 過期訊息會傳送至稱為「寄不出的信件佇列」的特殊佇列。 訊息最後也可以因為其他原因而放在寄不出的信件佇列中，例如超過佇列配額或經歷驗證失敗。  
  
 一般而言，所有共用佇列管理員的佇列應用程式都有單一整個系統之寄不出的信件佇列。 各個應用程式之寄不出的信件佇列都會允許佇列應用程式指定自己應用程式特定之寄不出的信件佇列，讓這些應用程式之間有更好的隔離。 與其他應用程式共用寄不出的信件佇列之應用程式必須瀏覽佇列，以尋找適用的訊息。 使用應用程式特定之寄不出的信件佇列，可以向應用程式保證其寄不出的信件佇列中所有訊息都適用。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] 提供應用程式特定之寄不出的信件佇列。 應用程式特定之寄不出的信件佇列無法在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中使用，且應用程式必須使用整個系統之寄不出的信件佇列。  
  
## <a name="poison-message-handling"></a>有害訊息處理  
 有害訊息是超過嘗試傳遞至接收應用程式之次數上限的訊息。 當從異動式佇列讀取訊息的應用程式因錯誤無法立即處理訊息時，便會引起這種情況。 如果應用程式中止收到佇列訊息的交易，會將訊息傳回佇列。 然後應用程式會嘗試在新的異動中再次擷取訊息。 如果沒有更正造成錯誤的問題，接收應用程式會卡在接收及中止相同訊息的迴圈中，直到超過傳遞嘗試次數上限為止，而形成有害訊息。  
  
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的訊息佇列 (MSMQ) 之間，與有害處理有關的主要差別包括下列：  
  
- [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支援子佇列，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 不支援子佇列。 子佇列是在有害訊息處理中使用。 重試佇列和有害佇列都是應用程式佇列的子佇列，應用程式佇列是根據有害訊息處理設定而建立的。 `MaxRetryCycles` 會指示要建立多少重試子佇列。 因此，當在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上執行時，會略過 `MaxRetryCycles` 並且不允許 `ReceiveErrorHandling.Move`。  
  
- [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支援負認可，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 則否。 來自接收佇列管理員的負認可會造成傳送佇列管理員將拒絕的訊息放在寄不出的信件佇列中。 因此，`ReceiveErrorHandling.Reject` 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 不可使用 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
- [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支援訊息屬性，持續計算嘗試傳遞訊息的次數。 這個中止計數屬性無法在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上使用。 WCF 會維護記憶體中的中止計數，因此它是這個屬性可能不包含精確的值相同的訊息讀取的 Web 伺服陣列中的多個 WCF 服務時。  
  
## <a name="remote-transactional-read"></a>遠端交易式讀取  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 MSMQ 支援遠端異動式讀取。 這允許從佇列讀取的應用程式裝載在與裝載佇列不同的電腦上。 這可以確保讓服務的伺服陣列從中央佇列讀取的能力，以增加系統的整體輸送量。 它也可以確保當讀取及處理訊息、交易復原以及訊息保留在佇列中以供日後處理時，是否會發生失敗。  
  
## <a name="see-also"></a>另請參閱

- [使用無效信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
