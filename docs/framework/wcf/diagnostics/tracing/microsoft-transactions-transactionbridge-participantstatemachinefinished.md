---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 56eb40d4e8b2580ba094e67552872cf558c8a617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642291"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="04728-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="04728-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="04728-103">參與者登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="04728-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="04728-104">描述</span><span class="sxs-lookup"><span data-stu-id="04728-104">Description</span></span>  
 <span data-ttu-id="04728-105">當下層參與者登記的 2pc 程序已完成時，即進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="04728-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="04728-106">登記的結果可以是「已認可」或「已中止」。</span><span class="sxs-lookup"><span data-stu-id="04728-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="04728-107">如果任何參與者在「準備」期間表決為 ReadOnly 時，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="04728-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04728-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04728-108">See also</span></span>
- [<span data-ttu-id="04728-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="04728-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="04728-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="04728-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="04728-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="04728-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
