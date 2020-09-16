---
title: 端點：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 97e887bd04cd7a755ce38914ace6de39ac871687
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545712"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="cb4bb-102">端點：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="cb4bb-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="cb4bb-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="cb4bb-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cb4bb-104">描述</span><span class="sxs-lookup"><span data-stu-id="cb4bb-104">Description</span></span>  
 <span data-ttu-id="cb4bb-105">具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="cb4bb-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="cb4bb-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="cb4bb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cb4bb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cb4bb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="cb4bb-108">每當這個端點有未處理的例外狀況時，這個計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="cb4bb-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4bb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb4bb-109">See also</span></span>

- [<span data-ttu-id="cb4bb-110">指定與處理合約和服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="cb4bb-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
