---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579017"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
WS-AT 通訊協定服務在等待來自變動參與者的結果訊息回應時逾時。 如果參與者傳回則交易結果可能不確定。  
  
## <a name="description"></a>描述  
 當「變動」參與者決定要「認可」或「中止」，但是在指定時間內尚未回應「認可」或「復原」要求時就會追蹤。  
  
## <a name="troubleshooting"></a>疑難排解  
 請確定所有的「變動」參與者都能夠在指定時間內回應。 預設時間週期為 180 秒。  如果時間不夠的話，請增加 WS-AT 的 `VolatileOutcomeDelay` 計時器原則。  
  
## <a name="see-also"></a>請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
