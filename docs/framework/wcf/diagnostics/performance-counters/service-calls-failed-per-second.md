---
title: 服務：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315781"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="c0c51-102">服務：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="c0c51-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="c0c51-103">計數器名稱：每秒失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="c0c51-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c0c51-104">描述</span><span class="sxs-lookup"><span data-stu-id="c0c51-104">Description</span></span>  
 <span data-ttu-id="c0c51-105">未處理之例外狀況的呼叫數，以及此服務在一秒之內所收到的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="c0c51-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="c0c51-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="c0c51-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c0c51-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c0c51-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="c0c51-108">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0c51-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="c0c51-109">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0c51-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="c0c51-110">每當此服務有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="c0c51-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c51-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c51-111">See also</span></span>

- [<span data-ttu-id="c0c51-112">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="c0c51-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
