---
title: 端對端追蹤
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fd2964b39c758e41620fb453ddd8f61a1aa550aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092109"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="7c4c3-102">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="7c4c3-102">End-to-End Tracing</span></span>
<span data-ttu-id="7c4c3-103">端對端 (e2e) 追蹤可讓開發人員遵循的 Windows Communication Foundation (WCF) 基礎結構以便調查程式碼路徑失敗的原因，或是提供進行容量規劃與效能分析詳細的追蹤中的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="7c4c3-104">Windows Communication Foundation (WCF) 提供三種相互關聯機制，以協助診斷錯誤的成因： 活動、 傳輸和傳播。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="7c4c3-105">請參閱[端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)如需端對端追蹤案例，以及其個別活動與追蹤設計的清單。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c4c3-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c4c3-106">In This Section</span></span>  
 <span data-ttu-id="7c4c3-107">[活動](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):描述 Windows Communication Foundation (WCF) 追蹤模型中的活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="7c4c3-108">[傳輸](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):描述在 Windows Communication Foundation (WCF) 追蹤模型中，傳輸，並且使用傳輸讓端點內的活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="7c4c3-109">[傳播](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):描述在 Windows Communication Foundation (WCF) 追蹤模型中，並且使用傳播跨端點讓活動的相互關聯的活動傳播。</span><span class="sxs-lookup"><span data-stu-id="7c4c3-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="7c4c3-110">追蹤類型摘要</span><span class="sxs-lookup"><span data-stu-id="7c4c3-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="7c4c3-111">提供所有活動追蹤類型的摘要</span><span class="sxs-lookup"><span data-stu-id="7c4c3-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4c3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c4c3-112">See also</span></span>

- [<span data-ttu-id="7c4c3-113">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="7c4c3-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="7c4c3-114">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7c4c3-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="7c4c3-115">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="7c4c3-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="7c4c3-116">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="7c4c3-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
