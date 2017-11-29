---
title: "服務：每秒的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 940249c4ec0317013efcb03aafc11d384ec0363f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-per-second"></a><span data-ttu-id="664e5-102">服務：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="664e5-102">Service: Calls Per Second</span></span>
<span data-ttu-id="664e5-103">計數器名稱：每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="664e5-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="664e5-104">描述</span><span class="sxs-lookup"><span data-stu-id="664e5-104">Description</span></span>  
 <span data-ttu-id="664e5-105">對這個服務的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="664e5-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="664e5-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="664e5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="664e5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)，其中分子 (N) 表示最新樣本間隔期間的已執行作業數，分母 (D) 表示最新樣本間隔期間的已耗用時間，而 F 是刻度的頻率。</span><span class="sxs-lookup"><span data-stu-id="664e5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
