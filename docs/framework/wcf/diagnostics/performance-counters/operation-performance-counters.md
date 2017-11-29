---
title: "作業效能計數器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="535a1-102">作業效能計數器</span><span class="sxs-lookup"><span data-stu-id="535a1-102">Operation Performance Counters</span></span>
<span data-ttu-id="535a1-103">當使用效能監視器 (Perfmon.exe) 檢視時，您可以在 `ServiceModelOperation 4.0.0.0` 效能物件中找到作業效能計數器。</span><span class="sxs-lookup"><span data-stu-id="535a1-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="535a1-104">每個作業都有個別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="535a1-104">Each operation has an individual instance.</span></span> <span data-ttu-id="535a1-105">也就是，如果指定的合約有 10 個作業，就會有 10 個作業計數器執行個體與該合約產生關聯。</span><span class="sxs-lookup"><span data-stu-id="535a1-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="535a1-106">物件執行個體會使用以下模式來命名：</span><span class="sxs-lookup"><span data-stu-id="535a1-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="535a1-107">這個計數器能夠讓您測量呼叫的使用狀況，以及作業的執行效能。</span><span class="sxs-lookup"><span data-stu-id="535a1-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="535a1-108">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="535a1-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="535a1-109">當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 計數器執行個體名稱超出最大長度時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會以雜湊值取代此執行個體名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="535a1-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535a1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="535a1-110">See Also</span></span>  
 [<span data-ttu-id="535a1-111">效能計數器</span><span class="sxs-lookup"><span data-stu-id="535a1-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
