---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: dc64c03ee9c8cee6a5b3c5cc089b4a1a2c27f84a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924778"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 中有哪些診斷工具可供使用？

軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。

此文章會協助您找出所需的各種工具。

## <a name="managed-debuggers"></a>受控偵錯工具

[受管理的調試](managed-debuggers.md)程式可讓您與程式互動。 暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。 偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。

## <a name="logging-and-tracing"></a>記錄和追蹤

[記錄和追蹤](logging-tracing.md)是相關的技術。 它們會參考檢測程式碼以建立記錄檔。 那些檔案會記錄程式所執行之內容的詳細資料。 這些詳細資料可用來診斷最為複雜的問題。 透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。

## <a name="unit-testing"></a>單元測試

[單元測試](../testing/index.md)是持續整合和部署高品質軟體的重要元件。 單元測試的設計是要在您中斷某個項目時提前警告您。

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core dotnet 診斷通用工具

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-計數器](dotnet-counters.md)是效能監視工具，可進行第一層健全狀況監視和效能調查。 它會觀察透過 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。 例如，您可以快速監視 CPU 使用率，或 .NET Core 應用程式中擲回的例外狀況率等事項。

### <a name="dotnet-dump"></a>dotnet-dump

[Dotnet](dotnet-dump.md)傾印工具是在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印的方式。

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core 包含 `EventPipe` 要在其中公開診斷資料的呼叫。 [Dotnet 追蹤](dotnet-trace.md)工具可讓您從應用程式取用有趣的分析資料，以在需要執行速度緩慢的根本原因應用程式時提供協助。

## <a name="net-core-diagnostics-tutorials"></a>.NET Core 診斷教學課程

### <a name="debug-a-memory-leak"></a>針對記憶體流失進行偵錯

[教學課程：偵測記憶體](debug-memory-leak.md)流失會逐步解說找出記憶體流失的情況。 [Dotnet 計數器](dotnet-counters.md)工具是用來確認流失，而[dotnet](dotnet-dump.md)傾印工具是用來診斷遺漏的問題。

### <a name="debug-high-cpu-usage"></a>高 CPU 使用率的調試

[教學課程：高 cpu 使用量](debug-highcpu.md)的檢查會逐步引導您調查高 cpu 使用量。 它會使用[dotnet 計數器](dotnet-counters.md)工具來確認高 CPU 使用量。 接著，它會逐步引導您使用[效能分析公用程式（ `dotnet-trace` ）或 Linux 的追蹤](dotnet-trace.md) `perf` 來收集和查看 CPU 使用量設定檔。

### <a name="debug-deadlock"></a>Debug 鎖死

[教學課程： Debug 鎖死](debug-deadlock.md)會顯示如何使用[dotnet](dotnet-dump.md)傾印工具來調查執行緒和鎖定。
