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
# <a name="tools-and-diagnostics-in-net"></a><span data-ttu-id="269d0-103">.NET 中的工具和診斷</span><span class="sxs-lookup"><span data-stu-id="269d0-103">Tools and diagnostics in .NET</span></span>

<span data-ttu-id="269d0-104">在本文中，您將瞭解 .NET 開發人員可用的各種工具。</span><span class="sxs-lookup"><span data-stu-id="269d0-104">In this article, you'll learn about the various tools available to .NET developers.</span></span> <span data-ttu-id="269d0-105">使用 .NET，您有一個健全的軟體發展工具組 (SDK) ，其中包含 (CLI) 的命令列介面。</span><span class="sxs-lookup"><span data-stu-id="269d0-105">With .NET, you have a robust software development kit (SDK) that includes a command-line interface (CLI).</span></span> <span data-ttu-id="269d0-106">.NET CLI 可在整個中啟用許多功能。 (Ide) 的網路就緒整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="269d0-106">The .NET CLI enables many of the features throughout the .NET-ready integrated development environments (IDEs).</span></span> <span data-ttu-id="269d0-107">本文也提供生產力功能的資源，例如診斷效能問題的 .NET CLI 工具、記憶體流失、高 CPU、鎖死，以及程式碼分析的工具支援。</span><span class="sxs-lookup"><span data-stu-id="269d0-107">This article also provides resources to productivity capabilities, such as .NET CLI tools for diagnosing performance issues, memory leaks, high CPU, deadlocks, and tooling support for code analysis.</span></span>

## <a name="net-sdk"></a><span data-ttu-id="269d0-108">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="269d0-108">.NET SDK</span></span>

<span data-ttu-id="269d0-109">.NET SDK 包含 .NET 執行時間和 .NET CLI。</span><span class="sxs-lookup"><span data-stu-id="269d0-109">The .NET SDK includes both the .NET Runtime and the .NET CLI.</span></span> <span data-ttu-id="269d0-110">您可以下載適用于 Windows、Linux、macOS 或 Docker 的 [.NET SDK](https://dotnet.microsoft.com/download) 。</span><span class="sxs-lookup"><span data-stu-id="269d0-110">You can download the [.NET SDK](https://dotnet.microsoft.com/download) for Windows, Linux, macOS, or Docker.</span></span> <span data-ttu-id="269d0-111">如需詳細資訊，請參閱 [.NET SDK 總覽](../core/sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="269d0-111">For more information, see [.NET SDK overview](../core/sdk.md).</span></span>

## <a name="net-cli"></a><span data-ttu-id="269d0-112">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="269d0-112">.NET CLI</span></span>

<span data-ttu-id="269d0-113">.NET CLI 是一種跨平臺的工具鏈，可用於開發、建立、執行和發佈 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="269d0-113">The .NET CLI is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span> <span data-ttu-id="269d0-114">.Net CLI 隨附于 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="269d0-114">The .NET CLI is included with the .NET SDK.</span></span> <span data-ttu-id="269d0-115">如需詳細資訊，請參閱 [.NET CLI 總覽](../core/tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="269d0-115">For more information, see [.NET CLI overview](../core/tools/index.md).</span></span>

## <a name="ides"></a><span data-ttu-id="269d0-116">IDE</span><span class="sxs-lookup"><span data-stu-id="269d0-116">IDEs</span></span>

<span data-ttu-id="269d0-117">您可以在 [Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)或 [Visual Studio for Mac](/visualstudio/mac)中撰寫 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="269d0-117">You can write .NET applications in [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows), or [Visual Studio for Mac](/visualstudio/mac).</span></span> <span data-ttu-id="269d0-118">如需雲端支援的開發環境的詳細資訊，請參閱 [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)。</span><span class="sxs-lookup"><span data-stu-id="269d0-118">For information on cloud-powered development environments, see [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline).</span></span>

## <a name="additional-tools"></a><span data-ttu-id="269d0-119">其他工具</span><span class="sxs-lookup"><span data-stu-id="269d0-119">Additional tools</span></span>

<span data-ttu-id="269d0-120">除了更常見的工具之外，.NET 也提供適用于特定案例的工具。</span><span class="sxs-lookup"><span data-stu-id="269d0-120">In addition to the more common tools, .NET also provides tools for specific scenarios.</span></span> <span data-ttu-id="269d0-121">某些使用案例包括卸載 .NET SDK 或 .NET 執行時間、 (WCF) 中繼資料的 Windows Communication Foundation 抓取、產生 proxy 原始程式碼，以及序列化 XML。</span><span class="sxs-lookup"><span data-stu-id="269d0-121">Some of the use cases include uninstalling the .NET SDK or the .NET Runtime, retrieving Windows Communication Foundation (WCF) metadata, generating proxy source code, and serializing XML.</span></span> <span data-ttu-id="269d0-122">如需詳細資訊，請參閱 [.net 其他工具總覽](../core/additional-tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="269d0-122">For more information, see [.NET additional tools overview](../core/additional-tools/index.md).</span></span>

## <a name="diagnostics-and-instrumentation"></a><span data-ttu-id="269d0-123">診斷和檢測</span><span class="sxs-lookup"><span data-stu-id="269d0-123">Diagnostics and instrumentation</span></span>

<span data-ttu-id="269d0-124">作為 .NET 開發人員，您可以使用常見的效能診斷工具來監視應用程式效能、使用追蹤來分析應用程式、收集效能計量，以及分析傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="269d0-124">As a .NET developer, you can make use of common performance diagnostic tools to monitor app performance, profile apps with tracing, collect performance metrics, and analyze dump files.</span></span> <span data-ttu-id="269d0-125">您可以使用事件計數器收集效能計量，並使用程式碼剖析工具來深入瞭解應用程式的執行方式。</span><span class="sxs-lookup"><span data-stu-id="269d0-125">You collect performance metrics with event counters, and use profiling tools to gain insights into how apps perform.</span></span> <span data-ttu-id="269d0-126">如需詳細資訊，請參閱 [.net 診斷工具](../core/diagnostics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="269d0-126">For more information, see [.NET diagnostics tools](../core/diagnostics/index.md).</span></span>

## <a name="code-analysis"></a><span data-ttu-id="269d0-127">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="269d0-127">Code analysis</span></span>

<span data-ttu-id="269d0-128">.NET 編譯器平臺 (Roslyn) 分析器會檢查您的 c # 或 Visual Basic 程式碼，以瞭解程式碼品質和程式碼樣式問題。</span><span class="sxs-lookup"><span data-stu-id="269d0-128">The .NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="269d0-129">如需詳細資訊，請參閱 [.net 原始程式碼分析總覽](code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="269d0-129">For more information, see [.NET source code analysis overview](code-analysis/overview.md).</span></span>
