---
title: 每秒佇列捨棄的訊息數
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528119"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="713c0-102">每秒佇列捨棄的訊息數</span><span class="sxs-lookup"><span data-stu-id="713c0-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="713c0-103">計數器名稱：每秒捨棄的佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="713c0-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="713c0-104">描述</span><span class="sxs-lookup"><span data-stu-id="713c0-104">Description</span></span>  
 <span data-ttu-id="713c0-105">此服務的佇列傳輸每秒捨棄的訊息數。</span><span class="sxs-lookup"><span data-stu-id="713c0-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="713c0-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="713c0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="713c0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="713c0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
