---
title: 傳輸
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: c3f9420ac798bf2722f825d14ca64653127432b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662877"
---
# <a name="transfer"></a><span data-ttu-id="21a10-102">傳輸</span><span class="sxs-lookup"><span data-stu-id="21a10-102">Transfer</span></span>
<span data-ttu-id="21a10-103">本主題說明 Windows Communication Foundation (WCF) 的活動追蹤模型中的傳輸。</span><span class="sxs-lookup"><span data-stu-id="21a10-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="21a10-104">傳輸定義</span><span class="sxs-lookup"><span data-stu-id="21a10-104">Transfer Definition</span></span>  
 <span data-ttu-id="21a10-105">活動之間的傳輸表示在端點內相關活動中事件之間的因果關係。</span><span class="sxs-lookup"><span data-stu-id="21a10-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="21a10-106">當控制在這些活動之間流動時 (例如跨活動界限的方法呼叫)，有兩個活動會與傳輸相關。</span><span class="sxs-lookup"><span data-stu-id="21a10-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="21a10-107">在 WCF 中，當位元組傳入服務時，接聽活動會傳送到接收位元組活動在建立訊息物件。</span><span class="sxs-lookup"><span data-stu-id="21a10-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="21a10-108">如需端對端追蹤案例，以及其個別活動與追蹤設計的清單，請參閱 <<c0> [ 端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="21a10-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="21a10-109">若要發出傳輸追蹤，請使用追蹤來源的 `ActivityTracing` 設定，如同下列組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="21a10-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="21a10-110">使用傳輸以相互關聯端點內的活動</span><span class="sxs-lookup"><span data-stu-id="21a10-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="21a10-111">活動和傳輸都可能讓使用者找到錯誤的根本原因。</span><span class="sxs-lookup"><span data-stu-id="21a10-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="21a10-112">例如，如果在元件 M 和 N 中的活動 M 和 N 之間來回傳輸，而在傳輸回 M 之後 N 馬上發生當機，很可能是 N 將資料傳遞回 M 時造成。</span><span class="sxs-lookup"><span data-stu-id="21a10-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="21a10-113">當 M 和 N 之間具有控制流程時，就會從活動 M 將傳輸追蹤發出至活動 N。例如，由於跨活動界限的方法呼叫，N 就會執行 M 的部分工作。</span><span class="sxs-lookup"><span data-stu-id="21a10-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="21a10-114">N 可能已存在或已建立。</span><span class="sxs-lookup"><span data-stu-id="21a10-114">N may already exist or has been created.</span></span> <span data-ttu-id="21a10-115">當 N 是執行 M 之部分工作的新活動時，M 就會繁衍 (Spawn) N。</span><span class="sxs-lookup"><span data-stu-id="21a10-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="21a10-116">從 N 傳輸回 M 之後可能不會從 M 傳輸至 N。這是因為當 N 完成該工作時，M 可以繁衍 N 中的部分工作並且不會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="21a10-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="21a10-117">實際上，M 可以在 N 完成其工作之前就終止。</span><span class="sxs-lookup"><span data-stu-id="21a10-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="21a10-118">發生這種情況中的"Open ServiceHost"活動 (M) 會繁衍接聽項活動 (N)，並終止。</span><span class="sxs-lookup"><span data-stu-id="21a10-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="21a10-119">從 N 傳輸回 M 表示 N 已完成與 M 相關的工作。</span><span class="sxs-lookup"><span data-stu-id="21a10-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="21a10-120">N 則可以繼續執行其他與 M 不相關的處理，例如持續從不同登入活動接收登入要求 (M) 的現有驗證器活動 (N)。</span><span class="sxs-lookup"><span data-stu-id="21a10-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="21a10-121">在活動 M 和 N 之間不需要有巢狀關係，原因可能有兩個。</span><span class="sxs-lookup"><span data-stu-id="21a10-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="21a10-122">第一，當活動 M 在即使 M 初始化 N 的情況下，仍未監視在 N 上執行的實際處理時。第二，當 N 已經存在。</span><span class="sxs-lookup"><span data-stu-id="21a10-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="21a10-123">傳輸範例</span><span class="sxs-lookup"><span data-stu-id="21a10-123">Example of Transfers</span></span>  
 <span data-ttu-id="21a10-124">下列將會列出兩個傳輸範例。</span><span class="sxs-lookup"><span data-stu-id="21a10-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="21a10-125">當您建立服務主機時，建構函式會從呼叫程式碼中取得控制，或者呼叫程式碼會傳輸至建構函式。</span><span class="sxs-lookup"><span data-stu-id="21a10-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="21a10-126">建構函式執行完成時，會將控制權傳回呼叫程式碼，或者建構函式會傳輸回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="21a10-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="21a10-127">這就是巢狀關係的情況。</span><span class="sxs-lookup"><span data-stu-id="21a10-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="21a10-128">接聽項開始處理傳輸資料時，會建立新的執行緒，並將適當的內容交給接收位元組活動，以供處理、傳遞控制和資料。</span><span class="sxs-lookup"><span data-stu-id="21a10-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="21a10-129">當執行緒完成處理要求時，接收位元組活動不會將任何資料傳遞回接聽項。</span><span class="sxs-lookup"><span data-stu-id="21a10-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="21a10-130">在這個情況下，有資料傳輸進來，但沒有資料從新執行緒活動傳輸出去。</span><span class="sxs-lookup"><span data-stu-id="21a10-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="21a10-131">這兩個活動彼此相關，但不是巢狀關係。</span><span class="sxs-lookup"><span data-stu-id="21a10-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="21a10-132">活動傳輸順序</span><span class="sxs-lookup"><span data-stu-id="21a10-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="21a10-133">格式正確的活動傳輸順序包括下列步驟。</span><span class="sxs-lookup"><span data-stu-id="21a10-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="21a10-134">開始新活動，而此活動是由選取新 gAId 所組成。</span><span class="sxs-lookup"><span data-stu-id="21a10-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="21a10-135">從目前活動識別碼中，將傳輸追蹤發出至該新 gAId</span><span class="sxs-lookup"><span data-stu-id="21a10-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="21a10-136">在 TLS 中設定新識別碼</span><span class="sxs-lookup"><span data-stu-id="21a10-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="21a10-137">發出啟動追蹤，以指出新活動的起點。</span><span class="sxs-lookup"><span data-stu-id="21a10-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="21a10-138">傳回原始活動則包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="21a10-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="21a10-139">將傳輸追蹤發出至原始 gAId</span><span class="sxs-lookup"><span data-stu-id="21a10-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="21a10-140">發出停止追蹤以指出新活動的結束</span><span class="sxs-lookup"><span data-stu-id="21a10-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="21a10-141">將 TLS 設定為舊 gAId。</span><span class="sxs-lookup"><span data-stu-id="21a10-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="21a10-142">下列程式碼範例會示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="21a10-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="21a10-143">這個範例會假設傳輸至新活動時已產生區塊呼叫，而且其中也包含暫止/繼續追蹤。</span><span class="sxs-lookup"><span data-stu-id="21a10-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="21a10-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21a10-144">See also</span></span>

- [<span data-ttu-id="21a10-145">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="21a10-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="21a10-146">使用服務追蹤檢視器檢視相關追蹤並進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="21a10-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="21a10-147">端對端追蹤案例</span><span class="sxs-lookup"><span data-stu-id="21a10-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="21a10-148">服務追蹤檢視器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="21a10-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
