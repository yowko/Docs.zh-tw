---
title: 端點：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321464"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="2f0c1-102">端點：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="2f0c1-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="2f0c1-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="2f0c1-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f0c1-104">描述</span><span class="sxs-lookup"><span data-stu-id="2f0c1-104">Description</span></span>  
 <span data-ttu-id="2f0c1-105">具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="2f0c1-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2f0c1-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="2f0c1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2f0c1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2f0c1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="2f0c1-108">每當這個端點有未處理的例外狀況時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="2f0c1-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0c1-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f0c1-109">See also</span></span>

- [<span data-ttu-id="2f0c1-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="2f0c1-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
