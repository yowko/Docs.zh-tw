---
title: "執行個體"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87423c3de551cb9fbf8c5a7756e2f0f999129a3b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="instances"></a><span data-ttu-id="32900-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="32900-102">Instances</span></span>
<span data-ttu-id="32900-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="32900-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="32900-104">描述</span><span class="sxs-lookup"><span data-stu-id="32900-104">Description</span></span>  
 <span data-ttu-id="32900-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="32900-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="32900-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="32900-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="32900-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32900-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="32900-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="32900-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="32900-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="32900-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32900-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32900-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
