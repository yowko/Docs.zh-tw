---
title: "端點：每秒的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480e0758df7e3062f9bd2b0b089c7a9b75e1c012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="50c4b-102">端點：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="50c4b-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="50c4b-103">計數器名稱：每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="50c4b-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="50c4b-104">描述</span><span class="sxs-lookup"><span data-stu-id="50c4b-104">Description</span></span>  
 <span data-ttu-id="50c4b-105">對這個端點的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="50c4b-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="50c4b-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="50c4b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="50c4b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="50c4b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
