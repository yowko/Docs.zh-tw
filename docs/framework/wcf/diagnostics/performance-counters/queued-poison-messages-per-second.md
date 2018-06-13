---
title: 每秒佇列的有害訊息數
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473255"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="b3462-102">每秒佇列的有害訊息數</span><span class="sxs-lookup"><span data-stu-id="b3462-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="b3462-103">計數器名稱：每秒佇列的有害訊息數。</span><span class="sxs-lookup"><span data-stu-id="b3462-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3462-104">描述</span><span class="sxs-lookup"><span data-stu-id="b3462-104">Description</span></span>  
 <span data-ttu-id="b3462-105">此服務佇列傳輸標示為有害的每秒訊息數量。</span><span class="sxs-lookup"><span data-stu-id="b3462-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="b3462-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="b3462-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b3462-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b3462-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
