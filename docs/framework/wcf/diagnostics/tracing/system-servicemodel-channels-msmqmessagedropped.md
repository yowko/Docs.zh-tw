---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661109"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ 已捨棄訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示已捨棄 MSMQ 訊息。 Windows Communication Foundation (WCF) （使用與 NetMsmqBinding 或 MsmqIntegrationBinding） 無法處理它們時，可以卸除 MSMQ 訊息。 這類訊息稱為有害訊息。  
  
 當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。 捨棄的訊息會從佇列中移除，無法再復原。  
  
 請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)
