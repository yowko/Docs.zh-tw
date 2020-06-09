---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594357"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="88828-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="88828-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="88828-103">參與者登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="88828-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88828-104">描述</span><span class="sxs-lookup"><span data-stu-id="88828-104">Description</span></span>  
 <span data-ttu-id="88828-105">當下層參與者登記的 2pc 程序已完成時，即進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="88828-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="88828-106">登記的結果可以是「已認可」或「已中止」。</span><span class="sxs-lookup"><span data-stu-id="88828-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="88828-107">如果任何參與者在「準備」期間表決為 ReadOnly 時，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="88828-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88828-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="88828-108">See also</span></span>

- [<span data-ttu-id="88828-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="88828-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="88828-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="88828-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="88828-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="88828-111">Administration and Diagnostics</span></span>](../index.md)
