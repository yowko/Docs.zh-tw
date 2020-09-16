---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: e97acccbe3bdd577ee600cefb9f1f0528d3c1ac0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538523"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 中有哪些診斷工具可供使用？

軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。

此文章會協助您找出所需的各種工具。

## <a name="managed-debuggers"></a>受控偵錯工具

[受管理的調試](managed-debuggers.md) 程式可讓您與程式互動。 暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。 偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。

## <a name="logging-and-tracing"></a>記錄和追蹤

[記錄和追蹤](logging-tracing.md) 是相關的技術。 它們會參考檢測程式碼以建立記錄檔。 那些檔案會記錄程式所執行之內容的詳細資料。 這些詳細資料可用來診斷最為複雜的問題。 透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。

## <a name="unit-testing"></a>單元測試

[單元測試](../testing/index.md) 是持續整合和部署高品質軟體的重要元件。 單元測試的設計是要在您中斷某個項目時提前警告您。

## <a name="debug-linux-dumps"></a>對 Linux 傾印進行偵錯

[Debug linux](debug-linux-dumps.md) 傾印說明如何收集和分析 linux 上的傾印。

## <a name="net-core-diagnostic-global-tools"></a>.NET Core 診斷通用工具

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-計數器](dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。 它會觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。 例如，您可以快速監視 CPU 使用量之類的專案，或在 .NET Core 應用程式中擲回例外狀況的速率。

### <a name="dotnet-dump"></a>dotnet-dump

[Dotnet](dotnet-dump.md)傾印工具可在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印。

### <a name="dotnet-gcdump"></a>dotnet-gcdump

[Dotnet-gcdump](dotnet-gcdump.md)工具是一種方式，可 (垃圾收集行程收集即時 .net 處理常式) 傾印。

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core 包含 `EventPipe` 用來公開診斷資料的呼叫。 [Dotnet 追蹤](dotnet-trace.md)工具可讓您從應用程式取用有趣的分析資料，在需要根本原因的應用程式執行速度變慢的情況下，可能會有所説明。

### <a name="dotnet-symbol"></a>dotnet-symbol

[dotnet-符號](dotnet-symbol.md) 會下載檔案 (符號、DAC/DBI、主機檔案等 ) 需要開啟核心傾印或小型傾印。 如果您需要符號和模組，以針對在不同電腦上所捕捉的傾印檔案進行調試，請使用此工具。

### <a name="dotnet-sos"></a>dotnet-sos

[dotnet-sos](dotnet-sos.md) 可用來將 [sos 偵錯工具擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能安裝在 Linux 或 MacOS (或 Windows 上（如果使用舊版偵錯工具) ）。

## <a name="net-core-diagnostics-tutorials"></a>.NET Core 診斷教學課程

### <a name="debug-a-memory-leak"></a>針對記憶體流失進行偵錯

[教學課程：偵測記憶體](debug-memory-leak.md) 流失會逐步引導您找出記憶體流失。 [Dotnet 計數器](dotnet-counters.md)工具是用來確認流失，而[dotnet](dotnet-dump.md)傾印工具是用來診斷流失的問題。

### <a name="debug-high-cpu-usage"></a>針對高 CPU 使用量進行偵錯

[教學課程：「高 cpu 使用率](debug-highcpu.md) 」會逐步引導您調查高 cpu 使用率。 它會使用 [dotnet 計數器](dotnet-counters.md) 工具來確認高 CPU 使用率。 接著，它會逐步引導您使用 [追蹤效能分析公用程式 (`dotnet-trace`) ](dotnet-trace.md) 或 Linux `perf` 收集和查看 CPU 使用量設定檔。

### <a name="debug-deadlock"></a>針對死結進行偵錯

[教學課程： Debug 鎖死](debug-deadlock.md) 會示範如何使用 [dotnet](dotnet-dump.md) 傾印工具來調查執行緒和鎖定。
