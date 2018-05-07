---
title: Windows Communication Foundation 中的佇列
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: 96dfee3304369c300c40d595860898c51ff728aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="queues-in-windows-communication-foundation"></a>Windows Communication Foundation 中的佇列
本節中的主題會討論 Windows Communication Foundation (WCF) 支援的佇列。 WCF 支援利用 Microsoft Message Queuing （舊稱 MSMQ） 做為傳輸方式的佇列，並可讓下列案例：  
  
-   鬆散結合的應用程式。 傳送應用程式可以傳送訊息至佇列，不需要知道接收應用程式是否可以處理訊息。 佇列以不依靠接收應用程式可以多快處理訊息的速率，提供允許傳送應用程式傳送訊息至佇列的獨立處理。 傳送訊息至未與訊息處理緊密結合的佇列時，整體系統可用性會增加。  
  
-   隔離失敗。 應用程式傳送或接收訊息至佇列可能失敗，但不會互相影響。 例如，如果接收應用程式失敗，傳送應用程式可以繼續傳送訊息至佇列。 當接收者再次接收時，可以處理來自佇列的訊息。 隔離失敗會增加整體系統的可靠性與可用性。  
  
-   負載平衡。 傳送應用程式可能會利用訊息讓接收應用程式爆滿。 佇列可以管理不相符的訊息產生與消耗率，因此接收者不會爆滿。  
  
-   中斷操作。 當透過高延遲網路或可用性有限的網路進行通訊時 (例如使用行動裝置)，傳送、接收和處理操作可能中斷。 佇列能夠使這些操作繼續進行，即使已經與端點中斷連線也是一樣。 重新建立連線後，佇列會將訊息轉送至接收應用程式。  
  
 若要使用的佇列功能的 WCF 應用程式中，您可以使用其中一個標準繫結，或如果其中一個標準繫結無法滿足您的需求，您可以建立自訂繫結。 如需相關的標準繫結，以及如何選擇其中一個的詳細資訊，請參閱[How to： 與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。 如需有關如何建立自訂繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 訊息佇列概念的概觀。  
  
 [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 WCF 佇列支援的概觀。  
  
 [如何：與 WCF 端點交換佇列訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 說明如何使用<xref:System.ServiceModel.NetMsmqBinding>類別間的 WCF 用戶端和 WCF 服務進行通訊。  
  
 [如何：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 說明如何使用<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>WCF 和訊息佇列應用程式之間進行通訊。  
  
 [在工作階段中群組佇列訊息](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 說明如何將佇列中的訊息分組，以協助單一接收應用程式處理相關訊息。  
  
 [批次處理異動中的訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 說明如何批次處理異動中的訊息。  
  
 [使用無效信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 說明如何使用寄不出的信件佇列處理訊息傳送和傳遞失敗，以及如何處理來自寄不出的信件佇列的訊息。  
  
 [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 說明如何處理有害訊息 (超過傳送到接收應用程式的最大嘗試傳遞次數的訊息)。  
  
 [Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 摘要說明在 WCF 的佇列功能之間的差異[!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，和[!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
 [使用傳輸安全性來保護訊息的安全](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 描述如何使用傳輸安全性來保護佇列訊息的安全。  
  
 [使用訊息安全性來保護訊息的安全](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 描述如何使用訊息安全性來保護佇列訊息的安全。  
  
 [為佇列訊息進行疑難排解](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 說明如何疑難排解常見的佇列問題。  
  
 [佇列通訊的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 說明使用 WCF 的最佳作法佇列通訊。  
  
## <a name="see-also"></a>另請參閱  
 [訊息佇列](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
