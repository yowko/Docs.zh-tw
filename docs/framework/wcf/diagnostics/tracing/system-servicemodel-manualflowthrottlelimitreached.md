---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35f149423fc8c0cd2a25834742d7c8b79ad8d8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="a6fc4-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="a6fc4-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="a6fc4-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="a6fc4-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="a6fc4-104">描述</span><span class="sxs-lookup"><span data-stu-id="a6fc4-104">Description</span></span>  
 <span data-ttu-id="a6fc4-105">系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="a6fc4-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="a6fc4-106">您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。</span><span class="sxs-lookup"><span data-stu-id="a6fc4-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="a6fc4-107">當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="a6fc4-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="a6fc4-108">以後再變更為 0 時將不會被追蹤。</span><span class="sxs-lookup"><span data-stu-id="a6fc4-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="a6fc4-109">執行個體內容上的流量控制限制只會針對每個內容追蹤一次。</span><span class="sxs-lookup"><span data-stu-id="a6fc4-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fc4-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6fc4-110">See Also</span></span>  
 [<span data-ttu-id="a6fc4-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="a6fc4-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a6fc4-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a6fc4-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a6fc4-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="a6fc4-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
