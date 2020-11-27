---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: aeeba38eaf674453f4c87cf62f5088c55b5fde2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290812"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed

無法移動或刪除訊息。  
  
## <a name="description"></a>描述  

 此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。  
  
 當搭配 NetMsmqBinding 或 MsmqIntegrationBinding) 使用時，Windows Communication Foundation (WCF)  (會採用 MSMQ 訊息。這項追蹤與 `ReceiveErrorHandling` NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性所選擇的值有關。  
  
 此追蹤不代表整體系統失敗。 但是，它代表某個訊息的選定有害訊息處置作業失敗。 如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
