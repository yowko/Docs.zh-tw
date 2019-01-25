---
title: 執行個體
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 1b2801b5df3a5d2ca6d7fd03299ecdf4b7df426a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520256"
---
# <a name="instances"></a><span data-ttu-id="caffa-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="caffa-102">Instances</span></span>
<span data-ttu-id="caffa-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="caffa-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="caffa-104">描述</span><span class="sxs-lookup"><span data-stu-id="caffa-104">Description</span></span>  
 <span data-ttu-id="caffa-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="caffa-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="caffa-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="caffa-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="caffa-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="caffa-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="caffa-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="caffa-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="caffa-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="caffa-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caffa-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caffa-110">See also</span></span>
- <xref:System.ServiceModel.OperationBehaviorAttribute>
