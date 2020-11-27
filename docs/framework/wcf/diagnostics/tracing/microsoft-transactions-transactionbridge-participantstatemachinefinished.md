---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: bd6c9124e6346437e2bb35df620e00bad13b60f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258942"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a>Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished

參與者登記的狀態電腦已進入完成狀態。  
  
## <a name="description"></a>描述  

 當下層參與者登記的 2pc 程序已完成時，即進行追蹤。 登記的結果可以是「已認可」或「已中止」。 如果任何參與者在「準備」期間表決為 ReadOnly 時，也會進行追蹤。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
