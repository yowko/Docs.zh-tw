---
title: 每秒不確定的交易作業數
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e165e934f17d599a9bb89f2702bb74d1ba0bf633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474307"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="6af95-102">每秒不確定的交易作業數</span><span class="sxs-lookup"><span data-stu-id="6af95-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="6af95-103">計數器名稱：每秒不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="6af95-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6af95-104">描述</span><span class="sxs-lookup"><span data-stu-id="6af95-104">Description</span></span>  
 <span data-ttu-id="6af95-105">每秒鐘此服務中結果不確定的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="6af95-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="6af95-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="6af95-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6af95-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6af95-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
