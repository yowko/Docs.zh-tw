---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: deb29820aab09adad8825a299145772892117948
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250004"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="9f254-102">每秒認可的交易作業數</span><span class="sxs-lookup"><span data-stu-id="9f254-102">Transacted Operations Committed Per Second</span></span>

<span data-ttu-id="9f254-103">計數器名稱：每秒認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="9f254-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f254-104">描述</span><span class="sxs-lookup"><span data-stu-id="9f254-104">Description</span></span>  

 <span data-ttu-id="9f254-105">此服務每秒所認可的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="9f254-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="9f254-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="9f254-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9f254-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9f254-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
