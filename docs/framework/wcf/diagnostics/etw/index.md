---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
  - 'diagnostics [WCF], analytic tracing'
  - 'administration [WCF], analytic tracing'
  - 'analytic tracing [WCF]'
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="858fc-102">具有 ETW 的分析追蹤</span><span class="sxs-lookup"><span data-stu-id="858fc-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="858fc-103">Windows Communication Foundation (WCF) 的分析追蹤提供 WCF 服務的執行期間擷取診斷資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="858fc-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="858fc-104">WCF 分析追蹤事件會在生產環境中的 WCF 服務的疑難排解 WCF 堆疊中的關鍵點發出。</span><span class="sxs-lookup"><span data-stu-id="858fc-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="858fc-105">分析追蹤 WCF 服務的影響降到最低的產品伺服器效能裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]這些事件是非常有效率的方式發出 Windows 事件追蹤 (ETW) 工作階段的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="858fc-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="858fc-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="858fc-106">In This Section</span></span>  
 [<span data-ttu-id="858fc-107">分析追蹤概觀</span><span class="sxs-lookup"><span data-stu-id="858fc-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="858fc-108">WCF 分析追蹤中的運作方式的討論[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="858fc-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="858fc-109">動態地啟用分析追蹤</span><span class="sxs-lookup"><span data-stu-id="858fc-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="858fc-110">討論如何啟用或停用 ETW 動態追蹤。</span><span class="sxs-lookup"><span data-stu-id="858fc-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="858fc-111">設定訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="858fc-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="858fc-112">說明如何設定訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="858fc-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="858fc-113">分析追蹤事件參考</span><span class="sxs-lookup"><span data-stu-id="858fc-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="858fc-114">顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。</span><span class="sxs-lookup"><span data-stu-id="858fc-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858fc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="858fc-115">See also</span></span>
- [<span data-ttu-id="858fc-116">WCF 服務和 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="858fc-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="858fc-117">在 Windows 事件追蹤中追蹤事件</span><span class="sxs-lookup"><span data-stu-id="858fc-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
