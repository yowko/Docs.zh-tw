---
title: 端點效能計數器
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803133"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="43917-102">端點效能計數器</span><span class="sxs-lookup"><span data-stu-id="43917-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="43917-103">端點效能計數器會擷取顯示端點如何接受訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="43917-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="43917-104">使用效能監視器檢視時，可以在 `ServiceModelEndpoint 4.0.0.0` 效能物件下找到它們。</span><span class="sxs-lookup"><span data-stu-id="43917-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="43917-105">執行個體是使用下列模式來命名：</span><span class="sxs-lookup"><span data-stu-id="43917-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="43917-106">此資料與針對個別作業而收集的資料類似，但只彙總了端點之間的資料。</span><span class="sxs-lookup"><span data-stu-id="43917-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="43917-107">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="43917-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="43917-108">當 Windows Communication Foundation (WCF) 計數器執行個體名稱超出最大長度時，WCF 會取代的雜湊值的執行個體名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="43917-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43917-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43917-109">See Also</span></span>  
 [<span data-ttu-id="43917-110">效能計數器</span><span class="sxs-lookup"><span data-stu-id="43917-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
