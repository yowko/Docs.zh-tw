---
title: "具有 ETW 的分析追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="c7f59-102">具有 ETW 的分析追蹤</span><span class="sxs-lookup"><span data-stu-id="c7f59-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="c7f59-103"> 分析追蹤提供可在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務執行期間擷取診斷資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="c7f59-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="c7f59-104"> 分析追蹤事件會在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，以便在實際執行環境中處理 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="c7f59-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="c7f59-105">分析追蹤[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務最少對效能造成影響的產品伺服器裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)][!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]為這些事件會非常有效率的方式發出 Windows 事件追蹤 (ETW) 工作階段 services。</span><span class="sxs-lookup"><span data-stu-id="c7f59-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7f59-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c7f59-106">In This Section</span></span>  
 [<span data-ttu-id="c7f59-107">分析追蹤概觀</span><span class="sxs-lookup"><span data-stu-id="c7f59-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="c7f59-108">討論 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤如何在 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中運作。</span><span class="sxs-lookup"><span data-stu-id="c7f59-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="c7f59-109">動態地啟用分析追蹤</span><span class="sxs-lookup"><span data-stu-id="c7f59-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="c7f59-110">討論如何啟用或停用 ETW 動態追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7f59-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="c7f59-111">設定訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="c7f59-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="c7f59-112">說明如何設定訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7f59-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="c7f59-113">分析追蹤事件參考</span><span class="sxs-lookup"><span data-stu-id="c7f59-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="c7f59-114">顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c7f59-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f59-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f59-115">See Also</span></span>  
 [<span data-ttu-id="c7f59-116">WCF 服務和 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="c7f59-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="c7f59-117">在 Windows 事件追蹤中追蹤事件</span><span class="sxs-lookup"><span data-stu-id="c7f59-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
