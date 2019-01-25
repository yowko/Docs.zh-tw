---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597732"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="af0a8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="af0a8-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="af0a8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="af0a8-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="af0a8-104">描述</span><span class="sxs-lookup"><span data-stu-id="af0a8-104">Description</span></span>  
 <span data-ttu-id="af0a8-105">系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="af0a8-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="af0a8-106">您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。</span><span class="sxs-lookup"><span data-stu-id="af0a8-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="af0a8-107">當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="af0a8-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="af0a8-108">以後再變更為 0 時將不會被追蹤。</span><span class="sxs-lookup"><span data-stu-id="af0a8-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="af0a8-109">執行個體內容上的流量控制限制只會針對每個內容追蹤一次。</span><span class="sxs-lookup"><span data-stu-id="af0a8-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0a8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0a8-110">See also</span></span>
- [<span data-ttu-id="af0a8-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="af0a8-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="af0a8-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="af0a8-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="af0a8-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="af0a8-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
