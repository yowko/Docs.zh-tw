---
title: "每秒佇列捨棄的訊息數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8512c757f7a18172b267fe7d3469b1a2749818aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="39293-102">每秒佇列捨棄的訊息數</span><span class="sxs-lookup"><span data-stu-id="39293-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="39293-103">計數器名稱：每秒捨棄的佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="39293-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="39293-104">描述</span><span class="sxs-lookup"><span data-stu-id="39293-104">Description</span></span>  
 <span data-ttu-id="39293-105">此服務的佇列傳輸每秒捨棄的訊息數。</span><span class="sxs-lookup"><span data-stu-id="39293-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="39293-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="39293-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="39293-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="39293-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
