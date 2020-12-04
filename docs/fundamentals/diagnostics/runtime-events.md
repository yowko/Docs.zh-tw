---
title: 運行時間事件
description: 檢查 .NET 執行時間發出的診斷事件， (可搭配 ETW、LTTng 或 EventPipe 使用的 CoreCLR) 。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586637"
---
# <a name="net-runtime-events"></a><span data-ttu-id="dc468-103">.NET 運行時間事件</span><span class="sxs-lookup"><span data-stu-id="dc468-103">.NET runtime events</span></span>

<span data-ttu-id="dc468-104">.NET 執行時間 (CoreCLR) 發出各種事件，可用來診斷 .NET 應用程式的問題，這些問題可透過各種機制（例如 `ETW` 、和）使用 `LTTng` `EventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="dc468-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="dc468-105">本檔是 .NET Core 執行時間所引發事件的參考。</span><span class="sxs-lookup"><span data-stu-id="dc468-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="dc468-106">針對 .NET Framework 中的運行時間事件，請參閱 [CLR ETW 事件](../../framework/performance/clr-etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="dc468-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dc468-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="dc468-107">In this section</span></span>

<span data-ttu-id="dc468-108">[爭用事件](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="dc468-109">這些事件會收集監視器鎖定爭用的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="dc468-110">[垃圾收集事件](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="dc468-111">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="dc468-112">它們有助於診斷和偵測，包括決定執行垃圾收集的次數、在垃圾收集期間釋放多少記憶體等等。</span><span class="sxs-lookup"><span data-stu-id="dc468-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="dc468-113">[例外狀況事件](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="dc468-114">這些運行時間事件會捕捉擲回之例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="dc468-115">[Interop 事件](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="dc468-116">這些運行時間事件會捕獲一般中繼語言 (CIL) 存根產生的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="dc468-117">[載入器和系結器事件](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="dc468-118">這些事件會收集載入和卸載元件和模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="dc468-119">[方法事件](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="dc468-120">這些事件會收集方法的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="dc468-121">若要進行符號解析，需使用這些事件的承載。</span><span class="sxs-lookup"><span data-stu-id="dc468-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="dc468-122">此外，這些事件會提供實用資訊，例如呼叫方法的次數。</span><span class="sxs-lookup"><span data-stu-id="dc468-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="dc468-123">[執行緒事件](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="dc468-124">這些事件會收集背景工作和 I/O 執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="dc468-125">[類型事件](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="dc468-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="dc468-126">這些事件會收集有關型別系統的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc468-126">These events collect information about the type system.</span></span>
