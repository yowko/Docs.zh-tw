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
ms.openlocfilehash: 42683acdfe2e63d59a13496b210f83fb97c02de7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="789a2-102">具有 ETW 的分析追蹤</span><span class="sxs-lookup"><span data-stu-id="789a2-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="789a2-103"> 分析追蹤提供可在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務執行期間擷取診斷資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="789a2-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="789a2-104"> 分析追蹤事件會在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，以便在實際執行環境中處理 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="789a2-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="789a2-105">分析追蹤[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務最少對效能造成影響的產品伺服器裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)][!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]為這些事件會非常有效率的方式發出 Windows 事件追蹤 (ETW) 工作階段 services。</span><span class="sxs-lookup"><span data-stu-id="789a2-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="789a2-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="789a2-106">In This Section</span></span>  
 [<span data-ttu-id="789a2-107">分析追蹤的概觀</span><span class="sxs-lookup"><span data-stu-id="789a2-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="789a2-108">討論 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤如何在 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中運作。</span><span class="sxs-lookup"><span data-stu-id="789a2-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="789a2-109">動態地啟用分析追蹤</span><span class="sxs-lookup"><span data-stu-id="789a2-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="789a2-110">討論如何啟用或停用 ETW 動態追蹤。</span><span class="sxs-lookup"><span data-stu-id="789a2-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="789a2-111">設定訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="789a2-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="789a2-112">說明如何設定訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="789a2-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="789a2-113">分析追蹤事件參考</span><span class="sxs-lookup"><span data-stu-id="789a2-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="789a2-114">顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。</span><span class="sxs-lookup"><span data-stu-id="789a2-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789a2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="789a2-115">See Also</span></span>  
 [<span data-ttu-id="789a2-116">WCF Services and Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="789a2-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="789a2-117">Windows 事件追蹤中追蹤事件</span><span class="sxs-lookup"><span data-stu-id="789a2-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
