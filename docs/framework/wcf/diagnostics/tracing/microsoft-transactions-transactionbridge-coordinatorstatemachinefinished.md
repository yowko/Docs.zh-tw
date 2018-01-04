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
ms.workload: dotnet
ms.openlocfilehash: 960166c7c1d91bcab8420a55e633b461bf37c626
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="f573e-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="f573e-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="f573e-103">協調器登記的狀態電腦已進入完成狀態。</span><span class="sxs-lookup"><span data-stu-id="f573e-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f573e-104">描述</span><span class="sxs-lookup"><span data-stu-id="f573e-104">Description</span></span>  
 <span data-ttu-id="f573e-105">當本機異動管理員相信上層協調器登記已完成 2pc 處理時，便會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="f573e-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="f573e-106">登記的結果可以是「已認可」、「已中止」或「已遺失」。</span><span class="sxs-lookup"><span data-stu-id="f573e-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="f573e-107">如果本機異動管理員在「準備」期間表決為 ReadOnly，也會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="f573e-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f573e-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="f573e-108">See Also</span></span>  
 [<span data-ttu-id="f573e-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="f573e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f573e-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="f573e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f573e-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f573e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
