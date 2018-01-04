---
title: "端點效能計數器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc5fa1b3600489cb2d5f31c263019ae5006edf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="2cfe1-102">端點效能計數器</span><span class="sxs-lookup"><span data-stu-id="2cfe1-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="2cfe1-103">端點效能計數器會擷取顯示端點如何接受訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="2cfe1-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="2cfe1-104">使用效能監視器檢視時，可以在 `ServiceModelEndpoint 4.0.0.0` 效能物件下找到它們。</span><span class="sxs-lookup"><span data-stu-id="2cfe1-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="2cfe1-105">執行個體是使用下列模式來命名：</span><span class="sxs-lookup"><span data-stu-id="2cfe1-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="2cfe1-106">此資料與針對個別作業而收集的資料類似，但只彙總了端點之間的資料。</span><span class="sxs-lookup"><span data-stu-id="2cfe1-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2cfe1-107">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="2cfe1-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="2cfe1-108">當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 計數器執行個體名稱超出最大長度時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會以雜湊值取代此執行個體名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="2cfe1-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfe1-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="2cfe1-109">See Also</span></span>  
 [<span data-ttu-id="2cfe1-110">效能計數器</span><span class="sxs-lookup"><span data-stu-id="2cfe1-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
