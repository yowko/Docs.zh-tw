---
title: 端對端追蹤
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fc8fc448bdcf94ab25349f6b34961a34e5ed2a5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598576"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="04231-102">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="04231-102">End-to-End Tracing</span></span>
<span data-ttu-id="04231-103">端對端（e2e）追蹤可讓開發人員遵循 Windows Communication Foundation （WCF）基礎結構中的程式碼執行，來調查程式碼路徑失敗的原因，或是針對容量規劃和效能分析提供詳細的追蹤。</span><span class="sxs-lookup"><span data-stu-id="04231-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="04231-104">Windows Communication Foundation （WCF）提供三種相互關聯機制，協助診斷錯誤的原因：活動、傳輸和傳播。</span><span class="sxs-lookup"><span data-stu-id="04231-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="04231-105">如需端對端追蹤案例的清單，以及其各自的活動和追蹤設計，請參閱[端對端追蹤案例](end-to-end-tracing-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="04231-105">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04231-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="04231-106">In This Section</span></span>  
 <span data-ttu-id="04231-107">[活動](activity.md)：描述 WINDOWS COMMUNICATION FOUNDATION （WCF）追蹤模型中的活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="04231-107">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="04231-108">[轉移](transfer.md)：描述在 WINDOWS COMMUNICATION FOUNDATION （WCF）追蹤模型中的傳輸，以及使用傳送來使端點內的活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="04231-108">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="04231-109">[傳播](propagation.md)：描述 WINDOWS COMMUNICATION FOUNDATION （WCF）追蹤模型中的活動傳播，並使用傳播來使各個端點的活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="04231-109">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="04231-110">追蹤類型摘要</span><span class="sxs-lookup"><span data-stu-id="04231-110">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="04231-111">提供所有活動追蹤類型的摘要</span><span class="sxs-lookup"><span data-stu-id="04231-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04231-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="04231-112">See also</span></span>

- [<span data-ttu-id="04231-113">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="04231-113">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="04231-114">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="04231-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="04231-115">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="04231-115">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="04231-116">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="04231-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
