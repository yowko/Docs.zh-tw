---
title: 每秒佇列的有害訊息數
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509335"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="dadd9-102">每秒佇列的有害訊息數</span><span class="sxs-lookup"><span data-stu-id="dadd9-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="dadd9-103">計數器名稱：每秒佇列的有害訊息數。</span><span class="sxs-lookup"><span data-stu-id="dadd9-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dadd9-104">描述</span><span class="sxs-lookup"><span data-stu-id="dadd9-104">Description</span></span>  
 <span data-ttu-id="dadd9-105">此服務佇列傳輸標示為有害的每秒訊息數量。</span><span class="sxs-lookup"><span data-stu-id="dadd9-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="dadd9-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="dadd9-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="dadd9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="dadd9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
