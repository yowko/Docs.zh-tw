---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: bffaed4976d82202eaea9ce50f6d389548fdabfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144819"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="2c1af-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="2c1af-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="2c1af-103">協調器登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="2c1af-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c1af-104">描述</span><span class="sxs-lookup"><span data-stu-id="2c1af-104">Description</span></span>  
 <span data-ttu-id="2c1af-105">當本機異動管理員相信上層協調器登記已完成 2pc 處理時，便會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1af-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="2c1af-106">登記的結果可以是「已認可」、「已中止」或「已遺失」。</span><span class="sxs-lookup"><span data-stu-id="2c1af-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="2c1af-107">如果本機異動管理員在「準備」期間表決為 ReadOnly，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1af-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1af-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c1af-108">See also</span></span>

- [<span data-ttu-id="2c1af-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="2c1af-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="2c1af-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2c1af-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2c1af-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2c1af-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
