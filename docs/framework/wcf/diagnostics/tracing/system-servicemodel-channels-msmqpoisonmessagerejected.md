---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 562399c1d45dc73c7c88bd165e9f95ee1bcfa19d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125077"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
已拒絕有害訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示遇到有害訊息，隨後拒絕該訊息。 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。 被拒絕的訊息會傳遞回寄件者[寄不出信件佇列](https://go.microsoft.com/fwlink/?LinkId=99544)。  
  
 請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkId=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。 請參閱[MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)如需詳細資訊被拒絕的訊息表示 MSMQ 中。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害訊息處理](https://go.microsoft.com/fwlink/?LinkId=99546)
- [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)
