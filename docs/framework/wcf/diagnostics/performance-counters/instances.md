---
title: 執行個體
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473038"
---
# <a name="instances"></a><span data-ttu-id="12a60-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="12a60-102">Instances</span></span>
<span data-ttu-id="12a60-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="12a60-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="12a60-104">描述</span><span class="sxs-lookup"><span data-stu-id="12a60-104">Description</span></span>  
 <span data-ttu-id="12a60-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="12a60-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="12a60-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="12a60-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="12a60-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="12a60-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="12a60-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="12a60-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="12a60-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="12a60-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a60-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12a60-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
