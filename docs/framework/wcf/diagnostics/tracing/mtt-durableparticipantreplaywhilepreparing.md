---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。 因此，交易已中止。  
  
## <a name="description"></a>描述  
 如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。 這是此狀態的不合法訊息，因此交易即將中止。  
  
## <a name="troubleshooting"></a>疑難排解  
 接收這項錯誤可能表示參與者 (包括下層異動管理員) 已經從失敗復原，不過不確定異動結果並要求其狀態。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
