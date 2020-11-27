---
title: CLR ETW 事件
description: 請參閱適用于 Windows (ETW) 事件之 common language runtime (CLR) 事件追蹤的相關文章。 有兩個事件提供者：執行時間提供者和取消提供者。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 8acc792b5217519e2a73c0cdf30c20161373c678
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283909"
---
# <a name="clr-etw-events"></a><span data-ttu-id="130ce-104">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="130ce-104">CLR ETW Events</span></span>

<span data-ttu-id="130ce-105">本節中的主題描述 Windows (ETW) 事件的事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="130ce-105">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="130ce-106">每個事件都有相關聯的關鍵字和層級，如 [CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="130ce-106">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="130ce-107">CLR 具有事件的兩個提供者：</span><span class="sxs-lookup"><span data-stu-id="130ce-107">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="130ce-108">執行階段提供者，以根據啟用哪些關鍵字 (事件的類別) 來引發事件。</span><span class="sxs-lookup"><span data-stu-id="130ce-108">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="130ce-109">CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="130ce-109">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="130ce-110">具有特殊用途的取消提供者。</span><span class="sxs-lookup"><span data-stu-id="130ce-110">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="130ce-111">CLR 取消提供者 GUID 是 a669021c-c450-4609-a035-5af59af4df18。</span><span class="sxs-lookup"><span data-stu-id="130ce-111">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="130ce-112">如需提供者的詳細資訊，請參閱 [CLR ETW 提供者](clr-etw-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="130ce-112">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="130ce-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="130ce-113">In This Section</span></span>  

 [<span data-ttu-id="130ce-114">執行階段資訊事件</span><span class="sxs-lookup"><span data-stu-id="130ce-114">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="130ce-115">擷取執行階段的相關資訊，包含 SKU、版本號碼、執行階段啟用方式、用來啟動它的命令列參數、GUID (適用時)，以及其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-115">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="130ce-116">Exception Thrown_V1 事件</span><span class="sxs-lookup"><span data-stu-id="130ce-116">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="130ce-117">擷取所擲回例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-117">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="130ce-118">爭用事件</span><span class="sxs-lookup"><span data-stu-id="130ce-118">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="130ce-119">擷取爭用執行階段所使用之監視鎖定或原生鎖定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-119">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="130ce-120">執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="130ce-120">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="130ce-121">擷取背景工作執行緒集區和 I/O 執行緒集區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-121">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="130ce-122">載入器事件</span><span class="sxs-lookup"><span data-stu-id="130ce-122">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="130ce-123">擷取載入和卸載應用程式定義域、組件和模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-123">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="130ce-124">方法事件</span><span class="sxs-lookup"><span data-stu-id="130ce-124">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="130ce-125">擷取進行符號解析之 CLR 方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-125">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="130ce-126">記憶體回收事件</span><span class="sxs-lookup"><span data-stu-id="130ce-126">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="130ce-127">擷取記憶體回收的相關資訊，以協助診斷和偵錯。</span><span class="sxs-lookup"><span data-stu-id="130ce-127">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="130ce-128">JIT 追蹤事件</span><span class="sxs-lookup"><span data-stu-id="130ce-128">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="130ce-129">擷取 Just-In-Time (JIT) 內嵌和 tail 呼叫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-129">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="130ce-130">Interop 事件</span><span class="sxs-lookup"><span data-stu-id="130ce-130">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="130ce-131">擷取 Microsoft Intermediate Language (MSIL) Stub 產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-131">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="130ce-132">ARM 事件</span><span class="sxs-lookup"><span data-stu-id="130ce-132">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="130ce-133">擷取應用程式定義域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-133">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="130ce-134">安全性事件</span><span class="sxs-lookup"><span data-stu-id="130ce-134">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="130ce-135">擷取強式名稱和 Authenticode 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-135">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="130ce-136">堆疊事件</span><span class="sxs-lookup"><span data-stu-id="130ce-136">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="130ce-137">擷取與其他事件搭配使用以在引發事件之後產生堆疊追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="130ce-137">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130ce-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130ce-138">See also</span></span>

- [<span data-ttu-id="130ce-139">使用 ETW 改善偵錯和效能調整</span><span class="sxs-lookup"><span data-stu-id="130ce-139">Improve Debugging And Performance Tuning With ETW</span></span>](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="130ce-140">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="130ce-140">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="130ce-141">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="130ce-141">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="130ce-142">CLR ETW 關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="130ce-142">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="130ce-143">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="130ce-143">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
