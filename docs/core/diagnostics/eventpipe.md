---
title: EventPipe 總覽
description: 瞭解 EventPipe 以及如何使用它來追蹤您的 .NET 應用程式，以診斷效能問題。
ms.date: 11/09/2020
ms.topic: overview
ms.openlocfilehash: d30cdf02c3ae300401febe2078dfd3431269c73e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688568"
---
# <a name="eventpipe"></a>EventPipe

EventPipe 是執行時間元件，可用於收集追蹤資料，類似于 ETW 或 LTTng。 EventPipe 的目標是要讓 .NET 開發人員輕鬆地追蹤其 .NET 應用程式，而不需要依賴平臺特定的 OS 原生元件，例如 ETW 或 LTTng。

EventPipe 是許多診斷工具背後的機制，可用來取用執行時間所發出的事件，以及使用 [EventSource](xref:System.Diagnostics.Tracing.EventSource)撰寫的自訂事件。

本文概要說明如何及如何使用 EventPipe，以及如何設定它以最符合您的需求。

## <a name="eventpipe-basics"></a>EventPipe 基本概念

EventPipe 會匯總執行時間元件發出的事件，例如，即時編譯器或垃圾收集行程，以及從程式庫和使用者程式碼中的 [EventSource](xref:System.Diagnostics.Tracing.EventSource) 實例寫入的事件。

然後，系統會將事件序列化，並且可以直接寫入檔案，或透過診斷埠從 proces cannot 使用。 在 Windows 上，診斷埠會實作為 `NamedPipe` 。 在非 Windows 平臺上（例如 Linux 或 macOS），它是使用 Unix 網域通訊端來實行。 如需診斷埠的詳細資訊，以及如何透過其自訂處理序間通訊協定與其互動的詳細資訊，請參閱 [診斷 IPC 通訊協定檔](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)。

然後，EventPipe 會以 `.nettrace` 檔案格式（透過診斷埠或直接寫入檔案）來寫入序列化的事件。 若要深入瞭解 EventPipe 序列化格式，請參閱 [EventPipe 格式檔](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md)。

## <a name="eventpipe-vs-etwlttng"></a>EventPipe 與 ETW/LTTng

EventPipe 是 .NET 執行時間的一部分 (CoreCLR) ，其設計目的是在 .NET Core 支援的所有平臺上以相同的方式運作。 這可讓您以 EventPipe （例如、和）為基礎的追蹤工具 `dotnet-counters` `dotnet-gcdump` `dotnet-trace` 跨平臺順暢地運作。

不過，因為 EventPipe 是執行時間內建元件，所以其範圍僅限於 managed 程式碼和執行時間本身。 EventPipe 無法用來追蹤一些較低層級的事件，例如解決機器碼堆疊或取得各種核心事件。 如果您在應用程式中使用 C/c + + interop，或您想要追蹤以 c + +) 撰寫的執行時間本身 (，或想要更深入診斷需要核心事件的應用程式行為 (也就是原生執行緒內容切換事件) 您應使用 ETW 或 [perf/LTTng](./trace-perfcollect-lttng.md)。

EventPipe 和 ETW/LTTng 之間的另一個主要差異在於系統管理員/根許可權需求。 若要使用 ETW 或 LTTng 追蹤應用程式，您必須是系統管理員/根目錄。 使用 EventPipe 時，您可以追蹤應用程式，只要追蹤 (例如， `dotnet-trace`) 會以與啟動應用程式的使用者相同的使用者來執行。

下表是 EventPipe 和 ETW/LTTng 之間差異的摘要。

|功能|EventPipe|ETW|LTTng|
|-------|---------|---|-----------|
|跨平台|是|只有 Windows) 上沒有 (|只有支援的 Linux 散發版本) 上沒有 (|
|需要系統管理員/根許可權|否|是|是|
|可以取得作業系統/核心事件|否|是|是|
|可以解析原生呼叫堆疊|否|是|是|

## <a name="use-eventpipe-to-trace-your-net-application"></a>使用 EventPipe 來追蹤您的 .NET 應用程式

您可以使用 EventPipe，透過許多方式來追蹤您的 .NET 應用程式：

* 使用以 EventPipe 為基礎的其中一個 [診斷工具](#tools-using-eventpipe) 。

* 使用 [NETCore](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) 撰寫您自己的工具，自行設定並開始 EventPipe 會話。

* 使用 [環境變數](#trace-using-environment-variables) 來啟動 EventPipe。

當您產生 `nettrace` 包含 EventPipe 事件的檔案之後，您可以在或 Visual Studio 中查看檔案 [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) 。 在非 Windows 平臺上，您可以使用命令將檔案轉換 `nettrace` 成 `speedscope` 或 `Chromium` 追蹤格式 [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) ，並使用 [`speedscope`](https://www.speedscope.app/) 或 Chrome DevTools 來加以查看。

您也可以使用 [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md)，以程式設計方式分析 EventPipe 追蹤。

### <a name="tools-that-use-eventpipe"></a>使用 EventPipe 的工具

這是使用 EventPipe 來追蹤應用程式的最簡單方式。 若要深入瞭解如何使用這些工具的詳細資訊，請參閱每個工具的檔。

* [dotnet-計數器](./dotnet-counters.md) 可讓您監視和收集 .net 執行時間和核心程式庫所發出的各種計量，以及您可以撰寫的自訂計量。

* [dotnet-gcdump](./dotnet-gcdump.md) 可讓您收集即時進程的 GC 堆積傾印，以分析應用程式的受控堆積。

* [dotnet 追蹤](./dotnet-trace.md) 可讓您收集應用程式的追蹤，以分析效能。

## <a name="trace-using-environment-variables"></a>使用環境變數進行追蹤

使用 EventPipe 的慣用機制是使用或連結 `dotnet-trace` `Microsoft.Diagnostics.NETCore.Client` 庫。

不過，您可以使用下列環境變數來設定應用程式上的 EventPipe 會話，並讓它將追蹤直接寫入至檔案。 若要停止追蹤，請結束應用程式。

* `COMPlus_EnableEventPipe`：將此設定為， `1` 以啟動直接寫入檔案的 EventPipe 會話。 預設值是 `0`。

* `COMPlus_EventPipeOutputPath`：當其設定為透過執行時，輸出 EventPipe 追蹤檔案的路徑 `COMPlus_EnableEventPipe` 。 預設值是 `trace.nettrace` ，它會在應用程式執行所在的相同目錄中建立。

* `COMPlus_CircularBufferMB`： EventPipe 設定為透過執行時，所使用的內部緩衝區大小 `COMPlus_EnableEventPipe` 。

* `COMPlus_EventPipeConfig`：使用啟動 EventPipe 會話時，設定 EventPipe 會話設定 `COMPlus_EnableEventPipe` 。

  語法如下：

  `<provider>:<keyword>:<level>`

  您也可以使用逗號串連來指定多個提供者：

  `<provider1>:<keyword1>:<level1>,<provider2>:<keyword2>:<level2>`

  如果未設定此環境變數，但已啟用 EventPipe `COMPlus_EnableEventPipe` ，則會使用下列關鍵字和層級啟用下列提供者來開始追蹤：

  - `Microsoft-Windows-DotNETRuntime:4c14fccbd:5`
  - `Microsoft-Windows-DotNETRuntimePrivate:4002000b:5`
  - `Microsoft-DotNETCore-SampleProfiler:0:5`
