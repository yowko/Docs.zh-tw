---
title: 服務：每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5066108d8183502eeaec7c25186c00d9978261b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546929"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="23b72-102">服務：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="23b72-102">Service: Calls Per Second</span></span>
<span data-ttu-id="23b72-103">計數器名稱：每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="23b72-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="23b72-104">描述</span><span class="sxs-lookup"><span data-stu-id="23b72-104">Description</span></span>  
 <span data-ttu-id="23b72-105">對這個服務的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="23b72-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="23b72-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="23b72-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="23b72-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)，其中分子 (N) 表示最新樣本間隔期間的已執行作業數，分母 (D) 表示最新樣本間隔期間的已耗用時間，而 F 是刻度的頻率。</span><span class="sxs-lookup"><span data-stu-id="23b72-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
