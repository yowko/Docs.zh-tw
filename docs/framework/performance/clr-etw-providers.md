---
title: CLR ETW 提供者
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 639ebe1552fd3950bd77acd7b5730b0d3bdb150f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302617"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="c43ad-102">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="c43ad-102">CLR ETW Providers</span></span>
<span data-ttu-id="c43ad-103">Common Language Runtime (CLR) 有兩個提供者：執行階段提供者和取消提供者。</span><span class="sxs-lookup"><span data-stu-id="c43ad-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="c43ad-104">執行階段提供者會根據啟用哪些關鍵字 (事件的類別) 來引發事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="c43ad-105">例如，您可以啟用 `LoaderKeyword` 關鍵字來收集載入器事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="c43ad-106">Windows (ETW) 事件的事件追蹤會記錄至副檔名為 .etl 的檔案，稍後可視需要在逗號分隔值 (.csv) 檔案中後置處理。</span><span class="sxs-lookup"><span data-stu-id="c43ad-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="c43ad-107">如需如何將 .etl 檔案轉換成 .csv 檔案的資訊，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="c43ad-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="c43ad-108">執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="c43ad-108">The Runtime Provider</span></span>  
 <span data-ttu-id="c43ad-109">執行階段提供者是主要 CLR ETW 提供者。</span><span class="sxs-lookup"><span data-stu-id="c43ad-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="c43ad-110">CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="c43ad-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="c43ad-111">如需如何使用常用工具來記錄和檢視 CLR ETW 事件的範例，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="c43ad-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="c43ad-112">除了使用 `LoaderKeyword` 這類關鍵字之外，您可能還需要啟用關鍵字來記錄可能太頻繁引發的事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="c43ad-113">`StartEnumerationKeyword` 和 `EndEnumerationKeyword` 關鍵字會啟用這些事件，[CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)中會有摘要說明。</span><span class="sxs-lookup"><span data-stu-id="c43ad-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="c43ad-114">取消提供者</span><span class="sxs-lookup"><span data-stu-id="c43ad-114">The Rundown Provider</span></span>  
 <span data-ttu-id="c43ad-115">針對某些特殊用途，必須開啟取消提供者。</span><span class="sxs-lookup"><span data-stu-id="c43ad-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="c43ad-116">不過，對大部分的使用者而言，執行階段提供者應該就已足夠。</span><span class="sxs-lookup"><span data-stu-id="c43ad-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="c43ad-117">CLR 取消提供者 GUID 是 A669021C-C450-4609-A035-5AF59AF4DF18。</span><span class="sxs-lookup"><span data-stu-id="c43ad-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="c43ad-118">一般來說，會在啟動處理序之前啟用 ETW 記錄，並在處理序結束之後關閉記錄。</span><span class="sxs-lookup"><span data-stu-id="c43ad-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="c43ad-119">不過，如果在處理序執行時開啟 ETW 記錄，則需要處理序的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="c43ad-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="c43ad-120">例如，進行符號解析時，您必須針對已在開啟記錄之前載入的方法，來記錄方法事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="c43ad-121">`DCStart` 和 `DCEnd` 事件會擷取啟動和停止資料收集時的處理序狀態</span><span class="sxs-lookup"><span data-stu-id="c43ad-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="c43ad-122">(狀態是指高階資訊，包含已進行 Just-In-Time (JIT) 編譯的方法，以及已載入的組件)。這兩個事件都可以提供處理序中發生情況的相關資訊；例如，哪些方法已進行 JIT 編譯，依此類推。</span><span class="sxs-lookup"><span data-stu-id="c43ad-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="c43ad-123">在取消提供者下，只會引發其名稱含有 `DC`、`DCStart`、`DCEnd` 或 `DCInit` 的事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="c43ad-124">此外，只會在取消提供者下引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="c43ad-125">除了事件關鍵字篩選之外，取消提供者也支援 `StartRundownKeyword` 和 `EndRundownKeyword` 關鍵字，以提供目標篩選。</span><span class="sxs-lookup"><span data-stu-id="c43ad-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="c43ad-126">開始取消</span><span class="sxs-lookup"><span data-stu-id="c43ad-126">Start Rundown</span></span>  
 <span data-ttu-id="c43ad-127">使用 `StartRundownKeyword` 關鍵字啟用取消提供者下的記錄時，會觸發開始取消。</span><span class="sxs-lookup"><span data-stu-id="c43ad-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="c43ad-128">這會引發 `DCStart` 事件，並擷取系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="c43ad-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="c43ad-129">開始列舉之前，會引發 `DCStartInit` 事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="c43ad-130">列舉結束時，會引發 `DCStartComplete` 事件，以通知控制器資料收集已正常終止。</span><span class="sxs-lookup"><span data-stu-id="c43ad-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="c43ad-131">結束取消</span><span class="sxs-lookup"><span data-stu-id="c43ad-131">End Rundown</span></span>  
 <span data-ttu-id="c43ad-132">使用 `EndRundownKeyword` 關鍵字啟用取消提供者下的記錄時，會觸發結束取消。</span><span class="sxs-lookup"><span data-stu-id="c43ad-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="c43ad-133">結束取消會停止對繼續執行之處理序的分析。</span><span class="sxs-lookup"><span data-stu-id="c43ad-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="c43ad-134">`DCEnd` 事件會擷取停止分析時的系統狀態。</span><span class="sxs-lookup"><span data-stu-id="c43ad-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="c43ad-135">開始列舉之前，會引發 `DCEndInit` 事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="c43ad-136">列舉結束時，會引發 `DCEndComplete` 事件，以通知消費者資料收集已正常終止。</span><span class="sxs-lookup"><span data-stu-id="c43ad-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="c43ad-137">開始取消和結束取消主要用於 Managed 符號解析。</span><span class="sxs-lookup"><span data-stu-id="c43ad-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="c43ad-138">開始取消可以提供已在啟動分析工作階段之前進行 JIT 編譯之方法的位址範圍資訊。</span><span class="sxs-lookup"><span data-stu-id="c43ad-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="c43ad-139">結束取消可以提供已在即將關閉分析時進行 JIT 編譯之所有方法的位址範圍資訊。</span><span class="sxs-lookup"><span data-stu-id="c43ad-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="c43ad-140">停止分析工作階段時，不會自動發生結束取消。</span><span class="sxs-lookup"><span data-stu-id="c43ad-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="c43ad-141">相反地，就在停止分析之前，嘗試執行 Managed 符號解析的工具必須在啟用 `EndRundownKeyword` 關鍵字的情況下明確地叫用 CLR 取消提供者工作階段。</span><span class="sxs-lookup"><span data-stu-id="c43ad-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="c43ad-142">雖然開始取消或結束取消可以提供 Managed 符號解析的方法位址範圍資訊，但是建議您使用 `EndRundownKeyword` 關鍵字 (其提供 `DCEnd` 事件)，而非 `StartRundownKeyword` 關鍵字 (其提供 `DCStart` 事件)。</span><span class="sxs-lookup"><span data-stu-id="c43ad-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="c43ad-143">使用 `StartRundownKeyword` 可在分析工作階段期間發生取消，而這可能會干擾分析的案例。</span><span class="sxs-lookup"><span data-stu-id="c43ad-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="c43ad-144">使用執行階段和取消提供者的 ETW 資料收集</span><span class="sxs-lookup"><span data-stu-id="c43ad-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="c43ad-145">下列範例示範如何使用 CLR 取消提供者，而方式是允許 Managed 處理序的符號解析，並且影響最少，而且不論處理序是在分析的時間範圍內部或外部開始或結束。</span><span class="sxs-lookup"><span data-stu-id="c43ad-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="c43ad-146">使用 CLR 執行階段提供者開啟 ETW 記錄：</span><span class="sxs-lookup"><span data-stu-id="c43ad-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="c43ad-147">記錄會儲存至 clr1.etl 檔案。</span><span class="sxs-lookup"><span data-stu-id="c43ad-147">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="c43ad-148">若要在處理序繼續執行時停止分析，請啟動取消提供者來擷取 `DCEnd` 事件：</span><span class="sxs-lookup"><span data-stu-id="c43ad-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="c43ad-149">這會啟用 `DCEnd` 事件的收集來啟動取消工作階段。</span><span class="sxs-lookup"><span data-stu-id="c43ad-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="c43ad-150">您可能需要等待 30 到 60 秒的時間，以收集所有事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="c43ad-151">記錄會儲存至 clr1.et2 檔案。</span><span class="sxs-lookup"><span data-stu-id="c43ad-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="c43ad-152">關閉所有 ETW 分析：</span><span class="sxs-lookup"><span data-stu-id="c43ad-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="c43ad-153">合併設定檔以建立一個記錄檔：</span><span class="sxs-lookup"><span data-stu-id="c43ad-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="c43ad-154">merged.etl 檔案將包含來自執行階段和取消提供者工作階段的事件。</span><span class="sxs-lookup"><span data-stu-id="c43ad-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="c43ad-155">工具可以執行步驟 2 和 3 (啟動取消工作階段，然後終止分析)，而不是在使用者要求停止分析時立即關閉分析。</span><span class="sxs-lookup"><span data-stu-id="c43ad-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="c43ad-156">工具也可以執行步驟 4。</span><span class="sxs-lookup"><span data-stu-id="c43ad-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43ad-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c43ad-157">See also</span></span>

- [<span data-ttu-id="c43ad-158">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="c43ad-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
