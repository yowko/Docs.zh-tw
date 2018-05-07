---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ 已拒絕訊息。  
  
## <a name="description"></a>描述  
 這個追蹤表示已拒絕 MSMQ 訊息。  
  
 Windows Communication Foundation (WCF) （與 NetMsmqBinding 或 msmqintegrationbinding 配合使用） 無法處理它們時，可以拒絕 MSMQ 訊息。 這類訊息稱為有害訊息。 有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。 拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkID=99544)。  
  
 請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。  
  
 請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)如需有關在 MSMQ 中表示的拒絕的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
