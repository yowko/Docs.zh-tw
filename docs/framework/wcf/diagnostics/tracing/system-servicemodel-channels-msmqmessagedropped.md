---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6e8b134f61d2dc9bd5daf541db4ec81604166baa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260379"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped

MSMQ 已捨棄訊息。  
  
## <a name="description"></a>描述  

 此追蹤表示已捨棄 MSMQ 訊息。 當 Windows Communication Foundation (WCF)  (搭配 NetMsmqBinding 或 MsmqIntegrationBinding) 無法處理時，可以卸載 MSMQ 訊息。 這類訊息稱為有害訊息。  
  
 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。 捨棄的訊息會從佇列中移除，無法再復原。  
  
 如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
- [有害訊息處理](../../feature-details/poison-message-handling.md)
