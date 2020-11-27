---
title: 每秒不確定的交易作業數
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 9162809ec467f282674e0ab21f7ce5e4d2222da4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249978"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="515d8-102">每秒不確定的交易作業數</span><span class="sxs-lookup"><span data-stu-id="515d8-102">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="515d8-103">計數器名稱：每秒不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="515d8-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="515d8-104">描述</span><span class="sxs-lookup"><span data-stu-id="515d8-104">Description</span></span>  

 <span data-ttu-id="515d8-105">每秒鐘此服務中結果不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="515d8-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="515d8-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="515d8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="515d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="515d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
