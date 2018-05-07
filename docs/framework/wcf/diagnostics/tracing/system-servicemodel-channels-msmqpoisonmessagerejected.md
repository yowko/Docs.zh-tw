---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 7dc1e4120caae7c4a592067f5e77ed4f56e82e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
已拒絕有害訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示遇到有害訊息，隨後拒絕該訊息。 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。 拒絕的訊息傳送至寄件者的[寄不出的信件佇列](http://go.microsoft.com/fwlink/?LinkId=99544)。  
  
 請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。 請參閱[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)如需有關在 MSMQ 中表示的拒絕的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [有害訊息處理](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
