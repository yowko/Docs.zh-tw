---
title: .NET 中的工具和診斷
author: IEvangelist
description: 瞭解 .NET 開發人員可用的開發和診斷工具。
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "96586565"
---
# <a name="tools-and-diagnostics-in-net"></a>.NET 中的工具和診斷

在本文中，您將瞭解 .NET 開發人員可用的各種工具。 使用 .NET，您有一個健全的軟體發展工具組 (SDK) ，其中包含 (CLI) 的命令列介面。 .NET CLI 可在整個中啟用許多功能。 (Ide) 的網路就緒整合式開發環境。 本文也提供生產力功能的資源，例如診斷效能問題的 .NET CLI 工具、記憶體流失、高 CPU、鎖死，以及程式碼分析的工具支援。

## <a name="net-sdk"></a>.NET SDK

.NET SDK 包含 .NET 執行時間和 .NET CLI。 您可以下載適用于 Windows、Linux、macOS 或 Docker 的 [.NET SDK](https://dotnet.microsoft.com/download) 。 如需詳細資訊，請參閱 [.NET SDK 總覽](../core/sdk.md)。

## <a name="net-cli"></a>.NET CLI

.NET CLI 是一種跨平臺的工具鏈，可用於開發、建立、執行和發佈 .NET 應用程式。 .Net CLI 隨附于 .NET SDK。 如需詳細資訊，請參閱 [.NET CLI 總覽](../core/tools/index.md)。

## <a name="ides"></a>IDE

您可以在 [Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)或 [Visual Studio for Mac](/visualstudio/mac)中撰寫 .net 應用程式。 如需雲端支援的開發環境的詳細資訊，請參閱 [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)。

## <a name="additional-tools"></a>其他工具

除了更常見的工具之外，.NET 也提供適用于特定案例的工具。 某些使用案例包括卸載 .NET SDK 或 .NET 執行時間、 (WCF) 中繼資料的 Windows Communication Foundation 抓取、產生 proxy 原始程式碼，以及序列化 XML。 如需詳細資訊，請參閱 [.net 其他工具總覽](../core/additional-tools/index.md)。

## <a name="diagnostics-and-instrumentation"></a>診斷和檢測

作為 .NET 開發人員，您可以使用常見的效能診斷工具來監視應用程式效能、使用追蹤來分析應用程式、收集效能計量，以及分析傾印檔案。 您可以使用事件計數器收集效能計量，並使用程式碼剖析工具來深入瞭解應用程式的執行方式。 如需詳細資訊，請參閱 [.net 診斷工具](../core/diagnostics/index.md)。

## <a name="code-analysis"></a>程式碼分析

.NET 編譯器平臺 (Roslyn) 分析器會檢查您的 c # 或 Visual Basic 程式碼，以瞭解程式碼品質和程式碼樣式問題。 如需詳細資訊，請參閱 [.net 原始程式碼分析總覽](code-analysis/overview.md)。
