---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596203"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
重新執行訊息重試已傳送給沒有回應的協調器。  
  
## <a name="description"></a>描述  
 追蹤本機異動管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「重新執行」訊息給上層協調器。  
  
## <a name="troubleshooting"></a>疑難排解  
 調查讓回應無法準時傳遞的潛在網路或產品問題。  如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。 這兩個問題都會大幅降低系統內的異動量。  
  
## <a name="see-also"></a>請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
