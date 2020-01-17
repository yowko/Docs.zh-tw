---
title: 服務：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: e165348a71101b21fa66bd4907c43335b1e476e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163978"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="ca68f-102">服務：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="ca68f-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="ca68f-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="ca68f-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ca68f-104">描述</span><span class="sxs-lookup"><span data-stu-id="ca68f-104">Description</span></span>  
 <span data-ttu-id="ca68f-105">未處理之例外狀況的呼叫數，以及此服務在一秒之內所收到的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="ca68f-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="ca68f-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="ca68f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ca68f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ca68f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ca68f-108">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca68f-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="ca68f-109">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca68f-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="ca68f-110">每當此服務有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="ca68f-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca68f-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca68f-111">See also</span></span>

- [<span data-ttu-id="ca68f-112">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="ca68f-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
