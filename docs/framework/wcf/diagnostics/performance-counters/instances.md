---
title: 執行個體
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975581"
---
# <a name="instances"></a><span data-ttu-id="93207-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="93207-102">Instances</span></span>
<span data-ttu-id="93207-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="93207-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="93207-104">描述</span><span class="sxs-lookup"><span data-stu-id="93207-104">Description</span></span>  
 <span data-ttu-id="93207-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="93207-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="93207-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="93207-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="93207-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93207-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="93207-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93207-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="93207-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="93207-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93207-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93207-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
