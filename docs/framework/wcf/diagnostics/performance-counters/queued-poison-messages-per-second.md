---
title: 每秒佇列的有害訊息數
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 1e515a81580bd9773841bee4230288d8c7d12216
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276226"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="caa48-102">每秒佇列的有害訊息數</span><span class="sxs-lookup"><span data-stu-id="caa48-102">Queued Poison Messages Per Second</span></span>

<span data-ttu-id="caa48-103">計數器名稱：每秒佇列的有害訊息數。</span><span class="sxs-lookup"><span data-stu-id="caa48-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="caa48-104">描述</span><span class="sxs-lookup"><span data-stu-id="caa48-104">Description</span></span>  

 <span data-ttu-id="caa48-105">此服務佇列傳輸標示為有害的每秒訊息數量。</span><span class="sxs-lookup"><span data-stu-id="caa48-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="caa48-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="caa48-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="caa48-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="caa48-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
