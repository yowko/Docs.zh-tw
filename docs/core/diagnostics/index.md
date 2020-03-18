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
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="b756a-103">.NET Core 中有哪些診斷工具可供使用？</span><span class="sxs-lookup"><span data-stu-id="b756a-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="b756a-104">軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。</span><span class="sxs-lookup"><span data-stu-id="b756a-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="b756a-105">此文章會協助您找出所需的各種工具。</span><span class="sxs-lookup"><span data-stu-id="b756a-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="b756a-106">受控偵錯工具</span><span class="sxs-lookup"><span data-stu-id="b756a-106">Managed debuggers</span></span>

<span data-ttu-id="b756a-107">[託管調試器](managed-debuggers.md)允許您與程式進行交互。</span><span class="sxs-lookup"><span data-stu-id="b756a-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="b756a-108">暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。</span><span class="sxs-lookup"><span data-stu-id="b756a-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="b756a-109">偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。</span><span class="sxs-lookup"><span data-stu-id="b756a-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="b756a-110">記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="b756a-110">Logging and tracing</span></span>

<span data-ttu-id="b756a-111">[日誌記錄和跟蹤](logging-tracing.md)是相關的技術。</span><span class="sxs-lookup"><span data-stu-id="b756a-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="b756a-112">它們會參考檢測程式碼以建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b756a-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="b756a-113">那些檔案會記錄程式所執行之內容的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b756a-113">The files record the details of what a program does.</span></span> <span data-ttu-id="b756a-114">這些詳細資料可用來診斷最為複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="b756a-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="b756a-115">透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。</span><span class="sxs-lookup"><span data-stu-id="b756a-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="b756a-116">單元測試</span><span class="sxs-lookup"><span data-stu-id="b756a-116">Unit testing</span></span>

<span data-ttu-id="b756a-117">[單元測試](../testing/index.md)是持續集成和部署高品質軟體的關鍵組成部分。</span><span class="sxs-lookup"><span data-stu-id="b756a-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="b756a-118">單元測試的設計是要在您中斷某個項目時提前警告您。</span><span class="sxs-lookup"><span data-stu-id="b756a-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="b756a-119">.NET 核心點網診斷全域工具</span><span class="sxs-lookup"><span data-stu-id="b756a-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="b756a-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b756a-120">dotnet-counters</span></span>

<span data-ttu-id="b756a-121">[點網計數器](dotnet-counters.md)是一級運行狀況監控和性能調查的性能監控工具。</span><span class="sxs-lookup"><span data-stu-id="b756a-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="b756a-122">它觀察通過<xref:System.Diagnostics.Tracing.EventCounter>API 發佈的效能計數器值。</span><span class="sxs-lookup"><span data-stu-id="b756a-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="b756a-123">例如，您可以快速監視 CPU 使用率或 .NET Core 應用程式中引發異常的速率等內容。</span><span class="sxs-lookup"><span data-stu-id="b756a-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="b756a-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="b756a-124">dotnet-dump</span></span>

<span data-ttu-id="b756a-125">[dotnet 轉儲](dotnet-dump.md)工具是在沒有本機調試器的情況下收集和分析 Windows 和 Linux 核心轉儲的一種方式。</span><span class="sxs-lookup"><span data-stu-id="b756a-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="b756a-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="b756a-126">dotnet-trace</span></span>

<span data-ttu-id="b756a-127">.NET 核心包括公開`EventPipe`診斷資料的所謂內容。</span><span class="sxs-lookup"><span data-stu-id="b756a-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="b756a-128">[dotnet 跟蹤](dotnet-trace.md)工具允許您使用應用中有趣的分析資料，這些資料有助於在需要根植導致運行緩慢的應用的情況下。</span><span class="sxs-lookup"><span data-stu-id="b756a-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="b756a-129">.NET Core 診斷教學課程</span><span class="sxs-lookup"><span data-stu-id="b756a-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="b756a-130">針對記憶體流失進行偵錯</span><span class="sxs-lookup"><span data-stu-id="b756a-130">Debug a memory leak</span></span>

<span data-ttu-id="b756a-131">[教程：調試記憶體洩漏](debug-memory-leak.md)，通過查找記憶體洩漏。</span><span class="sxs-lookup"><span data-stu-id="b756a-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="b756a-132">[點網計數器](dotnet-counters.md)工具用於確認洩漏，並且[點網轉儲](dotnet-dump.md)工具用於診斷洩漏。</span><span class="sxs-lookup"><span data-stu-id="b756a-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
