---
title: 每秒佇列拒絕的訊息數
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 2b7686ee94ab051bc255bdb71681c8d1c473094c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276200"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="c6168-102">每秒佇列拒絕的訊息數</span><span class="sxs-lookup"><span data-stu-id="c6168-102">Queued Rejected Messages Per Second</span></span>

<span data-ttu-id="c6168-103">計數器名稱：每秒拒絕的佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="c6168-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6168-104">描述</span><span class="sxs-lookup"><span data-stu-id="c6168-104">Description</span></span>  

 <span data-ttu-id="c6168-105">此服務的佇列傳輸每秒拒絕的訊息數。</span><span class="sxs-lookup"><span data-stu-id="c6168-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="c6168-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="c6168-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c6168-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c6168-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
