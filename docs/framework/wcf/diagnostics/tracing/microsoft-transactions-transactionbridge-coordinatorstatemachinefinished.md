---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594409"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a>Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
協調器登記的狀態電腦已進入完成狀態。  
  
## <a name="description"></a>描述  
 當本機異動管理員相信上層協調器登記已完成 2pc 處理時，便會進行追蹤。 登記的結果可以是「已認可」、「已中止」或「已遺失」。 如果本機異動管理員在「準備」期間表決為 ReadOnly，也會進行追蹤。  
  
## <a name="see-also"></a>請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
