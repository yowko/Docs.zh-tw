---
title: 服務：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 9cd649788e1304c68caa1bbf4b5fd27e6fc9d508
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861812"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="cac14-102">服務：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="cac14-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="cac14-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="cac14-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cac14-104">描述</span><span class="sxs-lookup"><span data-stu-id="cac14-104">Description</span></span>  
 <span data-ttu-id="cac14-105">未處理之例外狀況的呼叫數，以及此服務在一秒之內所收到的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="cac14-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="cac14-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="cac14-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cac14-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cac14-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="cac14-108">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cac14-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="cac14-109">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cac14-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="cac14-110">每當此服務有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="cac14-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac14-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cac14-111">See Also</span></span>  
 [<span data-ttu-id="cac14-112">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="cac14-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
