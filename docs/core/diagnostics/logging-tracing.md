---
title: 記錄和追蹤-.NET Core
description: .NET Core 記錄和追蹤的簡介。
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 46e64a7f60b88c26ceef9ac817be885bfa180c8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926356"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="7d08b-103">.NET Core 記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="7d08b-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="7d08b-104">針對相同的技巧，記錄和追蹤其實是兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="7d08b-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="7d08b-105">自電腦提早起，使用了簡單的技巧。</span><span class="sxs-lookup"><span data-stu-id="7d08b-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="7d08b-106">它只需要檢測應用程式來寫入輸出，以便稍後使用。</span><span class="sxs-lookup"><span data-stu-id="7d08b-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="7d08b-107">使用記錄和追蹤的理由</span><span class="sxs-lookup"><span data-stu-id="7d08b-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="7d08b-108">這項簡單的技巧非常強大。</span><span class="sxs-lookup"><span data-stu-id="7d08b-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="7d08b-109">它可以用於偵錯工具失敗的情況：</span><span class="sxs-lookup"><span data-stu-id="7d08b-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="7d08b-110">很長一段時間內發生的問題，可能會很容易使用傳統的偵錯工具進行 debug。</span><span class="sxs-lookup"><span data-stu-id="7d08b-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="7d08b-111">記錄允許長時間內的詳細事後剖析後評論。</span><span class="sxs-lookup"><span data-stu-id="7d08b-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="7d08b-112">相反地，偵錯工具會限制為即時分析。</span><span class="sxs-lookup"><span data-stu-id="7d08b-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="7d08b-113">多執行緒應用程式和分散式應用程式通常很難進行調試。</span><span class="sxs-lookup"><span data-stu-id="7d08b-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="7d08b-114">附加偵錯工具通常會修改行為。</span><span class="sxs-lookup"><span data-stu-id="7d08b-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="7d08b-115">您可以視需要分析詳細的記錄，以瞭解複雜的系統。</span><span class="sxs-lookup"><span data-stu-id="7d08b-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="7d08b-116">分散式應用程式中的問題可能是因為許多元件之間的複雜互動而引發，所以將偵錯工具連接到系統的每個部分可能並不合理。</span><span class="sxs-lookup"><span data-stu-id="7d08b-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="7d08b-117">許多服務都不應該停止。</span><span class="sxs-lookup"><span data-stu-id="7d08b-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="7d08b-118">附加偵錯工具通常會導致逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d08b-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="7d08b-119">問題不一定是預見。</span><span class="sxs-lookup"><span data-stu-id="7d08b-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="7d08b-120">記錄和追蹤是針對低額外負荷而設計的，因此在發生問題的情況下，程式一律會進行記錄。</span><span class="sxs-lookup"><span data-stu-id="7d08b-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="7d08b-121">.NET Core Api</span><span class="sxs-lookup"><span data-stu-id="7d08b-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="7d08b-122">列印樣式 Api</span><span class="sxs-lookup"><span data-stu-id="7d08b-122">Print style APIs</span></span>

<span data-ttu-id="7d08b-123"><xref:System.Console?displayProperty=nameWithType>、和<xref:System.Diagnostics.Trace?displayProperty=nameWithType>類別各自提供類似的<xref:System.Diagnostics.Debug?displayProperty=nameWithType>列印樣式 api，方便進行記錄。</span><span class="sxs-lookup"><span data-stu-id="7d08b-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="7d08b-124">選擇要使用的列印樣式 API 是由您決定。</span><span class="sxs-lookup"><span data-stu-id="7d08b-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="7d08b-125">主要的差異如下：</span><span class="sxs-lookup"><span data-stu-id="7d08b-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-126">一律啟用並一律寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="7d08b-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="7d08b-127">適用于您的客戶可能需要在版本中看到的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d08b-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="7d08b-128">因為這是最簡單的方法，所以通常用於臨機操作暫存的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7d08b-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="7d08b-129">此 debug 程式碼通常不會簽入原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="7d08b-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-130">只有在定義`TRACE`時才啟用。</span><span class="sxs-lookup"><span data-stu-id="7d08b-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="7d08b-131">預設會寫入<xref:System.Diagnostics.Trace.Listeners>至附加的。 <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="7d08b-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="7d08b-132">建立將在大部分組建中啟用的記錄檔時，請使用此 API。</span><span class="sxs-lookup"><span data-stu-id="7d08b-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-133">只有在定義`DEBUG`時才啟用。</span><span class="sxs-lookup"><span data-stu-id="7d08b-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="7d08b-134">寫入附加的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7d08b-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="7d08b-135">`*nix` 當`COMPlus_DebugWriteToStdErr`已設定時，寫入 stderr。</span><span class="sxs-lookup"><span data-stu-id="7d08b-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="7d08b-136">建立只會在 debug 組建中啟用的記錄檔時，請使用此 API。</span><span class="sxs-lookup"><span data-stu-id="7d08b-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="7d08b-137">記錄事件</span><span class="sxs-lookup"><span data-stu-id="7d08b-137">Logging events</span></span>

<span data-ttu-id="7d08b-138">下列 Api 是更多事件導向。</span><span class="sxs-lookup"><span data-stu-id="7d08b-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="7d08b-139">與其記錄簡單的字串，它們會記錄事件物件。</span><span class="sxs-lookup"><span data-stu-id="7d08b-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-140">EventSource 是主要根 .NET Core 追蹤 API。</span><span class="sxs-lookup"><span data-stu-id="7d08b-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="7d08b-141">適用于所有 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="7d08b-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="7d08b-142">只允許追蹤可序列化物件。</span><span class="sxs-lookup"><span data-stu-id="7d08b-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="7d08b-143">寫入附加的[事件](xref:System.Diagnostics.Tracing.EventListener)接聽程式。</span><span class="sxs-lookup"><span data-stu-id="7d08b-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="7d08b-144">.NET Core 會針對下列各項提供接聽程式：</span><span class="sxs-lookup"><span data-stu-id="7d08b-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="7d08b-145">所有平臺上的 .NET Core EventPipe</span><span class="sxs-lookup"><span data-stu-id="7d08b-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="7d08b-146">Windows 事件追蹤（ETW）</span><span class="sxs-lookup"><span data-stu-id="7d08b-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="7d08b-147">適用于 Linux 的 LTTng 追蹤架構</span><span class="sxs-lookup"><span data-stu-id="7d08b-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-148">包含在 .NET Core 中，以及做為 .NET Framework 的[NuGet 套件](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)。</span><span class="sxs-lookup"><span data-stu-id="7d08b-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="7d08b-149">允許非可序列化物件的同進程追蹤。</span><span class="sxs-lookup"><span data-stu-id="7d08b-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="7d08b-150">包含橋接器，可讓所選的已記錄物件欄位寫入<xref:System.Diagnostics.Tracing.EventSource>。</span><span class="sxs-lookup"><span data-stu-id="7d08b-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-151">提供明確的方式來識別特定活動或交易所產生的記錄檔訊息。</span><span class="sxs-lookup"><span data-stu-id="7d08b-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="7d08b-152">此物件可用來讓不同服務之間的記錄相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7d08b-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="7d08b-153">僅限 Windows。</span><span class="sxs-lookup"><span data-stu-id="7d08b-153">Windows only.</span></span>
  - <span data-ttu-id="7d08b-154">將訊息寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7d08b-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="7d08b-155">系統管理員預期 Windows 事件記錄檔中會出現嚴重的應用程式錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7d08b-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="7d08b-156">ILogger 和記錄架構</span><span class="sxs-lookup"><span data-stu-id="7d08b-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="7d08b-157">低層級 Api 可能不是您記錄需求的正確選擇。</span><span class="sxs-lookup"><span data-stu-id="7d08b-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="7d08b-158">您可能想要考慮使用記錄架構。</span><span class="sxs-lookup"><span data-stu-id="7d08b-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="7d08b-159"><xref:Microsoft.Extensions.Logging.ILogger>介面已用來建立一般記錄介面，可透過相依性插入來插入記錄器。</span><span class="sxs-lookup"><span data-stu-id="7d08b-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="7d08b-160">比方說，若要讓您為應用程式`ASP.NET`提供最佳選擇，讓您能夠選擇內建和協力廠商架構：</span><span class="sxs-lookup"><span data-stu-id="7d08b-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="7d08b-161">ASP.NET 內建記錄提供者</span><span class="sxs-lookup"><span data-stu-id="7d08b-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="7d08b-162">ASP.NET 協力廠商記錄提供者</span><span class="sxs-lookup"><span data-stu-id="7d08b-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="7d08b-163">記錄相關參考</span><span class="sxs-lookup"><span data-stu-id="7d08b-163">Logging related references</span></span>

- [<span data-ttu-id="7d08b-164">如何：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="7d08b-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="7d08b-165">如何：將追蹤語句新增至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="7d08b-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="7d08b-166">[ASP.NET 記錄](/aspnet/core/fundamentals/logging)提供它所支援的記錄技術的總覽。</span><span class="sxs-lookup"><span data-stu-id="7d08b-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="7d08b-167">字串內插補點可簡化撰寫記錄程式碼的程式。 [ C# ](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="7d08b-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="7d08b-168"><xref:System.Exception.Message?displayProperty=nameWithType>屬性適用于記錄例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7d08b-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="7d08b-169">在<xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>您的記錄中提供堆疊資訊時，類別可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="7d08b-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="7d08b-170">效能考量</span><span class="sxs-lookup"><span data-stu-id="7d08b-170">Performance considerations</span></span>

<span data-ttu-id="7d08b-171">字串格式設定可能會產生顯著的 CPU 處理時間。</span><span class="sxs-lookup"><span data-stu-id="7d08b-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="7d08b-172">在效能關鍵應用程式中，建議您：</span><span class="sxs-lookup"><span data-stu-id="7d08b-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="7d08b-173">當沒有人在接聽時，請避免大量記錄。</span><span class="sxs-lookup"><span data-stu-id="7d08b-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="7d08b-174">請先檢查是否已啟用記錄，以避免建立昂貴的記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="7d08b-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="7d08b-175">只記錄有用的功能。</span><span class="sxs-lookup"><span data-stu-id="7d08b-175">Only log what's useful.</span></span>
- <span data-ttu-id="7d08b-176">將複雜的格式延後到分析階段。</span><span class="sxs-lookup"><span data-stu-id="7d08b-176">Defer fancy formatting to the analysis stage.</span></span>
