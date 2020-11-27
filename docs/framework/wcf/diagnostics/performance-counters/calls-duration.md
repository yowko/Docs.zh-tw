---
title: 呼叫持續時間
ms.date: 03/30/2017
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
ms.openlocfilehash: 99b4f62182c7864fd32b878373814e85926025b5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285495"
---
# <a name="calls-duration"></a><span data-ttu-id="239f1-102">呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="239f1-102">Calls Duration</span></span>

<span data-ttu-id="239f1-103">計數器名稱：呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="239f1-103">Counter Name: Calls Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="239f1-104">描述</span><span class="sxs-lookup"><span data-stu-id="239f1-104">Description</span></span>  

 <span data-ttu-id="239f1-105">這個作業呼叫的平均持續時間。</span><span class="sxs-lookup"><span data-stu-id="239f1-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="239f1-106">平均持續時間是根據此方程式計算而來：(N1-N0)/(D1-D0)。</span><span class="sxs-lookup"><span data-stu-id="239f1-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="239f1-107">在非同步 WCF 服務上使用時，呼叫持續時間計數器一律會傳回-1。</span><span class="sxs-lookup"><span data-stu-id="239f1-107">When used on an asynchronous WCF service the Calls Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239f1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="239f1-108">See also</span></span>

- <span data-ttu-id="239f1-109">[PERF_AVERAGE_TIMER](/previous-versions/windows/embedded/ms938538(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="239f1-109">[PERF_AVERAGE_TIMER](/previous-versions/windows/embedded/ms938538(v=msdn.10))</span></span>
