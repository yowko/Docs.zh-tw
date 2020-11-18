---
title: 記錄和追蹤-.NET Core
description: .NET Core 記錄和追蹤的簡介。
ms.date: 10/12/2020
ms.openlocfilehash: 86444f2451079e54050f6698f3e45ddff0700acf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820575"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="0f267-103">.NET Core 記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="0f267-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="0f267-104">記錄和追蹤其實是相同技術的兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="0f267-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="0f267-105">自電腦提早起，使用了簡單的技巧。</span><span class="sxs-lookup"><span data-stu-id="0f267-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="0f267-106">它只需要檢測應用程式，以寫入稍後要使用的輸出。</span><span class="sxs-lookup"><span data-stu-id="0f267-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="0f267-107">使用記錄和追蹤的原因</span><span class="sxs-lookup"><span data-stu-id="0f267-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="0f267-108">這種簡單的技術出奇的強大。</span><span class="sxs-lookup"><span data-stu-id="0f267-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="0f267-109">它可用於偵錯工具失敗的情況：</span><span class="sxs-lookup"><span data-stu-id="0f267-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="0f267-110">長時間出現的問題，可能很難利用傳統的偵錯工具進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="0f267-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="0f267-111">記錄允許長時間進行詳盡的事後檢討。</span><span class="sxs-lookup"><span data-stu-id="0f267-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="0f267-112">相反地，偵錯工具受限於即時分析。</span><span class="sxs-lookup"><span data-stu-id="0f267-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="0f267-113">多執行緒應用程式與分散式應用程式通常很難偵錯。</span><span class="sxs-lookup"><span data-stu-id="0f267-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="0f267-114">連結偵錯工具往往會修改行為。</span><span class="sxs-lookup"><span data-stu-id="0f267-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="0f267-115">您可以視需要分析詳細的記錄，以了解複雜的系統。</span><span class="sxs-lookup"><span data-stu-id="0f267-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="0f267-116">分散式應用程式中的問題可能是因為許多元件之間的複雜互動而引發，因此，將偵錯工具連接到系統的每個部分可能並不合理。</span><span class="sxs-lookup"><span data-stu-id="0f267-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="0f267-117">許多服務都不應該停止。</span><span class="sxs-lookup"><span data-stu-id="0f267-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="0f267-118">連結偵錯工具通常會導致逾時失敗。</span><span class="sxs-lookup"><span data-stu-id="0f267-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="0f267-119">問題不一定可以預見。</span><span class="sxs-lookup"><span data-stu-id="0f267-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="0f267-120">記錄和追蹤是針對低額外負荷而設計，因此，在發生問題時，程式一律會進行記錄。</span><span class="sxs-lookup"><span data-stu-id="0f267-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="0f267-121">.NET Core Api</span><span class="sxs-lookup"><span data-stu-id="0f267-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="0f267-122">列印樣式 Api</span><span class="sxs-lookup"><span data-stu-id="0f267-122">Print style APIs</span></span>

<span data-ttu-id="0f267-123"><xref:System.Console?displayProperty=nameWithType>、 <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 類別都提供類似的列印樣式 api，方便您進行記錄。</span><span class="sxs-lookup"><span data-stu-id="0f267-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="0f267-124">選擇要使用的列印樣式 API 完全取決於您。</span><span class="sxs-lookup"><span data-stu-id="0f267-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="0f267-125">主要差異包括：</span><span class="sxs-lookup"><span data-stu-id="0f267-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-126">一律啟用且一律寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="0f267-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="0f267-127">適用於客戶可能需要在發行版本中看到的資訊。</span><span class="sxs-lookup"><span data-stu-id="0f267-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="0f267-128">因為這是最簡單的方法，所以通常用於進行臨機操作的暫時性偵錯。</span><span class="sxs-lookup"><span data-stu-id="0f267-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="0f267-129">此偵錯程式碼通常絕對不會簽入到原始程式碼控制。</span><span class="sxs-lookup"><span data-stu-id="0f267-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-130">只有在定義 `TRACE` 時才會啟用。</span><span class="sxs-lookup"><span data-stu-id="0f267-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="0f267-131"><xref:System.Diagnostics.Trace.Listeners>依預設，寫入至附加 <xref:System.Diagnostics.DefaultTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="0f267-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="0f267-132">在建立將在大部分組建中啟用的記錄時，使用此 API。</span><span class="sxs-lookup"><span data-stu-id="0f267-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-133">只有在定義 `DEBUG` 時才會啟用。</span><span class="sxs-lookup"><span data-stu-id="0f267-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="0f267-134">寫入到已連結的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0f267-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="0f267-135">如果設定，則在 `*nix` 寫入至 stderr 時 `COMPlus_DebugWriteToStdErr` 。</span><span class="sxs-lookup"><span data-stu-id="0f267-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="0f267-136">在建立將只會在偵錯組建中啟用的記錄時，使用此 API。</span><span class="sxs-lookup"><span data-stu-id="0f267-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="0f267-137">記錄事件</span><span class="sxs-lookup"><span data-stu-id="0f267-137">Logging events</span></span>

<span data-ttu-id="0f267-138">下列 Api 更是事件導向。</span><span class="sxs-lookup"><span data-stu-id="0f267-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="0f267-139">它們不會記錄簡單字串，而是記錄事件物件。</span><span class="sxs-lookup"><span data-stu-id="0f267-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-140">EventSource 是主要的根 .NET Core 追蹤 API。</span><span class="sxs-lookup"><span data-stu-id="0f267-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="0f267-141">適用于所有的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="0f267-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="0f267-142">只允許追蹤可序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="0f267-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="0f267-143">可以透過設定為取用 EventSource 的任何 [EventListener](xref:System.Diagnostics.Tracing.EventListener) 實例，在同進程中使用。</span><span class="sxs-lookup"><span data-stu-id="0f267-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="0f267-144">可透過下列方式跨進程使用：</span><span class="sxs-lookup"><span data-stu-id="0f267-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="0f267-145">所有平臺上[的 .Net Core EventPipe](./eventpipe.md)</span><span class="sxs-lookup"><span data-stu-id="0f267-145">[.NET Core's EventPipe](./eventpipe.md) on all platforms</span></span>
    - [<span data-ttu-id="0f267-146">Windows 事件追蹤 (ETW)</span><span class="sxs-lookup"><span data-stu-id="0f267-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="0f267-147">適用于 Linux 的 LTTng 追蹤架構</span><span class="sxs-lookup"><span data-stu-id="0f267-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="0f267-148">逐步解說： [使用 PerfCollect 收集 LTTng 追蹤](trace-perfcollect-lttng.md)。</span><span class="sxs-lookup"><span data-stu-id="0f267-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-149">隨附于 .NET Core，以及做為 .NET Framework 的 [NuGet 套件](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) 。</span><span class="sxs-lookup"><span data-stu-id="0f267-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="0f267-150">允許非可序列化物件的同進程追蹤。</span><span class="sxs-lookup"><span data-stu-id="0f267-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="0f267-151">包含允許將已記錄物件的選定欄位寫入至的橋接器 <xref:System.Diagnostics.Tracing.EventSource> 。</span><span class="sxs-lookup"><span data-stu-id="0f267-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-152">提供一種明確的方式，可識別特定活動或交易所產生的記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="0f267-152">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="0f267-153">此物件可用來將不同服務之間的記錄相互關聯。</span><span class="sxs-lookup"><span data-stu-id="0f267-153">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="0f267-154">僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="0f267-154">Windows only.</span></span>
  - <span data-ttu-id="0f267-155">將訊息寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0f267-155">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="0f267-156">系統管理員預期會在 Windows 事件記錄檔中出現嚴重的應用程式錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0f267-156">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="0f267-157">ILogger 和記錄架構</span><span class="sxs-lookup"><span data-stu-id="0f267-157">ILogger and logging frameworks</span></span>

<span data-ttu-id="0f267-158">低層級 Api 可能不是您記錄需求的正確選擇。</span><span class="sxs-lookup"><span data-stu-id="0f267-158">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="0f267-159">您可能會想要考慮使用記錄架構。</span><span class="sxs-lookup"><span data-stu-id="0f267-159">You may want to consider a logging framework.</span></span>

<span data-ttu-id="0f267-160"><xref:Microsoft.Extensions.Logging.ILogger>介面已用來建立一般記錄介面，可透過相依性插入來插入記錄器。</span><span class="sxs-lookup"><span data-stu-id="0f267-160">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="0f267-161">比方說，若要讓您為應用程式 .NET 提供最理想的選擇，您可以選擇內建和協力廠商架構：</span><span class="sxs-lookup"><span data-stu-id="0f267-161">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="0f267-162">.NET 內建記錄提供者</span><span class="sxs-lookup"><span data-stu-id="0f267-162">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="0f267-163">.NET 協力廠商記錄提供者</span><span class="sxs-lookup"><span data-stu-id="0f267-163">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="0f267-164">記錄相關參考</span><span class="sxs-lookup"><span data-stu-id="0f267-164">Logging related references</span></span>

- [<span data-ttu-id="0f267-165">作法：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="0f267-165">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="0f267-166">作法：將追蹤陳述式新增至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="0f267-166">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="0f267-167">[.Net 中的記錄](../extensions/logging.md) 提供它所支援之記錄技術的總覽。</span><span class="sxs-lookup"><span data-stu-id="0f267-167">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="0f267-168">[C # 字串插補](../../csharp/language-reference/tokens/interpolated.md) 可簡化撰寫記錄程式碼的程式。</span><span class="sxs-lookup"><span data-stu-id="0f267-168">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- [<span data-ttu-id="0f267-169">執行時間提供者事件清單</span><span class="sxs-lookup"><span data-stu-id="0f267-169">Runtime Provider Event List</span></span>](../../fundamentals/diagnostics/runtime-events.md)

- <span data-ttu-id="0f267-170"><xref:System.Exception.Message?displayProperty=nameWithType>屬性適用于記錄例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f267-170">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="0f267-171"><xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>類別有助於在記錄中提供堆疊資訊。</span><span class="sxs-lookup"><span data-stu-id="0f267-171">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="0f267-172">效能考量</span><span class="sxs-lookup"><span data-stu-id="0f267-172">Performance considerations</span></span>

<span data-ttu-id="0f267-173">字串格式化可能需要很明顯的 CPU 處理時間。</span><span class="sxs-lookup"><span data-stu-id="0f267-173">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="0f267-174">在效能關鍵的應用程式中，建議您：</span><span class="sxs-lookup"><span data-stu-id="0f267-174">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="0f267-175">當沒有人在接聽時，請避免進行大量記錄。</span><span class="sxs-lookup"><span data-stu-id="0f267-175">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="0f267-176">藉由檢查是否先啟用記錄，以避免建立昂貴的記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="0f267-176">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="0f267-177">只記錄有用的內容。</span><span class="sxs-lookup"><span data-stu-id="0f267-177">Only log what's useful.</span></span>
- <span data-ttu-id="0f267-178">將複雜的格式設定延遲至分析階段。</span><span class="sxs-lookup"><span data-stu-id="0f267-178">Defer fancy formatting to the analysis stage.</span></span>
