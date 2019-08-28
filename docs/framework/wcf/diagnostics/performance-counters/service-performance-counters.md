---
title: 服務效能計數器
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 18a9e6336b70341f5da9c7b73cbd3f9bd3f958c7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044278"
---
# <a name="service-performance-counters"></a><span data-ttu-id="42f49-102">服務效能計數器</span><span class="sxs-lookup"><span data-stu-id="42f49-102">Service Performance Counters</span></span>
<span data-ttu-id="42f49-103">服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。</span><span class="sxs-lookup"><span data-stu-id="42f49-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="42f49-104">以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。</span><span class="sxs-lookup"><span data-stu-id="42f49-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="42f49-105">執行個體會使用以下模式來命名：</span><span class="sxs-lookup"><span data-stu-id="42f49-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
> <span data-ttu-id="42f49-106">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="42f49-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="42f49-107">當 Windows Communication Foundation (WCF) 計數器實例名稱超過最大長度時, WCF 會以雜湊值取代實例名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="42f49-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f49-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42f49-108">See also</span></span>

- [<span data-ttu-id="42f49-109">效能計數器</span><span class="sxs-lookup"><span data-stu-id="42f49-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
