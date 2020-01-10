---
title: CLR ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 3763e93ff3a14819f59102a01cf3285e85afd12d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716203"
---
# <a name="clr-etw-events"></a><span data-ttu-id="f6b30-102">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-102">CLR ETW Events</span></span>
<span data-ttu-id="f6b30-103">本節中的主題描述 Windows (ETW) 事件的事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="f6b30-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="f6b30-104">每個事件都有相關聯的關鍵字和層級，如 [CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="f6b30-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="f6b30-105">CLR 具有事件的兩個提供者：</span><span class="sxs-lookup"><span data-stu-id="f6b30-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="f6b30-106">執行階段提供者，以根據啟用哪些關鍵字 (事件的類別) 來引發事件。</span><span class="sxs-lookup"><span data-stu-id="f6b30-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="f6b30-107">CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="f6b30-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="f6b30-108">具有特殊用途的取消提供者。</span><span class="sxs-lookup"><span data-stu-id="f6b30-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="f6b30-109">CLR 取消提供者 GUID 是 a669021c-c450-4609-a035-5af59af4df18。</span><span class="sxs-lookup"><span data-stu-id="f6b30-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="f6b30-110">如需提供者的詳細資訊，請參閱 [CLR ETW 提供者](clr-etw-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b30-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6b30-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f6b30-111">In This Section</span></span>  
 [<span data-ttu-id="f6b30-112">執行階段資訊事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="f6b30-113">擷取執行階段的相關資訊，包含 SKU、版本號碼、執行階段啟用方式、用來啟動它的命令列參數、GUID (適用時)，以及其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="f6b30-114">Exception Thrown_V1 事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="f6b30-115">擷取所擲回例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="f6b30-116">爭用事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="f6b30-117">擷取爭用執行階段所使用之監視鎖定或原生鎖定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="f6b30-118">執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="f6b30-119">擷取背景工作執行緒集區和 I/O 執行緒集區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="f6b30-120">載入器事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="f6b30-121">擷取載入和卸載應用程式定義域、組件和模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="f6b30-122">方法事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="f6b30-123">擷取進行符號解析之 CLR 方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="f6b30-124">記憶體回收事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="f6b30-125">擷取記憶體回收的相關資訊，以協助診斷和偵錯。</span><span class="sxs-lookup"><span data-stu-id="f6b30-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="f6b30-126">JIT 追蹤事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="f6b30-127">擷取 Just-In-Time (JIT) 內嵌和 tail 呼叫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="f6b30-128">Interop 事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="f6b30-129">擷取 Microsoft Intermediate Language (MSIL) Stub 產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="f6b30-130">ARM 事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="f6b30-131">擷取應用程式定義域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="f6b30-132">安全性事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="f6b30-133">擷取強式名稱和 Authenticode 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="f6b30-134">堆疊事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="f6b30-135">擷取與其他事件搭配使用以在引發事件之後產生堆疊追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b30-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b30-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6b30-136">See also</span></span>

- [<span data-ttu-id="f6b30-137">使用 ETW 改善偵錯和效能調整</span><span class="sxs-lookup"><span data-stu-id="f6b30-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="f6b30-138">Windows 效能 Blog</span><span class="sxs-lookup"><span data-stu-id="f6b30-138">Windows Performance Blog</span></span>](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [<span data-ttu-id="f6b30-139">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="f6b30-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="f6b30-140">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="f6b30-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="f6b30-141">CLR ETW 關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="f6b30-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="f6b30-142">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f6b30-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
