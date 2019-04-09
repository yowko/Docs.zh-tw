---
title: CLR ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135859"
---
# <a name="clr-etw-events"></a><span data-ttu-id="7792b-102">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7792b-102">CLR ETW Events</span></span>
<span data-ttu-id="7792b-103">本節中的主題描述 Windows (ETW) 事件的事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="7792b-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="7792b-104">每個事件都有相關聯的關鍵字和層級，如 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="7792b-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="7792b-105">CLR 具有事件的兩個提供者：</span><span class="sxs-lookup"><span data-stu-id="7792b-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="7792b-106">執行階段提供者，以根據啟用哪些關鍵字 (事件的類別) 來引發事件。</span><span class="sxs-lookup"><span data-stu-id="7792b-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="7792b-107">CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="7792b-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="7792b-108">具有特殊用途的取消提供者。</span><span class="sxs-lookup"><span data-stu-id="7792b-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="7792b-109">CLR 取消提供者 GUID 是 a669021c-c450-4609-a035-5af59af4df18。</span><span class="sxs-lookup"><span data-stu-id="7792b-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="7792b-110">如需提供者的詳細資訊，請參閱 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="7792b-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7792b-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="7792b-111">In This Section</span></span>  
 [<span data-ttu-id="7792b-112">執行階段資訊事件</span><span class="sxs-lookup"><span data-stu-id="7792b-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="7792b-113">擷取執行階段的相關資訊，包含 SKU、版本號碼、執行階段啟用方式、用來啟動它的命令列參數、GUID (適用時)，以及其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="7792b-114">Exception Thrown_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7792b-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="7792b-115">擷取所擲回例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="7792b-116">爭用事件</span><span class="sxs-lookup"><span data-stu-id="7792b-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="7792b-117">擷取爭用執行階段所使用之監視鎖定或原生鎖定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="7792b-118">執行緒集區事件</span><span class="sxs-lookup"><span data-stu-id="7792b-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="7792b-119">擷取背景工作執行緒集區和 I/O 執行緒集區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="7792b-120">載入器事件</span><span class="sxs-lookup"><span data-stu-id="7792b-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="7792b-121">擷取載入和卸載應用程式定義域、組件和模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="7792b-122">方法事件</span><span class="sxs-lookup"><span data-stu-id="7792b-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="7792b-123">擷取進行符號解析之 CLR 方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="7792b-124">記憶體回收事件</span><span class="sxs-lookup"><span data-stu-id="7792b-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="7792b-125">擷取記憶體回收的相關資訊，以協助診斷和偵錯。</span><span class="sxs-lookup"><span data-stu-id="7792b-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="7792b-126">JIT 追蹤事件</span><span class="sxs-lookup"><span data-stu-id="7792b-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="7792b-127">擷取 Just-In-Time (JIT) 內嵌和 tail 呼叫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="7792b-128">Interop 事件</span><span class="sxs-lookup"><span data-stu-id="7792b-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="7792b-129">擷取 Microsoft Intermediate Language (MSIL) Stub 產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="7792b-130">ARM 事件</span><span class="sxs-lookup"><span data-stu-id="7792b-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="7792b-131">擷取應用程式定義域狀態的詳細診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="7792b-132">安全性事件</span><span class="sxs-lookup"><span data-stu-id="7792b-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="7792b-133">擷取強式名稱和 Authenticode 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="7792b-134">堆疊事件</span><span class="sxs-lookup"><span data-stu-id="7792b-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="7792b-135">擷取與其他事件搭配使用以在引發事件之後產生堆疊追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="7792b-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7792b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7792b-136">See also</span></span>

- [<span data-ttu-id="7792b-137">改善偵錯和效能調整使用 ETW</span><span class="sxs-lookup"><span data-stu-id="7792b-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)
- [<span data-ttu-id="7792b-138">Windows 效能部落格</span><span class="sxs-lookup"><span data-stu-id="7792b-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)
- [<span data-ttu-id="7792b-139">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="7792b-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)
- [<span data-ttu-id="7792b-140">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="7792b-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)
- [<span data-ttu-id="7792b-141">CLR ETW 關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="7792b-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="7792b-142">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7792b-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
