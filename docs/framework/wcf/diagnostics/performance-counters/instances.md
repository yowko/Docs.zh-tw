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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="baaaa-102">執行個體</span><span class="sxs-lookup"><span data-stu-id="baaaa-102">Instances</span></span>
<span data-ttu-id="baaaa-103">計數器名稱：執行個體。</span><span class="sxs-lookup"><span data-stu-id="baaaa-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="baaaa-104">描述</span><span class="sxs-lookup"><span data-stu-id="baaaa-104">Description</span></span>  
 <span data-ttu-id="baaaa-105">服務目前包含的執行個體內容數。</span><span class="sxs-lookup"><span data-stu-id="baaaa-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="baaaa-106">多數時候，執行個體內容數會與執行個體數相同。</span><span class="sxs-lookup"><span data-stu-id="baaaa-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="baaaa-107">不過，下列案例為此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="baaaa-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="baaaa-108">服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="baaaa-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="baaaa-109"><xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="baaaa-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaaa-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baaaa-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
