---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593746"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
無法移動或刪除訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。  
  
 MSMQ 訊息是由 Windows Communication Foundation （WCF）（搭配 NetMsmqBinding 或 MsmqIntegrationBinding 使用時）所採用。此追蹤與 `ReceiveErrorHandling` NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性所選擇的值有關。  
  
 此追蹤不代表整體系統失敗。 但是，它代表某個訊息的選定有害訊息處置作業失敗。 如需訊息何時會變成有害的詳細資訊，以及如何設定您的服務來適當地處理它們，請參閱[有害訊息處理](../../feature-details/poison-message-handling.md)。  
  
## <a name="see-also"></a>請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
