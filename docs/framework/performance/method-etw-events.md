---
title: 方法 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58249a0e080e045223bdaf170f2eaedb67fc0dea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046379"
---
# <a name="method-etw-events"></a><span data-ttu-id="59a11-102">方法 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-102">Method ETW Events</span></span>

<a name="top"></a> <span data-ttu-id="59a11-103">這些事件會收集方法的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="59a11-103">These events collect information that is specific to methods.</span></span> <span data-ttu-id="59a11-104">若要進行符號解析，需使用這些事件的承載。</span><span class="sxs-lookup"><span data-stu-id="59a11-104">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="59a11-105">此外，這些事件會提供實用資訊，例如呼叫方法的次數。</span><span class="sxs-lookup"><span data-stu-id="59a11-105">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="59a11-106">所有方法事件都具「告知性 (4)」的層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-106">All method events have a level of "Informational (4)".</span></span> <span data-ttu-id="59a11-107">所有方法的詳細資訊事件都具「詳細資訊 (5)」的層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-107">All method verbose events have a level of "Verbose (5)".</span></span>

<span data-ttu-id="59a11-108">所有方法事件都是由執行階段提供者下的 `JITKeyword` (0x10) 關鍵字或 `NGenKeyword` (0x20) 關鍵字，或由取消提供者下的 `JitRundownKeyword` (0x10) 或 `NGENRundownKeyword` (0x20) 所引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-108">All method events are raised by the `JITKeyword` (0x10) keyword or the `NGenKeyword` (0x20) keyword under the runtime provider, or `JitRundownKeyword` (0x10) or `NGENRundownKeyword` (0x20) under the rundown provider.</span></span>

<span data-ttu-id="59a11-109">CLR 方法事件會進一步細分為下列：</span><span class="sxs-lookup"><span data-stu-id="59a11-109">CLR method events are further subdivided into the following:</span></span>

- [<span data-ttu-id="59a11-110">方法事件</span><span class="sxs-lookup"><span data-stu-id="59a11-110">CLR Method Events</span></span>](#clr_method_events)

- [<span data-ttu-id="59a11-111">CLR 方法標記事件</span><span class="sxs-lookup"><span data-stu-id="59a11-111">CLR Method Marker Events</span></span>](#clr_method_marker_events)

- [<span data-ttu-id="59a11-112">CLR 方法詳細資料事件</span><span class="sxs-lookup"><span data-stu-id="59a11-112">CLR Method Verbose Events</span></span>](#clr_method_verbose_events)

- [<span data-ttu-id="59a11-113">MethodJittingStarted 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-113">MethodJittingStarted Event</span></span>](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a><span data-ttu-id="59a11-114">方法事件</span><span class="sxs-lookup"><span data-stu-id="59a11-114">CLR Method Events</span></span>

<span data-ttu-id="59a11-115">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-115">The following table shows the keyword and level.</span></span> <span data-ttu-id="59a11-116">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="59a11-116">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>

|<span data-ttu-id="59a11-117">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="59a11-117">Keyword for raising the event</span></span>|<span data-ttu-id="59a11-118">層級</span><span class="sxs-lookup"><span data-stu-id="59a11-118">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="59a11-119">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-119">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="59a11-120">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-120">Informational (4)</span></span>|
|<span data-ttu-id="59a11-121">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-121">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="59a11-122">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-122">Informational (4)</span></span>|
|<span data-ttu-id="59a11-123">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-123">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="59a11-124">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-124">Informational (4)</span></span>|
|<span data-ttu-id="59a11-125">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-125">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="59a11-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-126">Informational (4)</span></span>|

<span data-ttu-id="59a11-127">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="59a11-127">The following table shows the event information.</span></span>

|<span data-ttu-id="59a11-128">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-128">Event</span></span>|<span data-ttu-id="59a11-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="59a11-129">Event ID</span></span>|<span data-ttu-id="59a11-130">說明</span><span class="sxs-lookup"><span data-stu-id="59a11-130">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|<span data-ttu-id="59a11-131">136</span><span class="sxs-lookup"><span data-stu-id="59a11-131">136</span></span>|<span data-ttu-id="59a11-132">在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-132">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="59a11-133">動態和泛型的方法並不會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="59a11-133">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="59a11-134">JIT Helper 永遠不會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="59a11-134">JIT helpers never use this version.</span></span>|
|`MethodUnLoad_V1`|<span data-ttu-id="59a11-135">137</span><span class="sxs-lookup"><span data-stu-id="59a11-135">137</span></span>|<span data-ttu-id="59a11-136">在模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-136">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="59a11-137">動態方法永遠不會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="59a11-137">Dynamic methods never use this version for method unloads.</span></span>|
|`MethodDCStart_V1`|<span data-ttu-id="59a11-138">137</span><span class="sxs-lookup"><span data-stu-id="59a11-138">137</span></span>|<span data-ttu-id="59a11-139">於啟動取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-139">Enumerates methods during a start rundown.</span></span>|
|`MethodDCEnd_V1`|<span data-ttu-id="59a11-140">138</span><span class="sxs-lookup"><span data-stu-id="59a11-140">138</span></span>|<span data-ttu-id="59a11-141">於結束取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-141">Enumerates methods during an end rundown.</span></span>|

<span data-ttu-id="59a11-142">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="59a11-142">The following table shows the event data.</span></span>

|<span data-ttu-id="59a11-143">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="59a11-143">Field name</span></span>|<span data-ttu-id="59a11-144">資料類型</span><span class="sxs-lookup"><span data-stu-id="59a11-144">Data type</span></span>|<span data-ttu-id="59a11-145">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-145">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="59a11-146">MethodID</span><span class="sxs-lookup"><span data-stu-id="59a11-146">MethodID</span></span>|<span data-ttu-id="59a11-147">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-147">win:UInt64</span></span>|<span data-ttu-id="59a11-148">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="59a11-148">Unique identifier of a method.</span></span> <span data-ttu-id="59a11-149">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="59a11-149">For JIT helper methods, this is set to the start address of the method.</span></span>|
|<span data-ttu-id="59a11-150">ModuleID</span><span class="sxs-lookup"><span data-stu-id="59a11-150">ModuleID</span></span>|<span data-ttu-id="59a11-151">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-151">win:UInt64</span></span>|<span data-ttu-id="59a11-152">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="59a11-152">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|<span data-ttu-id="59a11-153">MethodStartAddress</span><span class="sxs-lookup"><span data-stu-id="59a11-153">MethodStartAddress</span></span>|<span data-ttu-id="59a11-154">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-154">win:UInt64</span></span>|<span data-ttu-id="59a11-155">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="59a11-155">Start address of the method.</span></span>|
|<span data-ttu-id="59a11-156">MethodSize</span><span class="sxs-lookup"><span data-stu-id="59a11-156">MethodSize</span></span>|<span data-ttu-id="59a11-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-157">win:UInt32</span></span>|<span data-ttu-id="59a11-158">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="59a11-158">Size of the method.</span></span>|
|<span data-ttu-id="59a11-159">MethodToken</span><span class="sxs-lookup"><span data-stu-id="59a11-159">MethodToken</span></span>|<span data-ttu-id="59a11-160">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-160">win:UInt32</span></span>|<span data-ttu-id="59a11-161">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="59a11-161">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="59a11-162">MethodFlags</span><span class="sxs-lookup"><span data-stu-id="59a11-162">MethodFlags</span></span>|<span data-ttu-id="59a11-163">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-163">win:UInt32</span></span>|<span data-ttu-id="59a11-164">0x1動態方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-164">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="59a11-165">0x2泛型方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-165">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="59a11-166">0x4JIT 編譯的程式碼方法（否則為 NGEN 原生映射程式碼）。</span><span class="sxs-lookup"><span data-stu-id="59a11-166">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="59a11-167">0x8Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-167">0x8: Helper method.</span></span>|
|<span data-ttu-id="59a11-168">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="59a11-168">ClrInstanceID</span></span>|<span data-ttu-id="59a11-169">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="59a11-169">win:UInt16</span></span>|<span data-ttu-id="59a11-170">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="59a11-170">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="59a11-171">回到頁首</span><span class="sxs-lookup"><span data-stu-id="59a11-171">Back to top</span></span>](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a><span data-ttu-id="59a11-172">CLR 方法標記事件</span><span class="sxs-lookup"><span data-stu-id="59a11-172">CLR Method Marker Events</span></span>

<span data-ttu-id="59a11-173">只有在取消提供者下會引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="59a11-173">These events are raised only under the rundown provider.</span></span> <span data-ttu-id="59a11-174">它們表示在啟動或結束取消期間的方法列舉結尾。</span><span class="sxs-lookup"><span data-stu-id="59a11-174">They signify the end of method enumeration during a start or end rundown.</span></span> <span data-ttu-id="59a11-175">(也就是說，啟用 `NGENRundownKeyword`、 `JitRundownKeyword`、 `LoaderRundownKeyword`、或 `AppDomainResourceManagementRundownKeyword` 關鍵字時會將其引發。)</span><span class="sxs-lookup"><span data-stu-id="59a11-175">(That is, they are raised when the `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, or `AppDomainResourceManagementRundownKeyword` keyword is enabled.)</span></span>

<span data-ttu-id="59a11-176">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-176">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="59a11-177">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="59a11-177">Keyword for raising the event</span></span>|<span data-ttu-id="59a11-178">層級</span><span class="sxs-lookup"><span data-stu-id="59a11-178">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="59a11-179">`AppDomainResourceManagementRundownKeyword` (0x800) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-179">`AppDomainResourceManagementRundownKeyword` (0x800) rundown provider</span></span>|<span data-ttu-id="59a11-180">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-180">Informational (4)</span></span>|
|<span data-ttu-id="59a11-181">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-181">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="59a11-182">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-182">Informational (4)</span></span>|
|<span data-ttu-id="59a11-183">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-183">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="59a11-184">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="59a11-184">Informational (4)</span></span>|

<span data-ttu-id="59a11-185">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="59a11-185">The following table shows the event information.</span></span>

|<span data-ttu-id="59a11-186">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-186">Event</span></span>|<span data-ttu-id="59a11-187">事件 ID</span><span class="sxs-lookup"><span data-stu-id="59a11-187">Event ID</span></span>|<span data-ttu-id="59a11-188">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-188">Description</span></span>|
|-----------|--------------|----------------|
|`DCStartInit_V1`|<span data-ttu-id="59a11-189">147</span><span class="sxs-lookup"><span data-stu-id="59a11-189">147</span></span>|<span data-ttu-id="59a11-190">在啟動取消期間、列舉開始之前傳送。</span><span class="sxs-lookup"><span data-stu-id="59a11-190">Sent before the start of the enumeration during a start rundown.</span></span>|
|`DCStartComplete_V1`|<span data-ttu-id="59a11-191">145</span><span class="sxs-lookup"><span data-stu-id="59a11-191">145</span></span>|<span data-ttu-id="59a11-192">在啟動取消期間、列舉結尾時傳送。</span><span class="sxs-lookup"><span data-stu-id="59a11-192">Sent at the end of the enumeration during a start rundown.</span></span>|
|`DCEndInit_V1`|<span data-ttu-id="59a11-193">148</span><span class="sxs-lookup"><span data-stu-id="59a11-193">148</span></span>|<span data-ttu-id="59a11-194">在結束取消期間、開始列舉之前傳送。</span><span class="sxs-lookup"><span data-stu-id="59a11-194">Sent before the start of the enumeration during an end rundown.</span></span>|
|`DCEndComplete_V1`|<span data-ttu-id="59a11-195">146</span><span class="sxs-lookup"><span data-stu-id="59a11-195">146</span></span>|<span data-ttu-id="59a11-196">在結束取消期間、列舉結尾時傳送。</span><span class="sxs-lookup"><span data-stu-id="59a11-196">Sent at the end of the enumeration during an end rundown.</span></span>|

<span data-ttu-id="59a11-197">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="59a11-197">The following table shows the event data.</span></span>

|<span data-ttu-id="59a11-198">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="59a11-198">Field name</span></span>|<span data-ttu-id="59a11-199">資料類型</span><span class="sxs-lookup"><span data-stu-id="59a11-199">Data type</span></span>|<span data-ttu-id="59a11-200">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-200">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="59a11-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="59a11-201">ClrInstanceID</span></span>|<span data-ttu-id="59a11-202">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="59a11-202">win:UInt16</span></span>|<span data-ttu-id="59a11-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="59a11-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="59a11-204">回到頁首</span><span class="sxs-lookup"><span data-stu-id="59a11-204">Back to top</span></span>](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a><span data-ttu-id="59a11-205">CLR 方法詳細資料事件</span><span class="sxs-lookup"><span data-stu-id="59a11-205">CLR Method Verbose Events</span></span>

<span data-ttu-id="59a11-206">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-206">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="59a11-207">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="59a11-207">Keyword for raising the event</span></span>|<span data-ttu-id="59a11-208">層級</span><span class="sxs-lookup"><span data-stu-id="59a11-208">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="59a11-209">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-209">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="59a11-210">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-210">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-211">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-211">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="59a11-212">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-212">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-213">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-213">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="59a11-214">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-214">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-215">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-215">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="59a11-216">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-216">Verbose (5)</span></span>|

<span data-ttu-id="59a11-217">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="59a11-217">The following table shows the event information.</span></span>

|<span data-ttu-id="59a11-218">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-218">Event</span></span>|<span data-ttu-id="59a11-219">事件 ID</span><span class="sxs-lookup"><span data-stu-id="59a11-219">Event ID</span></span>|<span data-ttu-id="59a11-220">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-220">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="59a11-221">143</span><span class="sxs-lookup"><span data-stu-id="59a11-221">143</span></span>|<span data-ttu-id="59a11-222">在 JIT 載入方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-222">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="59a11-223">動態和泛型的方法一律會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="59a11-223">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="59a11-224">JIT Helper 一律會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="59a11-224">JIT helpers always use this version.</span></span>|
|`MethodUnLoadVerbose_V1`|<span data-ttu-id="59a11-225">144</span><span class="sxs-lookup"><span data-stu-id="59a11-225">144</span></span>|<span data-ttu-id="59a11-226">在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-226">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="59a11-227">動態方法永遠一律會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="59a11-227">Dynamic methods always use this version for method unloads.</span></span>|
|`MethodDCStartVerbose_V1`|<span data-ttu-id="59a11-228">141</span><span class="sxs-lookup"><span data-stu-id="59a11-228">141</span></span>|<span data-ttu-id="59a11-229">於啟動取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-229">Enumerates methods during a start rundown.</span></span>|
|`MethodDCEndVerbose_V1`|<span data-ttu-id="59a11-230">142</span><span class="sxs-lookup"><span data-stu-id="59a11-230">142</span></span>|<span data-ttu-id="59a11-231">於結束取消期間列舉方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-231">Enumerates methods during an end rundown.</span></span>|

<span data-ttu-id="59a11-232">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="59a11-232">The following table shows the event data.</span></span>

|<span data-ttu-id="59a11-233">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="59a11-233">Field name</span></span>|<span data-ttu-id="59a11-234">資料類型</span><span class="sxs-lookup"><span data-stu-id="59a11-234">Data type</span></span>|<span data-ttu-id="59a11-235">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-235">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="59a11-236">MethodID</span><span class="sxs-lookup"><span data-stu-id="59a11-236">MethodID</span></span>|<span data-ttu-id="59a11-237">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-237">win:UInt64</span></span>|<span data-ttu-id="59a11-238">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="59a11-238">Unique identifier of the method.</span></span> <span data-ttu-id="59a11-239">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="59a11-239">For JIT helper methods, set to the start address of the method.</span></span>|
|<span data-ttu-id="59a11-240">ModuleID</span><span class="sxs-lookup"><span data-stu-id="59a11-240">ModuleID</span></span>|<span data-ttu-id="59a11-241">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-241">win:UInt64</span></span>|<span data-ttu-id="59a11-242">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="59a11-242">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|<span data-ttu-id="59a11-243">MethodStartAddress</span><span class="sxs-lookup"><span data-stu-id="59a11-243">MethodStartAddress</span></span>|<span data-ttu-id="59a11-244">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-244">win:UInt64</span></span>|<span data-ttu-id="59a11-245">起始位址：</span><span class="sxs-lookup"><span data-stu-id="59a11-245">Start address.</span></span>|
|<span data-ttu-id="59a11-246">MethodSize</span><span class="sxs-lookup"><span data-stu-id="59a11-246">MethodSize</span></span>|<span data-ttu-id="59a11-247">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-247">win:UInt32</span></span>|<span data-ttu-id="59a11-248">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="59a11-248">Method length.</span></span>|
|<span data-ttu-id="59a11-249">MethodToken</span><span class="sxs-lookup"><span data-stu-id="59a11-249">MethodToken</span></span>|<span data-ttu-id="59a11-250">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-250">win:UInt32</span></span>|<span data-ttu-id="59a11-251">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="59a11-251">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="59a11-252">MethodFlags</span><span class="sxs-lookup"><span data-stu-id="59a11-252">MethodFlags</span></span>|<span data-ttu-id="59a11-253">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-253">win:UInt32</span></span>|<span data-ttu-id="59a11-254">0x1動態方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-254">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="59a11-255">0x2泛型方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-255">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="59a11-256">0x4JIT 編譯的方法（否則由 Ngen.exe 產生）</span><span class="sxs-lookup"><span data-stu-id="59a11-256">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="59a11-257">0x8Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="59a11-257">0x8: Helper method.</span></span>|
|<span data-ttu-id="59a11-258">MethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="59a11-258">MethodNameSpace</span></span>|<span data-ttu-id="59a11-259">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-259">win:UnicodeString</span></span>|<span data-ttu-id="59a11-260">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="59a11-260">Full namespace name associated with the method.</span></span>|
|<span data-ttu-id="59a11-261">MethodName</span><span class="sxs-lookup"><span data-stu-id="59a11-261">MethodName</span></span>|<span data-ttu-id="59a11-262">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-262">win:UnicodeString</span></span>|<span data-ttu-id="59a11-263">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="59a11-263">Full class name associated with the method.</span></span>|
|<span data-ttu-id="59a11-264">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="59a11-264">MethodSignature</span></span>|<span data-ttu-id="59a11-265">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-265">win:UnicodeString</span></span>|<span data-ttu-id="59a11-266">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="59a11-266">Signature of the method (comma-separated list of type names).</span></span>|
|<span data-ttu-id="59a11-267">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="59a11-267">ClrInstanceID</span></span>|<span data-ttu-id="59a11-268">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="59a11-268">win:UInt16</span></span>|<span data-ttu-id="59a11-269">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="59a11-269">Unique ID for the instance of CLR or CoreCLR.</span></span>|

[<span data-ttu-id="59a11-270">回到頁首</span><span class="sxs-lookup"><span data-stu-id="59a11-270">Back to top</span></span>](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a><span data-ttu-id="59a11-271">MethodJittingStarted 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-271">MethodJittingStarted Event</span></span>

<span data-ttu-id="59a11-272">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="59a11-272">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="59a11-273">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="59a11-273">Keyword for raising the event</span></span>|<span data-ttu-id="59a11-274">層級</span><span class="sxs-lookup"><span data-stu-id="59a11-274">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="59a11-275">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-275">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="59a11-276">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-276">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-277">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-277">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="59a11-278">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-278">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-279">`JitRundownKeyword` (0x10) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-279">`JitRundownKeyword` (0x10) rundown provider</span></span>|<span data-ttu-id="59a11-280">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-280">Verbose (5)</span></span>|
|<span data-ttu-id="59a11-281">`NGENRundownKeyword` (0x20) 取消提供者</span><span class="sxs-lookup"><span data-stu-id="59a11-281">`NGENRundownKeyword` (0x20) rundown provider</span></span>|<span data-ttu-id="59a11-282">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="59a11-282">Verbose (5)</span></span>|

<span data-ttu-id="59a11-283">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="59a11-283">The following table shows the event information.</span></span>

|<span data-ttu-id="59a11-284">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-284">Event</span></span>|<span data-ttu-id="59a11-285">事件 ID</span><span class="sxs-lookup"><span data-stu-id="59a11-285">Event ID</span></span>|<span data-ttu-id="59a11-286">說明</span><span class="sxs-lookup"><span data-stu-id="59a11-286">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|<span data-ttu-id="59a11-287">145</span><span class="sxs-lookup"><span data-stu-id="59a11-287">145</span></span>|<span data-ttu-id="59a11-288">當某個方法正在進行 JIT 編譯時引發。</span><span class="sxs-lookup"><span data-stu-id="59a11-288">Raised when a method is being JIT-compiled.</span></span>|

<span data-ttu-id="59a11-289">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="59a11-289">The following table shows the event data.</span></span>

|<span data-ttu-id="59a11-290">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="59a11-290">Field name</span></span>|<span data-ttu-id="59a11-291">資料類型</span><span class="sxs-lookup"><span data-stu-id="59a11-291">Data type</span></span>|<span data-ttu-id="59a11-292">描述</span><span class="sxs-lookup"><span data-stu-id="59a11-292">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="59a11-293">MethodID</span><span class="sxs-lookup"><span data-stu-id="59a11-293">MethodID</span></span>|<span data-ttu-id="59a11-294">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-294">win:UInt64</span></span>|<span data-ttu-id="59a11-295">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="59a11-295">Unique identifier of the method.</span></span>|
|<span data-ttu-id="59a11-296">ModuleID</span><span class="sxs-lookup"><span data-stu-id="59a11-296">ModuleID</span></span>|<span data-ttu-id="59a11-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="59a11-297">win:UInt64</span></span>|<span data-ttu-id="59a11-298">這個方法所屬之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="59a11-298">Identifier of the module to which this method belongs.</span></span>|
|<span data-ttu-id="59a11-299">MethodToken</span><span class="sxs-lookup"><span data-stu-id="59a11-299">MethodToken</span></span>|<span data-ttu-id="59a11-300">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-300">win:UInt32</span></span>|<span data-ttu-id="59a11-301">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="59a11-301">0 for dynamic methods and JIT helpers.</span></span>|
|<span data-ttu-id="59a11-302">MethodILSize</span><span class="sxs-lookup"><span data-stu-id="59a11-302">MethodILSize</span></span>|<span data-ttu-id="59a11-303">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="59a11-303">win:UInt32</span></span>|<span data-ttu-id="59a11-304">正在進行 JIT 編譯之方法的 Microsoft Intermediate Language (MSIL) 大小。</span><span class="sxs-lookup"><span data-stu-id="59a11-304">The size of the Microsoft intermediate language (MSIL) for the method that is being JIT-compiled.</span></span>|
|<span data-ttu-id="59a11-305">MethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="59a11-305">MethodNameSpace</span></span>|<span data-ttu-id="59a11-306">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-306">win:UnicodeString</span></span>|<span data-ttu-id="59a11-307">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="59a11-307">Full class name associated with the method.</span></span>|
|<span data-ttu-id="59a11-308">MethodName</span><span class="sxs-lookup"><span data-stu-id="59a11-308">MethodName</span></span>|<span data-ttu-id="59a11-309">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-309">win:UnicodeString</span></span>|<span data-ttu-id="59a11-310">方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="59a11-310">Name of the method.</span></span>|
|<span data-ttu-id="59a11-311">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="59a11-311">MethodSignature</span></span>|<span data-ttu-id="59a11-312">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="59a11-312">win:UnicodeString</span></span>|<span data-ttu-id="59a11-313">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="59a11-313">Signature of the method (comma-separated list of type names).</span></span>|
|<span data-ttu-id="59a11-314">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="59a11-314">ClrInstanceID</span></span>|<span data-ttu-id="59a11-315">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="59a11-315">win:UInt16</span></span>|<span data-ttu-id="59a11-316">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="59a11-316">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="59a11-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59a11-317">See also</span></span>

- [<span data-ttu-id="59a11-318">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="59a11-318">CLR ETW Events</span></span>](clr-etw-events.md)
