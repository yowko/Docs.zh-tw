---
title: 服務效能計數器
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810183"
---
# <a name="service-performance-counters"></a><span data-ttu-id="3edf6-102">服務效能計數器</span><span class="sxs-lookup"><span data-stu-id="3edf6-102">Service Performance Counters</span></span>
<span data-ttu-id="3edf6-103">服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。</span><span class="sxs-lookup"><span data-stu-id="3edf6-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="3edf6-104">以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。</span><span class="sxs-lookup"><span data-stu-id="3edf6-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="3edf6-105">執行個體會使用以下模式來命名：</span><span class="sxs-lookup"><span data-stu-id="3edf6-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="3edf6-106">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="3edf6-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="3edf6-107">當 Windows Communication Foundation (WCF) 計數器執行個體名稱超出最大長度時，WCF 會取代的雜湊值的執行個體名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="3edf6-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3edf6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3edf6-108">See Also</span></span>  
 [<span data-ttu-id="3edf6-109">效能計數器</span><span class="sxs-lookup"><span data-stu-id="3edf6-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
