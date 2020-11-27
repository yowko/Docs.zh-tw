---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 69da35f65e04a3cba15885c4fe6e57d63762cb1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260340"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected

已拒絕有害訊息。  
  
## <a name="description"></a>描述  

 此追蹤表示遇到有害訊息，隨後拒絕該訊息。 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Reject` 時，便會發生這種情況。 拒絕的訊息會傳回給寄件者的寄不出的 [信件佇列](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)。  
  
 如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。 如需 MSMQ 中的已拒絕訊息的詳細資訊，請參閱 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
- [有害訊息處理](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))
