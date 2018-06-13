---
title: 每秒佇列捨棄的訊息數
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 47835086a4ee920e814d9dd6c1e41b9cdc33efec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471465"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="e2974-102">每秒佇列捨棄的訊息數</span><span class="sxs-lookup"><span data-stu-id="e2974-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="e2974-103">計數器名稱：每秒捨棄的佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="e2974-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2974-104">描述</span><span class="sxs-lookup"><span data-stu-id="e2974-104">Description</span></span>  
 <span data-ttu-id="e2974-105">此服務的佇列傳輸每秒捨棄的訊息數。</span><span class="sxs-lookup"><span data-stu-id="e2974-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="e2974-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="e2974-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e2974-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e2974-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
