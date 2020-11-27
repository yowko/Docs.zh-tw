---
title: 執行個體
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: f4bf639e626945c7e753ac352dfecc7a79541bfd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266073"
---
# <a name="instances"></a><span data-ttu-id="a91f9-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="a91f9-102">Instances</span></span>

<span data-ttu-id="a91f9-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="a91f9-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a91f9-104">描述</span><span class="sxs-lookup"><span data-stu-id="a91f9-104">Description</span></span>  

 <span data-ttu-id="a91f9-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="a91f9-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="a91f9-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="a91f9-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="a91f9-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a91f9-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="a91f9-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a91f9-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="a91f9-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a91f9-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91f9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a91f9-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
