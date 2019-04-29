---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761516"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="69129-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="69129-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="69129-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="69129-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="69129-104">描述</span><span class="sxs-lookup"><span data-stu-id="69129-104">Description</span></span>  
 <span data-ttu-id="69129-105">系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="69129-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="69129-106">您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。</span><span class="sxs-lookup"><span data-stu-id="69129-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="69129-107">當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="69129-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="69129-108">以後再變更為 0 時將不會被追蹤。</span><span class="sxs-lookup"><span data-stu-id="69129-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="69129-109">執行個體內容上的流量控制限制只會針對每個內容追蹤一次。</span><span class="sxs-lookup"><span data-stu-id="69129-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69129-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69129-110">See also</span></span>

- [<span data-ttu-id="69129-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="69129-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="69129-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="69129-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="69129-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="69129-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
