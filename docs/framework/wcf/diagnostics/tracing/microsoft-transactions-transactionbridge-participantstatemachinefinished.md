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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53ac142c8c7d8004020210ffb3c0dcb2355a5b61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="1e220-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="1e220-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="1e220-103">參與者登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="1e220-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e220-104">描述</span><span class="sxs-lookup"><span data-stu-id="1e220-104">Description</span></span>  
 <span data-ttu-id="1e220-105">當下層參與者登記的 2pc 程序已完成時，即進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e220-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="1e220-106">登記的結果可以是「已認可」或「已中止」。</span><span class="sxs-lookup"><span data-stu-id="1e220-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="1e220-107">如果任何參與者在「準備」期間表決為 ReadOnly 時，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e220-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e220-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e220-108">See Also</span></span>  
 [<span data-ttu-id="1e220-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="1e220-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1e220-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1e220-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1e220-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="1e220-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
