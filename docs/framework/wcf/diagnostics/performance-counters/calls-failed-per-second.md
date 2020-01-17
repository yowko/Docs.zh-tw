---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 110ee5c264094f80d5c7c6542c3e388e758e1665
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163159"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="e2628-102">每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="e2628-102">Calls Failed Per Second</span></span>
<span data-ttu-id="e2628-103">計數器名稱：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="e2628-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2628-104">描述</span><span class="sxs-lookup"><span data-stu-id="e2628-104">Description</span></span>  
 <span data-ttu-id="e2628-105">此作業中包含每秒未處理例外狀況的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="e2628-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="e2628-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="e2628-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e2628-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e2628-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e2628-108">每次此作業中有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="e2628-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2628-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2628-109">See also</span></span>

- [<span data-ttu-id="e2628-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="e2628-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
