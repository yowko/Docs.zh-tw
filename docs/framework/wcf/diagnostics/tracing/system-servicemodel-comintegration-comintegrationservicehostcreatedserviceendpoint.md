---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: d56bbf145c85902d8e5f1fd21f760633121da6da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939213"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
無法移動或刪除訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。  
  
 MSMQ 訊息會採用由 Windows Communication Foundation (WCF) （當使用 NetMsmqBinding 或 MsmqIntegrationBinding）。這個追蹤所選的值與相關`ReceiveErrorHandling`NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性。  
  
 此追蹤不代表整體系統失敗。 但是，它代表某個訊息的選定有害訊息處置作業失敗。 請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
