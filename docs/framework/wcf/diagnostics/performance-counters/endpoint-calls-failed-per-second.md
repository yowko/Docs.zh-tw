---
title: "端點：每秒失敗的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6aaf1e504909805a542840fe92a6591c9083d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="ac7ba-102">端點：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="ac7ba-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="ac7ba-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="ac7ba-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ac7ba-104">描述</span><span class="sxs-lookup"><span data-stu-id="ac7ba-104">Description</span></span>  
 <span data-ttu-id="ac7ba-105">具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="ac7ba-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="ac7ba-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="ac7ba-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ac7ba-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ac7ba-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ac7ba-108">每當這個端點有未處理的例外狀況時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="ac7ba-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7ba-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac7ba-109">See Also</span></span>  
 [<span data-ttu-id="ac7ba-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="ac7ba-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
