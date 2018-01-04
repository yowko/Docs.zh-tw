---
title: "以 Web 裝載佇列應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a12348c3c49c29812530bc568bb5873ec53f7eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="web-hosting-a-queued-application"></a>以 Web 裝載佇列應用程式
Windows Process Activation Service (WAS) 管理背景工作處理序 (其中包含裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的應用程式) 的啟動與存留期。 WAS 處理序模型會藉由移除 HTTP 上的相依性，將 HTTP 伺服器的 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 處理序模型一般化。 如此可讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務能在支援訊息啟動以及提供可在指定電腦上裝載大量應用程式之能力的裝載環境中，同時使用 HTTP 和非 HTTP 通訊協定，例如 net.msmq 和 msmq.formatname。  
  
 WAS 包括訊息佇列 (MSMQ) 啟動服務，該服務會在佇列的應用程式所使用的其中一個佇列內置放一個或多個訊息時，啟動佇列的應用程式。 MSMQ 啟動服務是 NT 服務，預設為自動啟動。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WAS 和它的優點，請參閱[Windows Process Activation Service 中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]MSMQ 中，請參閱[佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
  
## <a name="queue-addressing-in-was"></a>WAS 中的佇列定址  
 WAS 應用程式擁有統一資源識別元 (URI) 位址。 應用程式位址包含兩個部分：基底 URI 前置詞和應用程式專屬的相對位址 (路徑)。 這兩個部分合在一起，便提供了應用程式的外部位址。 基底 URI 前置詞根據網站繫結所建構，並使用網站，例如"net.msmq: //localhost"、"msmq.formatname: //localhost"或"net.tcp: //localhost"下的所有應用程式。 然後會由特定應用程式的路徑片段建構應用程式位址 (例如"/ /applicationone") 並將它們附加至基底 URI 前置詞完整的應用程式的 URI，例如"net.msmq: //localhost/applicationone"。  
  
 MSMQ 啟動服務會使用應用程式 URI，比對 MSMQ 啟動服務必須監視的訊息佇列。 當 MSMQ 啟動服務啟動時，便會在設定為訊息接收來源的電腦上，列舉其所有的公用和私用佇列，並且監視佇列中是否有訊息。 MSMQ 啟動服務每 10 分鐘會更新一次監視的佇列清單。 若在佇列中找到訊息，啟動服務就會將訊息名稱與 net.msmq 繫結中相符程度最高的應用程式 URI 進行比對，並啟動應用程式。  
  
> [!NOTE]
>  啟動的應用程式必須符合 (相符程度最高) 佇列名稱的前置詞。  
  
 例如，佇列名稱為：msmqWebHost/orderProcessing/service.svc。 如果應用程式 1 擁有虛擬目錄 /msmqWebHost/orderProcessing，而且其中有一個 service.svc 檔案，而應用程式 2 擁有虛擬目錄 /msmqWebHost，而其中有一個 orderProcessing.svc 檔案，則會啟動應用程式 1。 如果應用程式 1 被刪除，則會啟動應用程式 2。  
  
> [!NOTE]
>  當建立佇列時，任何傳送到該佇列的訊息都不會啟動應用程式，除非 MSMQ 啟動服務重新整理佇列清單，也就是自建立佇列起算最多 10 分鐘。 重新啟動啟動服務也同時會重新整理佇列清單。  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>私用和公用佇列在定址上的影響  
 MSMQ 啟動服務並不會區分私用和公用佇列監視。 因此，您不能以相同名稱使用公用和私用佇列。 如果您這樣做，Web 裝載的應用程式可能會啟動，並從其中一個佇列讀取。  
  
### <a name="queue-configuration-for-activation"></a>啟動的佇列組態  
 MSMQ 啟動服務會以 NETWORK SERVICE 執行。 它是監視佇列以啟動應用程式的服務。 若要讓它從佇列啟動應用程式，則必須提供佇列，讓 NETWORK SERVICE 存取查看其存取控制清單 (ACL) 中的訊息。  
  
### <a name="poison-messaging"></a>有害訊息  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的有害訊息是由通道所處理，不僅會偵測訊息是否有害，還會根據使用者組態選取處置方法。 因此，佇列中會有單一訊息。 Web 裝載的應用程式會中止後續的次數，而且該訊息會移到重試佇列中。 在重試週期延遲所指定的時間點上，該訊息會從重試佇列移到主要佇列並再次嘗試。 但是這個動作需要佇列通道為使用中的狀態。 如果應用程式由 WAS 回收，那麼訊息就會留在重試佇列中，除非另一個訊息到達主要佇列並啟動佇列的應用程式。 這個情況的解決方法是手動將訊息從重試佇列移回主要佇列，以重新啟動應用程式。  
  
### <a name="subqueue-and-system-queue-caveat"></a>子佇列和系統佇列警告  
 WAS 裝載的應用程式無法根據系統佇列中的訊息啟動，例如整個系統寄不出的信件佇列，或是子佇列，例如有害子佇列。 這是這個產品版本的限制。  
  
## <a name="see-also"></a>請參閱  
 [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [服務端點與佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
