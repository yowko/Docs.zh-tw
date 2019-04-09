---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178616"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="1a80f-102">每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="1a80f-102">Calls Failed Per Second</span></span>
<span data-ttu-id="1a80f-103">計數器名稱：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="1a80f-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a80f-104">描述</span><span class="sxs-lookup"><span data-stu-id="1a80f-104">Description</span></span>  
 <span data-ttu-id="1a80f-105">此作業中包含每秒未處理例外狀況的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="1a80f-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="1a80f-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="1a80f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1a80f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1a80f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="1a80f-108">每當此作業含有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="1a80f-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a80f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a80f-109">See also</span></span>

- [<span data-ttu-id="1a80f-110">指定與處理合約和服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="1a80f-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
