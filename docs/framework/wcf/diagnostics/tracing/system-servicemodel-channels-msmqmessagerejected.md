---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674778"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ 已拒絕訊息。  
  
## <a name="description"></a>描述  
 這個追蹤表示已拒絕 MSMQ 訊息。  
  
 當 Windows 通信基礎 （WCF） （與 NetMmqBinding 或 Msmq 集成綁定一起使用） 無法處理 MSMQ 消息時，MSMQ 消息可能會被拒絕。 這類訊息稱為有害訊息。 有害訊息會在 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設為 `Reject` 時遭到拒絕。 被拒絕的郵件將傳遞回寄件者[的無效信件佇列](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)。  
  
 有關消息何時成為病毒以及如何佈建服務以正確處理它們的詳細資訊，請參閱[毒消息處理](../../feature-details/poison-message-handling.md)。  
  
 有關被拒絕的郵件在 MSMQ 中的含義的詳細資訊，請參閱[MQMarkMessage 拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
- [有害訊息處理](../../feature-details/poison-message-handling.md)
- [MQMark消息被拒絕](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
