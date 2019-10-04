---
title: 方法 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48e1c2271d6d011296d347e7d74fb363cc4d8527
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834557"
---
# <a name="method-etw-events"></a><span data-ttu-id="57aae-102">方法 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-102">Method ETW Events</span></span>

<a name="top"></a> <span data-ttu-id="57aae-103">這些事件會收集方法的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="57aae-103">These events collect information that is specific to methods.</span></span> <span data-ttu-id="57aae-104">若要進行符號解析，需使用這些事件的承載。</span><span class="sxs-lookup"><span data-stu-id="57aae-104">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="57aae-105">此外，這些事件會提供實用資訊，例如呼叫方法的次數。</span><span class="sxs-lookup"><span data-stu-id="57aae-105">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="57aae-106">所有方法事件都具「告知性 (4)」的層級。</span><span class="sxs-lookup"><span data-stu-id="57aae-106">All method events have a level of "Informational (4)".</span></span> <span data-ttu-id="57aae-107">所有方法的詳細資訊事件都具「詳細資訊 (5)」的層級。</span><span class="sxs-lookup"><span data-stu-id="57aae-107">All method verbose events have a level of "Verbose (5)".</span></span>

<span data-ttu-id="57aae-108">所有方法事件都是由執行階段提供者下的 `JITKeyword` (0x10) 關鍵字或 `NGenKeyword` (0x20) 關鍵字，或由取消提供者下的 `JitRundownKeyword` (0x10) 或 `NGENRundownKeyword` (0x20) 所引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-108">All method events are raised by the `JITKeyword` (0x10) keyword or the `NGenKeyword` (0x20) keyword under the runtime provider, or `JitRundownKeyword` (0x10) or `NGENRundownKeyword` (0x20) under the rundown provider.</span></span>

<span data-ttu-id="57aae-109">CLR 方法事件會進一步細分為下列：</span><span class="sxs-lookup"><span data-stu-id="57aae-109">CLR method events are further subdivided into the following:</span></span>

- [<span data-ttu-id="57aae-110">方法事件</span><span class="sxs-lookup"><span data-stu-id="57aae-110">CLR Method Events</span></span>](#clr_method_events)

- [<span data-ttu-id="57aae-111">CLR 方法標記事件</span><span class="sxs-lookup"><span data-stu-id="57aae-111">CLR Method Marker Events</span></span>](#clr_method_marker_events)

- [<span data-ttu-id="57aae-112">CLR 方法詳細資料事件</span><span class="sxs-lookup"><span data-stu-id="57aae-112">CLR Method Verbose Events</span></span>](#clr_method_verbose_events)

- [<span data-ttu-id="57aae-113">MethodJittingStarted 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-113">MethodJittingStarted Event</span></span>](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a><span data-ttu-id="57aae-114">方法事件</span><span class="sxs-lookup"><span data-stu-id="57aae-114">CLR Method Events</span></span>

<span data-ttu-id="57aae-115">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="57aae-115">The following table shows the keyword and level.</span></span> <span data-ttu-id="57aae-116">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="57aae-116">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="57aae-117">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="57aae-117">Keyword for raising the event</span></span>|<span data-ttu-id="57aae-118">層級</span><span class="sxs-lookup"><span data-stu-id="57aae-118">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="57aae-119">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-119">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="57aae-120">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-120">Informational (4)</span></span>|
|<span data-ttu-id="57aae-121">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-121">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="57aae-122">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-122">Informational (4)</span></span>|
|<span data-ttu-id="57aae-123">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-123">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="57aae-124">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-124">Informational (4)</span></span>|
|<span data-ttu-id="57aae-125">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-125">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="57aae-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-126">Informational (4)</span></span>|

<span data-ttu-id="57aae-127">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="57aae-127">The following table shows the event information:</span></span>

|<span data-ttu-id="57aae-128">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-128">Event</span></span>|<span data-ttu-id="57aae-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="57aae-129">Event ID</span></span>|<span data-ttu-id="57aae-130">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-130">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|<span data-ttu-id="57aae-131">136</span><span class="sxs-lookup"><span data-stu-id="57aae-131">136</span></span>|<span data-ttu-id="57aae-132">在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-132">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="57aae-133">動態和泛型的方法並不會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="57aae-133">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="57aae-134">JIT Helper 永遠不會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="57aae-134">JIT helpers never use this version.</span></span>|
|`MethodUnLoad_V1`|<span data-ttu-id="57aae-135">137</span><span class="sxs-lookup"><span data-stu-id="57aae-135">137</span></span>|<span data-ttu-id="57aae-136">在模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-136">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="57aae-137">動態方法永遠不會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="57aae-137">Dynamic methods never use this version for method unloads.</span></span>|
|`MethodDCStart_V1`|<span data-ttu-id="57aae-138">137</span><span class="sxs-lookup"><span data-stu-id="57aae-138">137</span></span>|<span data-ttu-id="57aae-139">於啟動取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-139">Enumerates methods during a start rundown.</span></span>|
|`MethodDCEnd_V1`|<span data-ttu-id="57aae-140">138</span><span class="sxs-lookup"><span data-stu-id="57aae-140">138</span></span>|<span data-ttu-id="57aae-141">於結束取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-141">Enumerates methods during an end rundown.</span></span>|

<span data-ttu-id="57aae-142">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="57aae-142">The following table shows the event data:</span></span>

|<span data-ttu-id="57aae-143">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="57aae-143">Field name</span></span>|<span data-ttu-id="57aae-144">資料類型</span><span class="sxs-lookup"><span data-stu-id="57aae-144">Data type</span></span>|<span data-ttu-id="57aae-145">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-145">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="57aae-146">MethodID</span><span class="sxs-lookup"><span data-stu-id="57aae-146">MethodID</span></span>|<span data-ttu-id="57aae-147">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-147">win:UInt64</span></span>|<span data-ttu-id="57aae-148">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="57aae-148">Unique identifier of a method.</span></span> <span data-ttu-id="57aae-149">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="57aae-149">For JIT helper methods, this is set to the start address of the method.</span></span>|
|<span data-ttu-id="57aae-150">ModuleID</span><span class="sxs-lookup"><span data-stu-id="57aae-150">ModuleID</span></span>|<span data-ttu-id="57aae-151">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-151">win:UInt64</span></span>|<span data-ttu-id="57aae-152">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="57aae-152">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|<span data-ttu-id="57aae-153">MethodStartAddress</span><span class="sxs-lookup"><span data-stu-id="57aae-153">MethodStartAddress</span></span>|<span data-ttu-id="57aae-154">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-154">win:UInt64</span></span>|<span data-ttu-id="57aae-155">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="57aae-155">Start address of the method.</span></span>|
|<span data-ttu-id="57aae-156">MethodSize</span><span class="sxs-lookup"><span data-stu-id="57aae-156">MethodSize</span></span>|<span data-ttu-id="57aae-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-157">win:UInt32</span></span>|<span data-ttu-id="57aae-158">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="57aae-158">Size of the method.</span></span>|
|<span data-ttu-id="57aae-159">MethodToken</span><span class="sxs-lookup"><span data-stu-id="57aae-159">MethodToken</span></span>|<span data-ttu-id="57aae-160">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-160">win:UInt32</span></span>|<span data-ttu-id="57aae-161">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="57aae-161">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="57aae-162">MethodFlags</span><span class="sxs-lookup"><span data-stu-id="57aae-162">MethodFlags</span></span>|<span data-ttu-id="57aae-163">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-163">win:UInt32</span></span>|<span data-ttu-id="57aae-164">0x1動態方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-164">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="57aae-165">0x2泛型方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-165">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="57aae-166">0x4JIT 編譯的程式碼方法（否則為 NGEN 原生映射程式碼）。</span><span class="sxs-lookup"><span data-stu-id="57aae-166">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="57aae-167">0x8Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-167">0x8: Helper method.</span></span>|
|<span data-ttu-id="57aae-168">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="57aae-168">ClrInstanceID</span></span>|<span data-ttu-id="57aae-169">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="57aae-169">win:UInt16</span></span>|<span data-ttu-id="57aae-170">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="57aae-170">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="57aae-171">回到頁首</span><span class="sxs-lookup"><span data-stu-id="57aae-171">Back to top</span></span>](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a><span data-ttu-id="57aae-172">CLR 方法標記事件</span><span class="sxs-lookup"><span data-stu-id="57aae-172">CLR Method Marker Events</span></span>

<span data-ttu-id="57aae-173">只有在取消提供者下會引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="57aae-173">These events are raised only under the rundown provider.</span></span> <span data-ttu-id="57aae-174">它們表示在啟動或結束取消期間的方法列舉結尾。</span><span class="sxs-lookup"><span data-stu-id="57aae-174">They signify the end of method enumeration during a start or end rundown.</span></span> <span data-ttu-id="57aae-175">(也就是說，啟用 `NGENRundownKeyword`、 `JitRundownKeyword`、 `LoaderRundownKeyword`、或 `AppDomainResourceManagementRundownKeyword` 關鍵字時會將其引發。)</span><span class="sxs-lookup"><span data-stu-id="57aae-175">(That is, they are raised when the `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, or `AppDomainResourceManagementRundownKeyword` keyword is enabled.)</span></span>

<span data-ttu-id="57aae-176">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="57aae-176">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="57aae-177">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="57aae-177">Keyword for raising the event</span></span>|<span data-ttu-id="57aae-178">層級</span><span class="sxs-lookup"><span data-stu-id="57aae-178">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="57aae-179">`AppDomainResourceManagementRundownKeyword` (0x800) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-179">`AppDomainResourceManagementRundownKeyword` (0x800) rundown provider</span></span>|<span data-ttu-id="57aae-180">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-180">Informational (4)</span></span>|
|<span data-ttu-id="57aae-181">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-181">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="57aae-182">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-182">Informational (4)</span></span>|
|<span data-ttu-id="57aae-183">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-183">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="57aae-184">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="57aae-184">Informational (4)</span></span>|

<span data-ttu-id="57aae-185">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="57aae-185">The following table shows the event information:</span></span>

|<span data-ttu-id="57aae-186">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-186">Event</span></span>|<span data-ttu-id="57aae-187">事件 ID</span><span class="sxs-lookup"><span data-stu-id="57aae-187">Event ID</span></span>|<span data-ttu-id="57aae-188">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-188">Description</span></span>|
|-----------|--------------|----------------|
|`DCStartInit_V1`|<span data-ttu-id="57aae-189">147</span><span class="sxs-lookup"><span data-stu-id="57aae-189">147</span></span>|<span data-ttu-id="57aae-190">在啟動取消期間、列舉開始之前傳送。</span><span class="sxs-lookup"><span data-stu-id="57aae-190">Sent before the start of the enumeration during a start rundown.</span></span>|
|`DCStartComplete_V1`|<span data-ttu-id="57aae-191">145</span><span class="sxs-lookup"><span data-stu-id="57aae-191">145</span></span>|<span data-ttu-id="57aae-192">在啟動取消期間、列舉結尾時傳送。</span><span class="sxs-lookup"><span data-stu-id="57aae-192">Sent at the end of the enumeration during a start rundown.</span></span>|
|`DCEndInit_V1`|<span data-ttu-id="57aae-193">148</span><span class="sxs-lookup"><span data-stu-id="57aae-193">148</span></span>|<span data-ttu-id="57aae-194">在結束取消期間、開始列舉之前傳送。</span><span class="sxs-lookup"><span data-stu-id="57aae-194">Sent before the start of the enumeration during an end rundown.</span></span>|
|`DCEndComplete_V1`|<span data-ttu-id="57aae-195">146</span><span class="sxs-lookup"><span data-stu-id="57aae-195">146</span></span>|<span data-ttu-id="57aae-196">在結束取消期間、列舉結尾時傳送。</span><span class="sxs-lookup"><span data-stu-id="57aae-196">Sent at the end of the enumeration during an end rundown.</span></span>|

<span data-ttu-id="57aae-197">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="57aae-197">The following table shows the event data:</span></span>

|<span data-ttu-id="57aae-198">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="57aae-198">Field name</span></span>|<span data-ttu-id="57aae-199">資料類型</span><span class="sxs-lookup"><span data-stu-id="57aae-199">Data type</span></span>|<span data-ttu-id="57aae-200">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-200">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="57aae-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="57aae-201">ClrInstanceID</span></span>|<span data-ttu-id="57aae-202">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="57aae-202">win:UInt16</span></span>|<span data-ttu-id="57aae-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="57aae-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="57aae-204">回到頁首</span><span class="sxs-lookup"><span data-stu-id="57aae-204">Back to top</span></span>](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a><span data-ttu-id="57aae-205">CLR 方法詳細資料事件</span><span class="sxs-lookup"><span data-stu-id="57aae-205">CLR Method Verbose Events</span></span>

<span data-ttu-id="57aae-206">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="57aae-206">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="57aae-207">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="57aae-207">Keyword for raising the event</span></span>|<span data-ttu-id="57aae-208">層級</span><span class="sxs-lookup"><span data-stu-id="57aae-208">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="57aae-209">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-209">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="57aae-210">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-210">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-211">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-211">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="57aae-212">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-212">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-213">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-213">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="57aae-214">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-214">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-215">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-215">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="57aae-216">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-216">Verbose (5)</span></span>|

<span data-ttu-id="57aae-217">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="57aae-217">The following table shows the event information:</span></span>

|<span data-ttu-id="57aae-218">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-218">Event</span></span>|<span data-ttu-id="57aae-219">事件 ID</span><span class="sxs-lookup"><span data-stu-id="57aae-219">Event ID</span></span>|<span data-ttu-id="57aae-220">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-220">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="57aae-221">143</span><span class="sxs-lookup"><span data-stu-id="57aae-221">143</span></span>|<span data-ttu-id="57aae-222">在 JIT 載入方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-222">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="57aae-223">動態和泛型的方法一律會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="57aae-223">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="57aae-224">JIT Helper 一律會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="57aae-224">JIT helpers always use this version.</span></span>|
|`MethodUnLoadVerbose_V1`|<span data-ttu-id="57aae-225">144</span><span class="sxs-lookup"><span data-stu-id="57aae-225">144</span></span>|<span data-ttu-id="57aae-226">在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-226">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="57aae-227">動態方法永遠一律會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="57aae-227">Dynamic methods always use this version for method unloads.</span></span>|
|`MethodDCStartVerbose_V1`|<span data-ttu-id="57aae-228">141</span><span class="sxs-lookup"><span data-stu-id="57aae-228">141</span></span>|<span data-ttu-id="57aae-229">於啟動取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-229">Enumerates methods during a start rundown.</span></span>|
|`MethodDCEndVerbose_V1`|<span data-ttu-id="57aae-230">142</span><span class="sxs-lookup"><span data-stu-id="57aae-230">142</span></span>|<span data-ttu-id="57aae-231">於結束取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-231">Enumerates methods during an end rundown.</span></span>|

<span data-ttu-id="57aae-232">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="57aae-232">The following table shows the event data:</span></span>

|<span data-ttu-id="57aae-233">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="57aae-233">Field name</span></span>|<span data-ttu-id="57aae-234">資料類型</span><span class="sxs-lookup"><span data-stu-id="57aae-234">Data type</span></span>|<span data-ttu-id="57aae-235">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-235">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="57aae-236">MethodID</span><span class="sxs-lookup"><span data-stu-id="57aae-236">MethodID</span></span>|<span data-ttu-id="57aae-237">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-237">win:UInt64</span></span>|<span data-ttu-id="57aae-238">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="57aae-238">Unique identifier of the method.</span></span> <span data-ttu-id="57aae-239">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="57aae-239">For JIT helper methods, set to the start address of the method.</span></span>|
|<span data-ttu-id="57aae-240">ModuleID</span><span class="sxs-lookup"><span data-stu-id="57aae-240">ModuleID</span></span>|<span data-ttu-id="57aae-241">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-241">win:UInt64</span></span>|<span data-ttu-id="57aae-242">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="57aae-242">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|<span data-ttu-id="57aae-243">MethodStartAddress</span><span class="sxs-lookup"><span data-stu-id="57aae-243">MethodStartAddress</span></span>|<span data-ttu-id="57aae-244">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-244">win:UInt64</span></span>|<span data-ttu-id="57aae-245">起始位址：</span><span class="sxs-lookup"><span data-stu-id="57aae-245">Start address.</span></span>|
|<span data-ttu-id="57aae-246">MethodSize</span><span class="sxs-lookup"><span data-stu-id="57aae-246">MethodSize</span></span>|<span data-ttu-id="57aae-247">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-247">win:UInt32</span></span>|<span data-ttu-id="57aae-248">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="57aae-248">Method length.</span></span>|
|<span data-ttu-id="57aae-249">MethodToken</span><span class="sxs-lookup"><span data-stu-id="57aae-249">MethodToken</span></span>|<span data-ttu-id="57aae-250">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-250">win:UInt32</span></span>|<span data-ttu-id="57aae-251">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="57aae-251">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="57aae-252">MethodFlags</span><span class="sxs-lookup"><span data-stu-id="57aae-252">MethodFlags</span></span>|<span data-ttu-id="57aae-253">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-253">win:UInt32</span></span>|<span data-ttu-id="57aae-254">0x1動態方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-254">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="57aae-255">0x2泛型方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-255">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="57aae-256">0x4JIT 編譯的方法（否則由 Ngen.exe 產生）</span><span class="sxs-lookup"><span data-stu-id="57aae-256">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="57aae-257">0x8Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="57aae-257">0x8: Helper method.</span></span>|
|<span data-ttu-id="57aae-258">MethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="57aae-258">MethodNameSpace</span></span>|<span data-ttu-id="57aae-259">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-259">win:UnicodeString</span></span>|<span data-ttu-id="57aae-260">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="57aae-260">Full namespace name associated with the method.</span></span>|
|<span data-ttu-id="57aae-261">MethodName</span><span class="sxs-lookup"><span data-stu-id="57aae-261">MethodName</span></span>|<span data-ttu-id="57aae-262">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-262">win:UnicodeString</span></span>|<span data-ttu-id="57aae-263">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="57aae-263">Full class name associated with the method.</span></span>|
|<span data-ttu-id="57aae-264">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="57aae-264">MethodSignature</span></span>|<span data-ttu-id="57aae-265">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-265">win:UnicodeString</span></span>|<span data-ttu-id="57aae-266">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="57aae-266">Signature of the method (comma-separated list of type names).</span></span>|
|<span data-ttu-id="57aae-267">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="57aae-267">ClrInstanceID</span></span>|<span data-ttu-id="57aae-268">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="57aae-268">win:UInt16</span></span>|<span data-ttu-id="57aae-269">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="57aae-269">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="57aae-270">回到頁首</span><span class="sxs-lookup"><span data-stu-id="57aae-270">Back to top</span></span>](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a><span data-ttu-id="57aae-271">MethodJittingStarted 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-271">MethodJittingStarted Event</span></span>

<span data-ttu-id="57aae-272">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="57aae-272">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="57aae-273">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="57aae-273">Keyword for raising the event</span></span>|<span data-ttu-id="57aae-274">層級</span><span class="sxs-lookup"><span data-stu-id="57aae-274">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="57aae-275">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-275">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="57aae-276">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-276">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-277">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-277">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="57aae-278">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-278">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-279">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-279">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="57aae-280">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-280">Verbose (5)</span></span>|
|<span data-ttu-id="57aae-281">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="57aae-281">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="57aae-282">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="57aae-282">Verbose (5)</span></span>|

<span data-ttu-id="57aae-283">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="57aae-283">The following table shows the event information:</span></span>

|<span data-ttu-id="57aae-284">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-284">Event</span></span>|<span data-ttu-id="57aae-285">事件 ID</span><span class="sxs-lookup"><span data-stu-id="57aae-285">Event ID</span></span>|<span data-ttu-id="57aae-286">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-286">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|<span data-ttu-id="57aae-287">145</span><span class="sxs-lookup"><span data-stu-id="57aae-287">145</span></span>|<span data-ttu-id="57aae-288">當某個方法正在進行 JIT 編譯時引發。</span><span class="sxs-lookup"><span data-stu-id="57aae-288">Raised when a method is being JIT-compiled.</span></span>|

<span data-ttu-id="57aae-289">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="57aae-289">The following table shows the event data:</span></span>

|<span data-ttu-id="57aae-290">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="57aae-290">Field name</span></span>|<span data-ttu-id="57aae-291">資料類型</span><span class="sxs-lookup"><span data-stu-id="57aae-291">Data type</span></span>|<span data-ttu-id="57aae-292">描述</span><span class="sxs-lookup"><span data-stu-id="57aae-292">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="57aae-293">MethodID</span><span class="sxs-lookup"><span data-stu-id="57aae-293">MethodID</span></span>|<span data-ttu-id="57aae-294">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-294">win:UInt64</span></span>|<span data-ttu-id="57aae-295">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="57aae-295">Unique identifier of the method.</span></span>|
|<span data-ttu-id="57aae-296">ModuleID</span><span class="sxs-lookup"><span data-stu-id="57aae-296">ModuleID</span></span>|<span data-ttu-id="57aae-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="57aae-297">win:UInt64</span></span>|<span data-ttu-id="57aae-298">這個方法所屬之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57aae-298">Identifier of the module to which this method belongs.</span></span>|
|<span data-ttu-id="57aae-299">MethodToken</span><span class="sxs-lookup"><span data-stu-id="57aae-299">MethodToken</span></span>|<span data-ttu-id="57aae-300">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-300">win:UInt32</span></span>|<span data-ttu-id="57aae-301">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="57aae-301">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="57aae-302">MethodILSize</span><span class="sxs-lookup"><span data-stu-id="57aae-302">MethodILSize</span></span>|<span data-ttu-id="57aae-303">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="57aae-303">win:UInt32</span></span>|<span data-ttu-id="57aae-304">正在進行 JIT 編譯之方法的 Microsoft Intermediate Language (MSIL) 大小。</span><span class="sxs-lookup"><span data-stu-id="57aae-304">The size of the Microsoft intermediate language (MSIL) for the method that is being JIT-compiled.</span></span>|
|<span data-ttu-id="57aae-305">MethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="57aae-305">MethodNameSpace</span></span>|<span data-ttu-id="57aae-306">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-306">win:UnicodeString</span></span>|<span data-ttu-id="57aae-307">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="57aae-307">Full class name associated with the method.</span></span>|
|<span data-ttu-id="57aae-308">MethodName</span><span class="sxs-lookup"><span data-stu-id="57aae-308">MethodName</span></span>|<span data-ttu-id="57aae-309">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-309">win:UnicodeString</span></span>|<span data-ttu-id="57aae-310">方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="57aae-310">Name of the method.</span></span>|
|<span data-ttu-id="57aae-311">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="57aae-311">MethodSignature</span></span>|<span data-ttu-id="57aae-312">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="57aae-312">win:UnicodeString</span></span>|<span data-ttu-id="57aae-313">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="57aae-313">Signature of the method (comma-separated list of type names).</span></span>|
|<span data-ttu-id="57aae-314">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="57aae-314">ClrInstanceID</span></span>|<span data-ttu-id="57aae-315">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="57aae-315">win:UInt16</span></span>|<span data-ttu-id="57aae-316">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="57aae-316">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="57aae-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57aae-317">See also</span></span>

- [<span data-ttu-id="57aae-318">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="57aae-318">CLR ETW Events</span></span>](clr-etw-events.md)
