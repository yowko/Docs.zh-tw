---
title: 呼叫持續時間
ms.date: 03/30/2017
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
ms.openlocfilehash: 9d565088d90456ca7d2e56cb06e2267f4423aac7
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987190"
---
# <a name="calls-duration"></a><span data-ttu-id="70ea8-102">呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="70ea8-102">Calls Duration</span></span>
<span data-ttu-id="70ea8-103">計數器名稱:呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="70ea8-103">Counter Name: Calls Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="70ea8-104">說明</span><span class="sxs-lookup"><span data-stu-id="70ea8-104">Description</span></span>  
 <span data-ttu-id="70ea8-105">這個作業呼叫的平均持續時間。</span><span class="sxs-lookup"><span data-stu-id="70ea8-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="70ea8-106">平均持續時間是根據這個方程式來計算:(N1-N0)/(D1-D0)。</span><span class="sxs-lookup"><span data-stu-id="70ea8-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="70ea8-107">在非同步 WCF 服務上使用時, 呼叫持續時間計數器一律會傳回-1。</span><span class="sxs-lookup"><span data-stu-id="70ea8-107">When used on an asynchronous WCF service the Calls Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ea8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ea8-108">See also</span></span>

- [<span data-ttu-id="70ea8-109">PERF_AVERAGE_TIMER</span><span class="sxs-lookup"><span data-stu-id="70ea8-109">PERF_AVERAGE_TIMER</span></span>](https://go.microsoft.com/fwlink/?LinkId=95015)
