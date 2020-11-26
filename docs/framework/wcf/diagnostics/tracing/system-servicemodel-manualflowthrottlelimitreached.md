---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 180a06efc94acba40806e1f5d661553127549596
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248483"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="9faae-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="9faae-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="9faae-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="9faae-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="9faae-104">描述</span><span class="sxs-lookup"><span data-stu-id="9faae-104">Description</span></span>  

 <span data-ttu-id="9faae-105">系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="9faae-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="9faae-106">您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。</span><span class="sxs-lookup"><span data-stu-id="9faae-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="9faae-107">當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="9faae-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="9faae-108">以後再變更為 0 時將不會被追蹤。</span><span class="sxs-lookup"><span data-stu-id="9faae-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="9faae-109">執行個體內容上的流量控制限制只會針對每個內容追蹤一次。</span><span class="sxs-lookup"><span data-stu-id="9faae-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9faae-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9faae-110">See also</span></span>

- [<span data-ttu-id="9faae-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="9faae-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9faae-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="9faae-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9faae-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="9faae-113">Administration and Diagnostics</span></span>](../index.md)
