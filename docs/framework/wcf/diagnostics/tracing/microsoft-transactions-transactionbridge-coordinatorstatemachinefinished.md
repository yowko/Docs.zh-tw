---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f99670d61df45edfef5350da080f12e892a0f74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="595b3-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="595b3-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="595b3-103">協調器登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="595b3-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="595b3-104">描述</span><span class="sxs-lookup"><span data-stu-id="595b3-104">Description</span></span>  
 <span data-ttu-id="595b3-105">當本機交易管理員相信上層協調器登記已完成 2pc 處理時，便會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="595b3-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="595b3-106">登記的結果可以是「已認可」、「已中止」或「已遺失」。</span><span class="sxs-lookup"><span data-stu-id="595b3-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="595b3-107">如果本機異動管理員在「準備」期間表決為 ReadOnly，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="595b3-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595b3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="595b3-108">See Also</span></span>  
 [<span data-ttu-id="595b3-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="595b3-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="595b3-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="595b3-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="595b3-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="595b3-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
