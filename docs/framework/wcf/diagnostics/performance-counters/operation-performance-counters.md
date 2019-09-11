---
title: 作業效能計數器
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 31b0f92ae3477bd3c1de8c348a60e5c64d7c53cc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855689"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="08dce-102">作業效能計數器</span><span class="sxs-lookup"><span data-stu-id="08dce-102">Operation Performance Counters</span></span>
<span data-ttu-id="08dce-103">當使用效能監視器 (Perfmon.exe) 檢視時，您可以在 `ServiceModelOperation 4.0.0.0` 效能物件中找到作業效能計數器。</span><span class="sxs-lookup"><span data-stu-id="08dce-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="08dce-104">每個作業都有個別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="08dce-104">Each operation has an individual instance.</span></span> <span data-ttu-id="08dce-105">也就是，如果指定的合約有 10 個作業，就會有 10 個作業計數器執行個體與該合約產生關聯。</span><span class="sxs-lookup"><span data-stu-id="08dce-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="08dce-106">物件執行個體會使用以下模式來命名：</span><span class="sxs-lookup"><span data-stu-id="08dce-106">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="08dce-107">這個計數器能夠讓您測量呼叫的使用狀況，以及作業的執行效能。</span><span class="sxs-lookup"><span data-stu-id="08dce-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="08dce-108">效能計數器執行個體的名稱具有長度限制。</span><span class="sxs-lookup"><span data-stu-id="08dce-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="08dce-109">當 Windows Communication Foundation （WCF）計數器實例名稱超過最大長度時，WCF 會以雜湊值取代實例名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="08dce-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dce-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08dce-110">See also</span></span>

- [<span data-ttu-id="08dce-111">效能計數器</span><span class="sxs-lookup"><span data-stu-id="08dce-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
