---
title: 每秒不確定的交易作業數
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 59186b1fc113bb87264a8b946cfee2719ff50b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550595"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="59c1b-102">每秒不確定的交易作業數</span><span class="sxs-lookup"><span data-stu-id="59c1b-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="59c1b-103">計數器名稱：每秒不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="59c1b-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59c1b-104">描述</span><span class="sxs-lookup"><span data-stu-id="59c1b-104">Description</span></span>  
 <span data-ttu-id="59c1b-105">每秒鐘此服務中結果不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="59c1b-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="59c1b-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="59c1b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="59c1b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="59c1b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
