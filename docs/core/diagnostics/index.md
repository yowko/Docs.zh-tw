---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399046"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 中有哪些診斷工具可供使用？

軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。

此文章會協助您找出所需的各種工具。

## <a name="managed-debuggers"></a>受控偵錯工具

[託管調試器](managed-debuggers.md)允許您與程式進行交互。 暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。 偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。

## <a name="logging-and-tracing"></a>記錄和追蹤

[日誌記錄和跟蹤](logging-tracing.md)是相關的技術。 它們會參考檢測程式碼以建立記錄檔。 那些檔案會記錄程式所執行之內容的詳細資料。 這些詳細資料可用來診斷最為複雜的問題。 透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。

## <a name="unit-testing"></a>單元測試

[單元測試](../testing/index.md)是持續集成和部署高品質軟體的關鍵組成部分。 單元測試的設計是要在您中斷某個項目時提前警告您。

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET 核心點網診斷全域工具

### <a name="dotnet-counters"></a>dotnet-counters

[點網計數器](dotnet-counters.md)是一級運行狀況監控和性能調查的性能監控工具。 它觀察通過<xref:System.Diagnostics.Tracing.EventCounter>API 發佈的效能計數器值。 例如，您可以快速監視 CPU 使用率或 .NET Core 應用程式中引發異常的速率等內容。

### <a name="dotnet-dump"></a>dotnet-dump

[dotnet 轉儲](dotnet-dump.md)工具是在沒有本機調試器的情況下收集和分析 Windows 和 Linux 核心轉儲的一種方式。

### <a name="dotnet-trace"></a>dotnet-trace

.NET 核心包括公開`EventPipe`診斷資料的所謂內容。 [dotnet 跟蹤](dotnet-trace.md)工具允許您使用應用中有趣的分析資料，這些資料有助於在需要根植導致運行緩慢的應用的情況下。

## <a name="net-core-diagnostics-tutorials"></a>.NET Core 診斷教學課程

### <a name="debug-a-memory-leak"></a>針對記憶體流失進行偵錯

[教程：調試記憶體洩漏](debug-memory-leak.md)，通過查找記憶體洩漏。 [點網計數器](dotnet-counters.md)工具用於確認洩漏，並且[點網轉儲](dotnet-dump.md)工具用於診斷洩漏。
