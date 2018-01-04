---
title: "服務效能計數器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8145ff12f5a9befdef3cbf5edf69e5162c4d7014
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="99dc6-102">服務效能計數器</span><span class="sxs-lookup"><span data-stu-id="99dc6-102">Service Performance Counters</span></span>
<span data-ttu-id="99dc6-103">服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。</span><span class="sxs-lookup"><span data-stu-id="99dc6-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="99dc6-104">以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。</span><span class="sxs-lookup"><span data-stu-id="99dc6-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="99dc6-105">執行個體會使用以下模式來命名：</span><span class="sxs-lookup"><span data-stu-id="99dc6-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="99dc6-106">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="99dc6-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="99dc6-107">當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 計數器執行個體名稱超出最大長度時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會以雜湊值取代此執行個體名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="99dc6-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99dc6-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="99dc6-108">See Also</span></span>  
 [<span data-ttu-id="99dc6-109">效能計數器</span><span class="sxs-lookup"><span data-stu-id="99dc6-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
