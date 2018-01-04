---
title: "使用追蹤來疑難排解應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb46ad5fe95405c78baf3173a982969e0e7092fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="002a9-102">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="002a9-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="002a9-103">本節中的各個主題會說明如何使用追蹤來排解應用程式的問題。</span><span class="sxs-lookup"><span data-stu-id="002a9-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="002a9-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="002a9-104">In This Section</span></span>  
 [<span data-ttu-id="002a9-105">追蹤與訊息記錄的建議設定</span><span class="sxs-lookup"><span data-stu-id="002a9-105">Recommended Settings for Tracing and Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="002a9-106">說明實際執行環境與偵錯環境中的建議設定。</span><span class="sxs-lookup"><span data-stu-id="002a9-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="002a9-107">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="002a9-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="002a9-108">說明如何使用服務追蹤檢視器工具來檢視、關聯與分析追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="002a9-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="002a9-109">重大追蹤</span><span class="sxs-lookup"><span data-stu-id="002a9-109">Significant Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/significant-traces.md)  
 <span data-ttu-id="002a9-110">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 所發出之主要追蹤的清單。</span><span class="sxs-lookup"><span data-stu-id="002a9-110">A list of major traces emitted by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="002a9-111">用戶端偵錯</span><span class="sxs-lookup"><span data-stu-id="002a9-111">Debugging on the Client</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/debugging-on-the-client.md)  
 <span data-ttu-id="002a9-112">讓用戶端能夠對您的應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="002a9-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="002a9-113">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="002a9-113">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="002a9-114">說明 E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 案例所使用的追蹤，例如，同步 wsHttp 要求-回覆，與非同步 TCP 單向要求。</span><span class="sxs-lookup"><span data-stu-id="002a9-114">Describes traces used for E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="002a9-115">發出使用者程式碼追蹤</span><span class="sxs-lookup"><span data-stu-id="002a9-115">Emitting User-Code Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)  
 <span data-ttu-id="002a9-116">說明如何透過使用者程式碼以程式設計方式發出追蹤，方便您主動建立檢測資料以便稍後用在診斷用途上，並與 WCF 追蹤產生關聯。</span><span class="sxs-lookup"><span data-stu-id="002a9-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002a9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="002a9-117">See Also</span></span>  
 [<span data-ttu-id="002a9-118">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="002a9-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="002a9-119">追蹤</span><span class="sxs-lookup"><span data-stu-id="002a9-119">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="002a9-120">端對端追蹤</span><span class="sxs-lookup"><span data-stu-id="002a9-120">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
