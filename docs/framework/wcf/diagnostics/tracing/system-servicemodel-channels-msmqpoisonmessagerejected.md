---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674805"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
已拒絕有害訊息。  
  
## <a name="description"></a>描述  

 此追蹤表示遇到有害訊息，隨後拒絕該訊息。 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。 被拒絕的郵件將傳遞回寄件者[的無效信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。  
  
 有關消息何時成為病毒以及如何佈建服務以正確處理它們的詳細資訊，請參閱[毒消息處理](../../feature-details/poison-message-handling.md)。 有關被拒絕的郵件在 MSMQ 中的含義的詳細資訊，請參閱[MQMarkMessage 拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害訊息處理](../../feature-details/poison-message-handling.md)
- [MQMark消息被拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
