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
ms.openlocfilehash: 49b41e27847005c7187435229e030994df10df26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="88a3b-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="88a3b-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="88a3b-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="88a3b-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="88a3b-104">描述</span><span class="sxs-lookup"><span data-stu-id="88a3b-104">Description</span></span>  
 <span data-ttu-id="88a3b-105">系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="88a3b-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="88a3b-106">您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。</span><span class="sxs-lookup"><span data-stu-id="88a3b-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="88a3b-107">當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="88a3b-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="88a3b-108">以後再變更為 0 時將不會被追蹤。</span><span class="sxs-lookup"><span data-stu-id="88a3b-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="88a3b-109">執行個體內容上的流量控制限制只會針對每個內容追蹤一次。</span><span class="sxs-lookup"><span data-stu-id="88a3b-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a3b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a3b-110">See Also</span></span>  
 [<span data-ttu-id="88a3b-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="88a3b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="88a3b-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="88a3b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="88a3b-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="88a3b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
