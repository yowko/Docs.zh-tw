---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974146"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="e4413-103">.NET Core 中有哪些診斷工具可供使用？</span><span class="sxs-lookup"><span data-stu-id="e4413-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="e4413-104">軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。</span><span class="sxs-lookup"><span data-stu-id="e4413-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="e4413-105">此文章會協助您找出所需的各種工具。</span><span class="sxs-lookup"><span data-stu-id="e4413-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="e4413-106">受控偵錯工具</span><span class="sxs-lookup"><span data-stu-id="e4413-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="e4413-107">受控偵錯工具可讓您與您的程式互動。</span><span class="sxs-lookup"><span data-stu-id="e4413-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="e4413-108">暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。</span><span class="sxs-lookup"><span data-stu-id="e4413-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="e4413-109">偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。</span><span class="sxs-lookup"><span data-stu-id="e4413-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="e4413-110">記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="e4413-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="e4413-111">記錄和追蹤是相關聯的技術。</span><span class="sxs-lookup"><span data-stu-id="e4413-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="e4413-112">它們會參考檢測程式碼以建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e4413-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="e4413-113">那些檔案會記錄程式所執行之內容的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e4413-113">The files record the details of what a program does.</span></span> <span data-ttu-id="e4413-114">這些詳細資料可用來診斷最為複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="e4413-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="e4413-115">透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。</span><span class="sxs-lookup"><span data-stu-id="e4413-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="e4413-116">單元測試</span><span class="sxs-lookup"><span data-stu-id="e4413-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="e4413-117">單元測試是持續整合和部署高品質軟體的重要元件。</span><span class="sxs-lookup"><span data-stu-id="e4413-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="e4413-118">單元測試的設計是要在您中斷某個項目時提前警告您。</span><span class="sxs-lookup"><span data-stu-id="e4413-118">Unit tests are designed to give you an early warning when you break something.</span></span>
