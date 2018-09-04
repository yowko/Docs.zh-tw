---
title: 呼叫持續時間
ms.date: 03/30/2017
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
ms.openlocfilehash: a18e35ba351f6a87da9dd61af223aed2bf647dea
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525208"
---
# <a name="call-duration"></a><span data-ttu-id="7a094-102">呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="7a094-102">Call Duration</span></span>
<span data-ttu-id="7a094-103">計數器名稱：呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="7a094-103">Counter Name: Call Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="7a094-104">描述</span><span class="sxs-lookup"><span data-stu-id="7a094-104">Description</span></span>  
 <span data-ttu-id="7a094-105">這個作業呼叫的平均持續時間。</span><span class="sxs-lookup"><span data-stu-id="7a094-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="7a094-106">平均持續時間是根據此方程式計算而來：(N1-N0)/(D1-D0)。</span><span class="sxs-lookup"><span data-stu-id="7a094-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7a094-107">在非同步 WCF 服務上使用時，呼叫持續時間計數器一定會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="7a094-107">When used on an asynchronous WCF service the Call Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a094-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a094-108">See Also</span></span>  
 [<span data-ttu-id="7a094-109">PERF_AVERAGE_TIMER</span><span class="sxs-lookup"><span data-stu-id="7a094-109">PERF_AVERAGE_TIMER</span></span>](https://go.microsoft.com/fwlink/?LinkId=95015)
