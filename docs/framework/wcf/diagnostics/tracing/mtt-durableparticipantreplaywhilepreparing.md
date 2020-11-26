---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: bfa279887339f025e4cb7c9c455fd25098684073
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236607"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing

WS-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。 因此，交易已中止。  
  
## <a name="description"></a>描述  

 如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。 這是此狀態的不合法訊息，因此異動即將中止。  
  
## <a name="troubleshooting"></a>疑難排解

收到此錯誤可能表示長期參與者 (包括次級 TransactionManagers) 已從失敗復原;不過，它不確定交易結果會要求其狀態。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
