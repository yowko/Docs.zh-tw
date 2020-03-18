---
title: 日誌記錄和跟蹤 - .NET 核心
description: .NET 核心日誌記錄和跟蹤簡介。
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714415"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="38074-103">.NET 核心日誌記錄和跟蹤</span><span class="sxs-lookup"><span data-stu-id="38074-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="38074-104">日誌記錄和跟蹤實際上是同一技術的兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="38074-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="38074-105">這種簡單的技術從電腦的早期就被使用。</span><span class="sxs-lookup"><span data-stu-id="38074-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="38074-106">它只需檢測應用程式以寫入以後使用的輸出。</span><span class="sxs-lookup"><span data-stu-id="38074-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="38074-107">使用日誌記錄和跟蹤的原因</span><span class="sxs-lookup"><span data-stu-id="38074-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="38074-108">這個簡單的技術是驚人的強大。</span><span class="sxs-lookup"><span data-stu-id="38074-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="38074-109">它可用於調試器失敗的情況：</span><span class="sxs-lookup"><span data-stu-id="38074-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="38074-110">長時間出現問題，使用傳統調試器可能很難調試。</span><span class="sxs-lookup"><span data-stu-id="38074-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="38074-111">日誌允許長時間進行詳細的事後審查。</span><span class="sxs-lookup"><span data-stu-id="38074-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="38074-112">相反，調試器受限制為即時分析。</span><span class="sxs-lookup"><span data-stu-id="38074-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="38074-113">多執行緒應用程式和分散式應用程式通常難以調試。</span><span class="sxs-lookup"><span data-stu-id="38074-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="38074-114">附加調試器往往會修改行為。</span><span class="sxs-lookup"><span data-stu-id="38074-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="38074-115">可以根據需要分析詳細的日誌，以瞭解複雜的系統。</span><span class="sxs-lookup"><span data-stu-id="38074-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="38074-116">分散式應用程式中的問題可能來自許多元件之間的複雜交互，將調試器連接到系統的每個部分可能不合理。</span><span class="sxs-lookup"><span data-stu-id="38074-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="38074-117">許多服務不應停滯。</span><span class="sxs-lookup"><span data-stu-id="38074-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="38074-118">附加調試器通常會導致超時失敗。</span><span class="sxs-lookup"><span data-stu-id="38074-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="38074-119">問題並不總是被預見到的。</span><span class="sxs-lookup"><span data-stu-id="38074-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="38074-120">日誌記錄和跟蹤專為低開銷而設計，以便在出現問題時始終可以記錄程式。</span><span class="sxs-lookup"><span data-stu-id="38074-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="38074-121">.NET 核心 API</span><span class="sxs-lookup"><span data-stu-id="38074-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="38074-122">列印樣式 API</span><span class="sxs-lookup"><span data-stu-id="38074-122">Print style APIs</span></span>

<span data-ttu-id="38074-123">各<xref:System.Console?displayProperty=nameWithType><xref:System.Diagnostics.Trace?displayProperty=nameWithType>各<xref:System.Diagnostics.Debug?displayProperty=nameWithType>各提供便於日誌記錄的類似列印樣式 API。</span><span class="sxs-lookup"><span data-stu-id="38074-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="38074-124">選擇使用哪種列印樣式 API 由您決定。</span><span class="sxs-lookup"><span data-stu-id="38074-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="38074-125">主要差異包括：</span><span class="sxs-lookup"><span data-stu-id="38074-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="38074-126">始終啟用並始終寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="38074-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="38074-127">對於您的客戶可能需要在版本中看到的資訊非常有用。</span><span class="sxs-lookup"><span data-stu-id="38074-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="38074-128">因為它是最簡單的方法，它通常用於臨時臨時調試。</span><span class="sxs-lookup"><span data-stu-id="38074-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="38074-129">此調試代碼通常從未簽入到原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="38074-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="38074-130">僅在定義時`TRACE`啟用。</span><span class="sxs-lookup"><span data-stu-id="38074-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="38074-131">預設情況下，寫入<xref:System.Diagnostics.Trace.Listeners>附加的<xref:System.Diagnostics.DefaultTraceListener>。</span><span class="sxs-lookup"><span data-stu-id="38074-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="38074-132">創建將在大多數生成中啟用的日誌時使用此 API。</span><span class="sxs-lookup"><span data-stu-id="38074-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="38074-133">僅在定義時`DEBUG`啟用。</span><span class="sxs-lookup"><span data-stu-id="38074-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="38074-134">寫入附加的調試器。</span><span class="sxs-lookup"><span data-stu-id="38074-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="38074-135">如果`*nix``COMPlus_DebugWriteToStdErr`設置為"設置"，則寫入穩穩。</span><span class="sxs-lookup"><span data-stu-id="38074-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="38074-136">創建僅在調試生成中啟用的日誌時使用此 API。</span><span class="sxs-lookup"><span data-stu-id="38074-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="38074-137">日誌記錄事件</span><span class="sxs-lookup"><span data-stu-id="38074-137">Logging events</span></span>

<span data-ttu-id="38074-138">以下 API 更加面向事件。</span><span class="sxs-lookup"><span data-stu-id="38074-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="38074-139">他們不是記錄簡單的字串，而是記錄事件物件。</span><span class="sxs-lookup"><span data-stu-id="38074-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="38074-140">事件源是主根 .NET 核心跟蹤 API。</span><span class="sxs-lookup"><span data-stu-id="38074-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="38074-141">適用于所有 .NET 標準版本。</span><span class="sxs-lookup"><span data-stu-id="38074-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="38074-142">只允許跟蹤可序列化物件。</span><span class="sxs-lookup"><span data-stu-id="38074-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="38074-143">寫入附加[的事件攔截器](xref:System.Diagnostics.Tracing.EventListener)。</span><span class="sxs-lookup"><span data-stu-id="38074-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="38074-144">.NET 核心為：</span><span class="sxs-lookup"><span data-stu-id="38074-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="38074-145">.NET Core 在所有平臺上的事件管道</span><span class="sxs-lookup"><span data-stu-id="38074-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="38074-146">Windows 事件追蹤 (ETW)</span><span class="sxs-lookup"><span data-stu-id="38074-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="38074-147">Linux 的 LTTng 跟蹤框架</span><span class="sxs-lookup"><span data-stu-id="38074-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="38074-148">包含在 .NET 核心中，並作為 .NET 框架的[NuGet 包](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)。</span><span class="sxs-lookup"><span data-stu-id="38074-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="38074-149">允許在進程內跟蹤不可序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="38074-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="38074-150">包括一個橋接器，用於允許將記錄物件的選定欄位寫入<xref:System.Diagnostics.Tracing.EventSource>。</span><span class="sxs-lookup"><span data-stu-id="38074-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="38074-151">提供了一種識別特定活動或事務產生的日誌消息的明確方法。</span><span class="sxs-lookup"><span data-stu-id="38074-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="38074-152">此物件可用於關聯不同服務的日誌。</span><span class="sxs-lookup"><span data-stu-id="38074-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="38074-153">僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="38074-153">Windows only.</span></span>
  - <span data-ttu-id="38074-154">將消息寫入 Windows 事件日誌。</span><span class="sxs-lookup"><span data-stu-id="38074-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="38074-155">系統管理員希望致命的應用程式錯誤訊息出現在 Windows 事件日誌中。</span><span class="sxs-lookup"><span data-stu-id="38074-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="38074-156">ILogger 和日誌記錄框架</span><span class="sxs-lookup"><span data-stu-id="38074-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="38074-157">低級 API 可能不是滿足日誌記錄需求的正確選擇。</span><span class="sxs-lookup"><span data-stu-id="38074-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="38074-158">您可能需要考慮日誌記錄框架。</span><span class="sxs-lookup"><span data-stu-id="38074-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="38074-159">該<xref:Microsoft.Extensions.Logging.ILogger>介面已用於創建一個公共日誌記錄介面，其中記錄器可以通過依賴項注入插入。</span><span class="sxs-lookup"><span data-stu-id="38074-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="38074-160">例如，為了允許您為應用程式`ASP.NET`做出最佳選擇，可以支援一系列內置和協力廠商框架：</span><span class="sxs-lookup"><span data-stu-id="38074-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="38074-161">ASP.NET內置日誌記錄提供程式</span><span class="sxs-lookup"><span data-stu-id="38074-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="38074-162">ASP.NET協力廠商日誌記錄提供程式</span><span class="sxs-lookup"><span data-stu-id="38074-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="38074-163">記錄相關引用</span><span class="sxs-lookup"><span data-stu-id="38074-163">Logging related references</span></span>

- [<span data-ttu-id="38074-164">如何：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="38074-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="38074-165">如何：將追蹤陳述式加入至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="38074-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="38074-166">[ASP.NET日誌記錄](/aspnet/core/fundamentals/logging)提供了它支援的日誌記錄技術的概述。</span><span class="sxs-lookup"><span data-stu-id="38074-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="38074-167">[C# 字串插值](../../csharp/language-reference/tokens/interpolated.md)可以簡化日誌記錄代碼的編寫。</span><span class="sxs-lookup"><span data-stu-id="38074-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="38074-168">該<xref:System.Exception.Message?displayProperty=nameWithType>屬性可用於記錄異常。</span><span class="sxs-lookup"><span data-stu-id="38074-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="38074-169">該<xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>類可用於在日誌中提供堆疊資訊。</span><span class="sxs-lookup"><span data-stu-id="38074-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="38074-170">效能考量</span><span class="sxs-lookup"><span data-stu-id="38074-170">Performance considerations</span></span>

<span data-ttu-id="38074-171">字串格式可能需要明顯的 CPU 處理時間。</span><span class="sxs-lookup"><span data-stu-id="38074-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="38074-172">在性能關鍵型應用程式中，建議您：</span><span class="sxs-lookup"><span data-stu-id="38074-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="38074-173">當沒有人在聽時，避免大量日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="38074-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="38074-174">通過檢查是否首先啟用日誌記錄，避免構造昂貴的日誌記錄消息。</span><span class="sxs-lookup"><span data-stu-id="38074-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="38074-175">只記錄有用內容。</span><span class="sxs-lookup"><span data-stu-id="38074-175">Only log what's useful.</span></span>
- <span data-ttu-id="38074-176">將花哨的格式延遲到分析階段。</span><span class="sxs-lookup"><span data-stu-id="38074-176">Defer fancy formatting to the analysis stage.</span></span>
