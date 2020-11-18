---
title: EventPipe 總覽
description: 瞭解 EventPipe 以及如何使用它來追蹤您的 .NET 應用程式，以診斷效能問題。
ms.date: 11/09/2020
ms.topic: overview
ms.openlocfilehash: 00378c4f409b307afa9183e40de6078cdafd3ae7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820614"
---
# <a name="eventpipe"></a><span data-ttu-id="40adf-103">EventPipe</span><span class="sxs-lookup"><span data-stu-id="40adf-103">EventPipe</span></span>

<span data-ttu-id="40adf-104">EventPipe 是執行時間元件，可用於收集追蹤資料，類似于 ETW 或 LTTng。</span><span class="sxs-lookup"><span data-stu-id="40adf-104">EventPipe is a runtime component that can be used to collect tracing data, similar to ETW or LTTng.</span></span> <span data-ttu-id="40adf-105">EventPipe 的目標是要讓 .NET 開發人員輕鬆地追蹤其 .NET 應用程式，而不需要依賴平臺特定的 OS 原生元件，例如 ETW 或 LTTng。</span><span class="sxs-lookup"><span data-stu-id="40adf-105">The goal of EventPipe is to allow .NET developers to easily trace their .NET applications without having to rely on platform-specific OS-native components such as ETW or LTTng.</span></span>

<span data-ttu-id="40adf-106">EventPipe 是許多診斷工具背後的機制，可用來取用執行時間所發出的事件，以及使用 [EventSource](xref:System.Diagnostics.Tracing.EventSource)撰寫的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="40adf-106">EventPipe is the mechanism behind many of the diagnostic tools and can be used for consuming events emitted by the runtime as well as custom events written with [EventSource](xref:System.Diagnostics.Tracing.EventSource).</span></span>

<span data-ttu-id="40adf-107">本文概要說明如何及如何使用 EventPipe，以及如何設定它以最符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="40adf-107">This article is a high-level overview of EventPipe describing when and how to use EventPipe, and how to configure it to best suit your needs.</span></span>

## <a name="eventpipe-basics"></a><span data-ttu-id="40adf-108">EventPipe 基本概念</span><span class="sxs-lookup"><span data-stu-id="40adf-108">EventPipe basics</span></span>

<span data-ttu-id="40adf-109">EventPipe 會匯總執行時間元件發出的事件，例如，即時編譯器或垃圾收集行程，以及從程式庫和使用者程式碼中的 [EventSource](xref:System.Diagnostics.Tracing.EventSource) 實例寫入的事件。</span><span class="sxs-lookup"><span data-stu-id="40adf-109">EventPipe aggregates events emitted by runtime components - for example, the Just-In-Time compiler or the garbage collector - and events written from [EventSource](xref:System.Diagnostics.Tracing.EventSource) instances in the libraries and user code.</span></span>

<span data-ttu-id="40adf-110">然後，系統會將事件序列化，並且可以直接寫入檔案，或透過診斷埠從 proces cannot 使用。</span><span class="sxs-lookup"><span data-stu-id="40adf-110">The events are then serialized and can be written directly to a file or consumed through a Diagnostics Port from out-of-proces.</span></span> <span data-ttu-id="40adf-111">在 Windows 上，診斷埠會實作為 `NamedPipe` 。</span><span class="sxs-lookup"><span data-stu-id="40adf-111">On Windows, Diagnostic Ports are implemented as `NamedPipe`s.</span></span> <span data-ttu-id="40adf-112">在非 Windows 平臺上（例如 Linux 或 macOS），它是使用 Unix 網域通訊端來實行。</span><span class="sxs-lookup"><span data-stu-id="40adf-112">On non-Windows platforms, such as Linux or macOS, it is implemented using Unix Domain Sockets.</span></span> <span data-ttu-id="40adf-113">如需診斷埠的詳細資訊，以及如何透過其自訂處理序間通訊協定與其互動的詳細資訊，請參閱 [診斷 IPC 通訊協定檔](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)。</span><span class="sxs-lookup"><span data-stu-id="40adf-113">For more information about the Diagnostics Port and how to interact with it via its custom inter-process communication protocol, see the [diagnostics IPC protocol documentation](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>

<span data-ttu-id="40adf-114">然後，EventPipe 會以 `.nettrace` 檔案格式（透過診斷埠或直接寫入檔案）來寫入序列化的事件。</span><span class="sxs-lookup"><span data-stu-id="40adf-114">EventPipe then writes the serialized events in the `.nettrace` file format, either as a stream via Diagnostic Ports or directly to a file.</span></span> <span data-ttu-id="40adf-115">若要深入瞭解 EventPipe 序列化格式，請參閱 [EventPipe 格式檔](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md)。</span><span class="sxs-lookup"><span data-stu-id="40adf-115">To learn more about the EventPipe serialization format, refer to the [EventPipe format documentation](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md).</span></span>

## <a name="eventpipe-vs-etwlttng"></a><span data-ttu-id="40adf-116">EventPipe 與 ETW/LTTng</span><span class="sxs-lookup"><span data-stu-id="40adf-116">EventPipe vs. ETW/LTTng</span></span>

<span data-ttu-id="40adf-117">EventPipe 是 .NET 執行時間的一部分 (CoreCLR) ，其設計目的是在 .NET Core 支援的所有平臺上以相同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="40adf-117">EventPipe is part of the .NET runtime (CoreCLR) and is designed to work the same way across all the platforms .NET Core supports.</span></span> <span data-ttu-id="40adf-118">這可讓您以 EventPipe （例如、和）為基礎的追蹤工具 `dotnet-counters` `dotnet-gcdump` `dotnet-trace` 跨平臺順暢地運作。</span><span class="sxs-lookup"><span data-stu-id="40adf-118">This allows tracing tools based on EventPipe, such as `dotnet-counters`, `dotnet-gcdump`, and `dotnet-trace`, to work seamlessly across platforms.</span></span>

<span data-ttu-id="40adf-119">不過，因為 EventPipe 是執行時間內建元件，所以其範圍僅限於 managed 程式碼和執行時間本身。</span><span class="sxs-lookup"><span data-stu-id="40adf-119">However, because EventPipe is a runtime built-in component, its scope is limited to managed code and the runtime itself.</span></span> <span data-ttu-id="40adf-120">EventPipe 無法用來追蹤一些較低層級的事件，例如解決機器碼堆疊或取得各種核心事件。</span><span class="sxs-lookup"><span data-stu-id="40adf-120">EventPipe cannot be used for tracking some lower-level events, such as resolving native code stack or getting various kernel events.</span></span> <span data-ttu-id="40adf-121">如果您在應用程式中使用 C/c + + interop，或您想要追蹤以 c + +) 撰寫的執行時間本身 (，或想要更深入診斷需要核心事件的應用程式行為 (也就是原生執行緒內容切換事件) 您應使用 ETW 或 [perf/LTTng](./trace-perfcollect-lttng.md)。</span><span class="sxs-lookup"><span data-stu-id="40adf-121">If you use C/C++ interop in your app or you want to trace the runtime itself (which is written in C++), or want deeper diagnostics into the behavior of the app that requires kernel events (that is, native-thread context-switching events) you should use ETW or [perf/LTTng](./trace-perfcollect-lttng.md).</span></span>

<span data-ttu-id="40adf-122">EventPipe 和 ETW/LTTng 之間的另一個主要差異在於系統管理員/根許可權需求。</span><span class="sxs-lookup"><span data-stu-id="40adf-122">Another major difference between EventPipe and ETW/LTTng is admin/root privilege requirement.</span></span> <span data-ttu-id="40adf-123">若要使用 ETW 或 LTTng 追蹤應用程式，您必須是系統管理員/根目錄。</span><span class="sxs-lookup"><span data-stu-id="40adf-123">To trace an application using ETW or LTTng you need to be an admin/root.</span></span> <span data-ttu-id="40adf-124">使用 EventPipe 時，您可以追蹤應用程式，只要追蹤 (例如， `dotnet-trace`) 會以與啟動應用程式的使用者相同的使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="40adf-124">Using EventPipe, you can trace applications as long as the tracer (for example, `dotnet-trace`) is run as the same user as the user that launched the application.</span></span>

<span data-ttu-id="40adf-125">下表是 EventPipe 和 ETW/LTTng 之間差異的摘要。</span><span class="sxs-lookup"><span data-stu-id="40adf-125">The following table is a summary of the differences between EventPipe and ETW/LTTng.</span></span>

|<span data-ttu-id="40adf-126">功能</span><span class="sxs-lookup"><span data-stu-id="40adf-126">Feature</span></span>|<span data-ttu-id="40adf-127">EventPipe</span><span class="sxs-lookup"><span data-stu-id="40adf-127">EventPipe</span></span>|<span data-ttu-id="40adf-128">ETW</span><span class="sxs-lookup"><span data-stu-id="40adf-128">ETW</span></span>|<span data-ttu-id="40adf-129">LTTng</span><span class="sxs-lookup"><span data-stu-id="40adf-129">LTTng</span></span>|
|-------|---------|---|-----------|
|<span data-ttu-id="40adf-130">跨平台</span><span class="sxs-lookup"><span data-stu-id="40adf-130">Cross-platform</span></span>|<span data-ttu-id="40adf-131">是</span><span class="sxs-lookup"><span data-stu-id="40adf-131">Yes</span></span>|<span data-ttu-id="40adf-132">只有 Windows) 上沒有 (</span><span class="sxs-lookup"><span data-stu-id="40adf-132">No (only on Windows)</span></span>|<span data-ttu-id="40adf-133">只有支援的 Linux 散發版本) 上沒有 (</span><span class="sxs-lookup"><span data-stu-id="40adf-133">No (only on supported Linux distros)</span></span>|
|<span data-ttu-id="40adf-134">需要系統管理員/根許可權</span><span class="sxs-lookup"><span data-stu-id="40adf-134">Require admin/root privilege</span></span>|<span data-ttu-id="40adf-135">否</span><span class="sxs-lookup"><span data-stu-id="40adf-135">No</span></span>|<span data-ttu-id="40adf-136">是</span><span class="sxs-lookup"><span data-stu-id="40adf-136">Yes</span></span>|<span data-ttu-id="40adf-137">是</span><span class="sxs-lookup"><span data-stu-id="40adf-137">Yes</span></span>|
|<span data-ttu-id="40adf-138">可以取得作業系統/核心事件</span><span class="sxs-lookup"><span data-stu-id="40adf-138">Can get OS/kernel events</span></span>|<span data-ttu-id="40adf-139">否</span><span class="sxs-lookup"><span data-stu-id="40adf-139">No</span></span>|<span data-ttu-id="40adf-140">是</span><span class="sxs-lookup"><span data-stu-id="40adf-140">Yes</span></span>|<span data-ttu-id="40adf-141">是</span><span class="sxs-lookup"><span data-stu-id="40adf-141">Yes</span></span>|
|<span data-ttu-id="40adf-142">可以解析原生呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="40adf-142">Can resolve native callstacks</span></span>|<span data-ttu-id="40adf-143">否</span><span class="sxs-lookup"><span data-stu-id="40adf-143">No</span></span>|<span data-ttu-id="40adf-144">是</span><span class="sxs-lookup"><span data-stu-id="40adf-144">Yes</span></span>|<span data-ttu-id="40adf-145">是</span><span class="sxs-lookup"><span data-stu-id="40adf-145">Yes</span></span>|

## <a name="use-eventpipe-to-trace-your-net-application"></a><span data-ttu-id="40adf-146">使用 EventPipe 來追蹤您的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="40adf-146">Use EventPipe to trace your .NET application</span></span>

<span data-ttu-id="40adf-147">您可以使用 EventPipe，透過許多方式來追蹤您的 .NET 應用程式：</span><span class="sxs-lookup"><span data-stu-id="40adf-147">You can use EventPipe to trace your .NET application in many ways:</span></span>

* <span data-ttu-id="40adf-148">使用以 EventPipe 為基礎的其中一個 [診斷工具](#tools-that-use-eventpipe) 。</span><span class="sxs-lookup"><span data-stu-id="40adf-148">Use one of the [diagnostics tools](#tools-that-use-eventpipe) that are built on top of EventPipe.</span></span>

* <span data-ttu-id="40adf-149">使用 [NETCore](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) 撰寫您自己的工具，自行設定並開始 EventPipe 會話。</span><span class="sxs-lookup"><span data-stu-id="40adf-149">Use [Microsoft.Diagnostics.NETCore.Client](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) library to write your own tool to configure and start EventPipe sessions yourself.</span></span>

* <span data-ttu-id="40adf-150">使用 [環境變數](#trace-using-environment-variables) 來啟動 EventPipe。</span><span class="sxs-lookup"><span data-stu-id="40adf-150">Use [environment variables](#trace-using-environment-variables) to start EventPipe.</span></span>

<span data-ttu-id="40adf-151">當您產生 `nettrace` 包含 EventPipe 事件的檔案之後，您可以在或 Visual Studio 中查看檔案 [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) 。</span><span class="sxs-lookup"><span data-stu-id="40adf-151">After you've produced a `nettrace` file that contains your EventPipe events, you can view the file in [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) or Visual Studio.</span></span> <span data-ttu-id="40adf-152">在非 Windows 平臺上，您可以使用命令將檔案轉換 `nettrace` 成 `speedscope` 或 `Chromium` 追蹤格式 [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) ，並使用 [`speedscope`](https://www.speedscope.app/) 或 Chrome DevTools 來加以查看。</span><span class="sxs-lookup"><span data-stu-id="40adf-152">On non-Windows platforms, you can convert the `nettrace` file to a `speedscope` or `Chromium` trace format by using [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) command and view it with [`speedscope`](https://www.speedscope.app/) or Chrome DevTools.</span></span>

<span data-ttu-id="40adf-153">您也可以使用 [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md)，以程式設計方式分析 EventPipe 追蹤。</span><span class="sxs-lookup"><span data-stu-id="40adf-153">You can also analyze EventPipe traces programmatically with [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md).</span></span>

### <a name="tools-that-use-eventpipe"></a><span data-ttu-id="40adf-154">使用 EventPipe 的工具</span><span class="sxs-lookup"><span data-stu-id="40adf-154">Tools that use EventPipe</span></span>

<span data-ttu-id="40adf-155">這是使用 EventPipe 來追蹤應用程式的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="40adf-155">This is the easiest way to use EventPipe to trace your application.</span></span> <span data-ttu-id="40adf-156">若要深入瞭解如何使用這些工具的詳細資訊，請參閱每個工具的檔。</span><span class="sxs-lookup"><span data-stu-id="40adf-156">To learn more about how to use each of these tools, refer to each tool's documentation.</span></span>

* <span data-ttu-id="40adf-157">[dotnet-計數器](./dotnet-counters.md) 可讓您監視和收集 .net 執行時間和核心程式庫所發出的各種計量，以及您可以撰寫的自訂計量。</span><span class="sxs-lookup"><span data-stu-id="40adf-157">[dotnet-counters](./dotnet-counters.md) lets you monitor and collect various metrics emitted by the .NET runtime and core libraries, as well as custom metrics you can write.</span></span>

* <span data-ttu-id="40adf-158">[dotnet-gcdump](./dotnet-gcdump.md) 可讓您收集即時進程的 GC 堆積傾印，以分析應用程式的受控堆積。</span><span class="sxs-lookup"><span data-stu-id="40adf-158">[dotnet-gcdump](./dotnet-gcdump.md) lets you collect GC heap dumps of live processes for analyzing an application's managed heap.</span></span>

* <span data-ttu-id="40adf-159">[dotnet 追蹤](./dotnet-trace.md) 可讓您收集應用程式的追蹤，以分析效能。</span><span class="sxs-lookup"><span data-stu-id="40adf-159">[dotnet-trace](./dotnet-trace.md) lets you collect traces of applications to analyze for performance.</span></span>

## <a name="trace-using-environment-variables"></a><span data-ttu-id="40adf-160">使用環境變數進行追蹤</span><span class="sxs-lookup"><span data-stu-id="40adf-160">Trace using environment variables</span></span>

<span data-ttu-id="40adf-161">使用 EventPipe 的慣用機制是使用或連結 `dotnet-trace` `Microsoft.Diagnostics.NETCore.Client` 庫。</span><span class="sxs-lookup"><span data-stu-id="40adf-161">The preferred mechanism for using EventPipe is to use `dotnet-trace` or the `Microsoft.Diagnostics.NETCore.Client` library.</span></span>

<span data-ttu-id="40adf-162">不過，您可以使用下列環境變數來設定應用程式上的 EventPipe 會話，並讓它將追蹤直接寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="40adf-162">However, you can use the following environment variables to set up an EventPipe session on an app and have it write the trace directly to a file.</span></span> <span data-ttu-id="40adf-163">若要停止追蹤，請結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="40adf-163">To stop tracing, exit the application.</span></span>

* <span data-ttu-id="40adf-164">`COMPlus_EnableEventPipe`：將此設定為， `1` 以啟動直接寫入檔案的 EventPipe 會話。</span><span class="sxs-lookup"><span data-stu-id="40adf-164">`COMPlus_EnableEventPipe`: Set this to `1` to start an EventPipe session that writes directly to a file.</span></span> <span data-ttu-id="40adf-165">預設值是 `0`。</span><span class="sxs-lookup"><span data-stu-id="40adf-165">The default value is `0`.</span></span>

* <span data-ttu-id="40adf-166">`COMPlus_EventPipeOutputPath`：當其設定為透過執行時，輸出 EventPipe 追蹤檔案的路徑 `COMPlus_EnableEventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="40adf-166">`COMPlus_EventPipeOutputPath`: The path to the output EventPipe trace file when it's configured to run via `COMPlus_EnableEventPipe`.</span></span> <span data-ttu-id="40adf-167">預設值是 `trace.nettrace` ，它會在應用程式執行所在的相同目錄中建立。</span><span class="sxs-lookup"><span data-stu-id="40adf-167">The default value is `trace.nettrace`, which will be created in the same directory that the app is running from.</span></span>

* <span data-ttu-id="40adf-168">`COMPlus_CircularBufferMB`： EventPipe 設定為透過執行時，所使用的內部緩衝區大小 `COMPlus_EnableEventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="40adf-168">`COMPlus_CircularBufferMB`: The size of the internal buffer that is used by EventPipe when it's configured to run via `COMPlus_EnableEventPipe`.</span></span>

* <span data-ttu-id="40adf-169">`COMPlus_EventPipeConfig`：使用啟動 EventPipe 會話時，設定 EventPipe 會話設定 `COMPlus_EnableEventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="40adf-169">`COMPlus_EventPipeConfig`: Sets up the EventPipe session configuration when starting an EventPipe session with `COMPlus_EnableEventPipe`.</span></span>

  <span data-ttu-id="40adf-170">語法如下：</span><span class="sxs-lookup"><span data-stu-id="40adf-170">The syntax is as follows:</span></span>

  `<provider>:<keyword>:<level>`

  <span data-ttu-id="40adf-171">您也可以使用逗號串連來指定多個提供者：</span><span class="sxs-lookup"><span data-stu-id="40adf-171">You can also specify multiple providers by concatenating them with a comma:</span></span>

  `<provider1>:<keyword1>:<level1>,<provider2>:<keyword2>:<level2>`

  <span data-ttu-id="40adf-172">如果未設定此環境變數，但已啟用 EventPipe `COMPlus_EnableEventPipe` ，則會使用下列關鍵字和層級啟用下列提供者來開始追蹤：</span><span class="sxs-lookup"><span data-stu-id="40adf-172">If this environment variable is not set but EventPipe is enabled by `COMPlus_EnableEventPipe`, it will start tracing by enabling the following providers with the following keywords and levels:</span></span>

  - `Microsoft-Windows-DotNETRuntime:4c14fccbd:5`
  - `Microsoft-Windows-DotNETRuntimePrivate:4002000b:5`
  - `Microsoft-DotNETCore-SampleProfiler:0:5`
