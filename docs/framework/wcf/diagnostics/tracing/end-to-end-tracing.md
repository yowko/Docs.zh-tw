---
title: "端對端追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b4cdbc12f57c733d8e8ba3753ce5a2f29ab28ffd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="d07db-102">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="d07db-102">End-to-End Tracing</span></span>
<span data-ttu-id="d07db-103">「端對端 (e2e) 追蹤」可讓開發人員追蹤 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 基礎結構中程式碼執行的情況，以便調查程式碼路徑失敗的原因，或是針對容量規劃與效能分析提供詳細的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d07db-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="d07db-104"> 提供三種相互關聯的機制，協助診斷錯誤的成因：活動、傳輸和傳播。</span><span class="sxs-lookup"><span data-stu-id="d07db-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="d07db-105">請參閱[端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)如需端對端追蹤案例，以及其個別活動和追蹤設計的清單。</span><span class="sxs-lookup"><span data-stu-id="d07db-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d07db-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d07db-106">In This Section</span></span>  
 <span data-ttu-id="d07db-107">[活動](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md)： 描述中的活動追蹤[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]追蹤模型。</span><span class="sxs-lookup"><span data-stu-id="d07db-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="d07db-108">[傳輸](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md)： 描述傳輸中的[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]追蹤模型中，以及使用傳輸關聯端點內的活動。</span><span class="sxs-lookup"><span data-stu-id="d07db-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="d07db-109">[傳播](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md)： 描述中的活動傳播[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]追蹤模型中，以及使用傳播將活動相互關聯各端點。</span><span class="sxs-lookup"><span data-stu-id="d07db-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="d07db-110">追蹤類型摘要</span><span class="sxs-lookup"><span data-stu-id="d07db-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="d07db-111">提供所有活動追蹤類型的摘要</span><span class="sxs-lookup"><span data-stu-id="d07db-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07db-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d07db-112">See Also</span></span>  
 [<span data-ttu-id="d07db-113">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="d07db-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="d07db-114">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="d07db-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="d07db-115">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="d07db-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="d07db-116">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="d07db-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
