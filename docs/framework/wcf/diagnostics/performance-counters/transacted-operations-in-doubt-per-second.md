---
title: 每秒不確定的交易作業數
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169901"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="1eaf8-102">每秒不確定的交易作業數</span><span class="sxs-lookup"><span data-stu-id="1eaf8-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="1eaf8-103">計數器名稱：每秒不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="1eaf8-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1eaf8-104">描述</span><span class="sxs-lookup"><span data-stu-id="1eaf8-104">Description</span></span>  
 <span data-ttu-id="1eaf8-105">每秒鐘此服務中結果不確定的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="1eaf8-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="1eaf8-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="1eaf8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1eaf8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1eaf8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
