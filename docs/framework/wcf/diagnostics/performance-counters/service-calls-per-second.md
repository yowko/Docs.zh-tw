---
title: 服務：每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499883"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="57635-102">服務：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="57635-102">Service: Calls Per Second</span></span>
<span data-ttu-id="57635-103">計數器名稱：每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="57635-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="57635-104">描述</span><span class="sxs-lookup"><span data-stu-id="57635-104">Description</span></span>  
 <span data-ttu-id="57635-105">對這個服務的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="57635-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="57635-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="57635-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="57635-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)，其中分子 (N) 表示最新樣本間隔期間的已執行作業數，分母 (D) 表示最新樣本間隔期間的已耗用時間，而 F 是刻度的頻率。</span><span class="sxs-lookup"><span data-stu-id="57635-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
