---
title: 具有 ETW 的分析追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798085"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="3c987-102">具有 ETW 的分析追蹤</span><span class="sxs-lookup"><span data-stu-id="3c987-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="3c987-103">Windows Communication Foundation （WCF）分析追蹤提供在 WCF 服務執行期間捕捉診斷資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="3c987-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="3c987-104">WCF 分析追蹤事件會在 WCF 堆疊的關鍵點發出，以允許在生產環境中進行 WCF 服務的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="3c987-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="3c987-105">Wcf 服務的分析追蹤對於裝載[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF 服務之產品伺服器的效能影響最小，因為這些事件非常有效率地發出至 Windows 事件追蹤（ETW）會話。</span><span class="sxs-lookup"><span data-stu-id="3c987-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c987-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="3c987-106">In This Section</span></span>  
 [<span data-ttu-id="3c987-107">分析追蹤概觀</span><span class="sxs-lookup"><span data-stu-id="3c987-107">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="3c987-108">討論 WCF 分析追蹤在中的[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]運作方式。</span><span class="sxs-lookup"><span data-stu-id="3c987-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="3c987-109">動態地啟用分析追蹤</span><span class="sxs-lookup"><span data-stu-id="3c987-109">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="3c987-110">討論如何啟用或停用 ETW 動態追蹤。</span><span class="sxs-lookup"><span data-stu-id="3c987-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="3c987-111">設定訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="3c987-111">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="3c987-112">說明如何設定訊息流程追蹤。</span><span class="sxs-lookup"><span data-stu-id="3c987-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="3c987-113">分析追蹤事件參考</span><span class="sxs-lookup"><span data-stu-id="3c987-113">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="3c987-114">顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3c987-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c987-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c987-115">See also</span></span>

- [<span data-ttu-id="3c987-116">WCF 服務和 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="3c987-116">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="3c987-117">在 Windows 事件追蹤中追蹤事件</span><span class="sxs-lookup"><span data-stu-id="3c987-117">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
