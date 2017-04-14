---
title: "Windows Communication Foundation 中的佇列 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "佇列 [WCF]"
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Windows Communication Foundation 中的佇列
本節中的主題討論 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 對佇列的支援。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 利用 Microsoft Message Queuing \(先前簡稱為 MSMQ\) 做為傳輸以支援佇列功能，並且可以完成下列情節：  
  
-   鬆散結合的應用程式。傳送應用程式可以傳送訊息至佇列，不需要知道接收應用程式是否可以處理訊息。佇列以不依靠接收應用程式可以多快處理訊息的速率，提供允許傳送應用程式傳送訊息至佇列的獨立處理。傳送訊息至未與訊息處理緊密結合的佇列時，整體系統可用性會增加。  
  
-   隔離失敗。應用程式傳送或接收訊息至佇列可能失敗，但不會互相影響。例如，如果接收應用程式失敗，傳送應用程式可以繼續傳送訊息至佇列。當接收者再次接收時，可以處理來自佇列的訊息。隔離失敗會增加整體系統的可靠性與可用性。  
  
-   負載平衡。傳送應用程式可能會利用訊息讓接收應用程式爆滿。佇列可以管理不相符的訊息產生與消耗率，因此接收者不會爆滿。  
  
-   中斷操作。當透過高延遲網路或可用性有限的網路進行通訊時 \(例如使用行動裝置\)，傳送、接收和處理操作可能中斷。佇列能夠使這些操作繼續進行，即使已經與端點中斷連線也是一樣。重新建立連線後，佇列會將訊息轉送至接收應用程式。  
  
 若要使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中的佇列功能，您可以使用其中一個標準繫結，或者如果其中一個標準繫結無法滿足您的需求時，您可以建立自訂繫結。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]相關標準繫結以及如何選擇繫結的詳細資訊，請參閱 [HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## 在本節中  
 [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 訊息佇列概念的概觀。  
  
 [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 佇列支援的概觀。  
  
 [HOW TO：與 WCF 端點交換佇列訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 說明如何使用 <xref:System.ServiceModel.NetMsmqBinding> 類別在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間通訊。  
  
 [HOW TO：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 說明如何使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和訊息佇列應用程式之間通訊。  
  
 [在工作階段中群組佇列訊息](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 說明如何將佇列中的訊息分組，以協助單一接收應用程式處理相關訊息。  
  
 [批次處理交易中的訊息](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 說明如何批次處理交易中的訊息。  
  
 [使用寄不出的信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 說明如何使用寄不出的信件佇列處理訊息傳送和傳遞失敗，以及如何處理來自寄不出的信件佇列的訊息。  
  
 [有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 說明如何處理有害訊息 \(超過傳送到接收應用程式的最大嘗試傳遞次數的訊息\)。  
  
 [Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 摘要說明在 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 之間 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 佇列的差異。  
  
 [使用傳輸安全性來確保訊息的安全](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 描述如何使用傳輸安全性來保護佇列訊息的安全。  
  
 [使用訊息安全性來保護訊息的安全](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 描述如何使用訊息安全性來保護佇列訊息的安全。  
  
 [佇列訊息的疑難排解](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 說明如何疑難排解常見的佇列問題。  
  
 [佇列通訊的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 說明使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 佇列通訊的最佳做法。  
  
## 請參閱  
 [Message Queuing](http://msdn.microsoft.com/zh-tw/ff917e87-05d5-478f-9430-0f560675ece1)