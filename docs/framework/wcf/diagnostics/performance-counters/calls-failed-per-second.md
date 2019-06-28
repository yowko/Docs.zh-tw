---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: aa8cd4c2d9f642b525b2b9ccb931c4f2101a5129
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421794"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="90e8a-102">每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="90e8a-102">Calls Failed Per Second</span></span>
<span data-ttu-id="90e8a-103">計數器名稱：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="90e8a-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="90e8a-104">描述</span><span class="sxs-lookup"><span data-stu-id="90e8a-104">Description</span></span>  
 <span data-ttu-id="90e8a-105">此作業中包含每秒未處理例外狀況的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="90e8a-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="90e8a-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="90e8a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="90e8a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="90e8a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="90e8a-108">此計數器會遞增每次此作業中發生未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="90e8a-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e8a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e8a-109">See also</span></span>

- [<span data-ttu-id="90e8a-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="90e8a-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
