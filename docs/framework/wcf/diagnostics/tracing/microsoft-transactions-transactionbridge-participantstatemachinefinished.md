---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90989d6b83ea5b54d5ed476d58a5d7f6e32f1fed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="b1240-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="b1240-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="b1240-103">參與者登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="b1240-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b1240-104">描述</span><span class="sxs-lookup"><span data-stu-id="b1240-104">Description</span></span>  
 <span data-ttu-id="b1240-105">當下層參與者登記的 2pc 程序已完成時，即進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b1240-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="b1240-106">登記的結果可以是「已認可」或「已中止」。</span><span class="sxs-lookup"><span data-stu-id="b1240-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="b1240-107">如果任何參與者在「準備」期間表決為 ReadOnly 時，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b1240-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1240-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1240-108">See Also</span></span>  
 [<span data-ttu-id="b1240-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="b1240-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b1240-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b1240-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b1240-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b1240-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
