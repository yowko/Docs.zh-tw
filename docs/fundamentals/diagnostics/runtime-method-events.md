---
title: 方法運行時間事件
description: 請參閱收集方法特定診斷資訊的 .NET 運行時間事件，例如 CLR 方法事件、CLR 方法標記或 CLR 方法詳細資訊事件，以及 MethodJittingStarted。
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586634"
---
# <a name="net-runtime-method-events"></a><span data-ttu-id="1f131-103">.NET 執行時間方法事件</span><span class="sxs-lookup"><span data-stu-id="1f131-103">.NET runtime method events</span></span>

<span data-ttu-id="1f131-104">這些事件會收集方法的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="1f131-104">These events collect information that is specific to methods.</span></span> <span data-ttu-id="1f131-105">若要進行符號解析，需使用這些事件的承載。</span><span class="sxs-lookup"><span data-stu-id="1f131-105">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="1f131-106">此外，這些事件會提供有用的資訊，例如載入和卸載的方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-106">In addition, these events provide helpful information such as methods that are loaded and unloaded.</span></span> <span data-ttu-id="1f131-107">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="1f131-107">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

<span data-ttu-id="1f131-108">所有方法事件都具「告知性 (4)」的層級。</span><span class="sxs-lookup"><span data-stu-id="1f131-108">All method events have a level of "Informational (4)".</span></span> <span data-ttu-id="1f131-109">所有方法的詳細資訊事件都具「詳細資訊 (5)」的層級。</span><span class="sxs-lookup"><span data-stu-id="1f131-109">All method verbose events have a level of "Verbose (5)".</span></span>

<span data-ttu-id="1f131-110">所有方法事件都是由執行階段提供者下的 `JITKeyword` (0x10) 關鍵字或 `NGenKeyword` (0x20) 關鍵字，或由取消提供者下的 `JitRundownKeyword` (0x10) 或 `NGENRundownKeyword` (0x20) 所引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-110">All method events are raised by the `JITKeyword` (0x10) keyword or the `NGenKeyword` (0x20) keyword under the runtime provider, or `JitRundownKeyword` (0x10) or `NGENRundownKeyword` (0x20) under the rundown provider.</span></span>

<span data-ttu-id="1f131-111">這些事件的 V2 版本包含 ReJITID，V1 版本則否。</span><span class="sxs-lookup"><span data-stu-id="1f131-111">The V2 versions of these events include the ReJITID, the V1 versions do not.</span></span>

## <a name="methodload_v1-event"></a><span data-ttu-id="1f131-112">MethodLoad_V1 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-112">MethodLoad_V1 event</span></span>

<span data-ttu-id="1f131-113">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="1f131-113">The following table shows the event information:</span></span>

|<span data-ttu-id="1f131-114">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-114">Event</span></span>|<span data-ttu-id="1f131-115">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-115">Event ID</span></span>|<span data-ttu-id="1f131-116">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-116">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|<span data-ttu-id="1f131-117">141</span><span class="sxs-lookup"><span data-stu-id="1f131-117">141</span></span>|<span data-ttu-id="1f131-118">在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-118">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="1f131-119">動態和泛型的方法並不會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="1f131-119">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="1f131-120">JIT Helper 永遠不會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="1f131-120">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="1f131-121">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-121">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-122">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-122">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-123">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="1f131-123">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="1f131-124">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-124">Informational (4)</span></span>|
|<span data-ttu-id="1f131-125">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="1f131-125">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="1f131-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-126">Informational (4)</span></span>|

|<span data-ttu-id="1f131-127">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-127">Field name</span></span>|<span data-ttu-id="1f131-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-128">Data type</span></span>|<span data-ttu-id="1f131-129">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-129">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-130">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-130">Unique identifier of a method.</span></span> <span data-ttu-id="1f131-131">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-131">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-132">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-132">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-133">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-133">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-134">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="1f131-134">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-135">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-135">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-136">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-136">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-137">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-137">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-138">0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。</span><span class="sxs-lookup"><span data-stu-id="1f131-138">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="1f131-139">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-139">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-140">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-140">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodload_v2-event"></a><span data-ttu-id="1f131-141">MethodLoad_V2 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-141">MethodLoad_V2 event</span></span>

|<span data-ttu-id="1f131-142">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-142">Event</span></span>|<span data-ttu-id="1f131-143">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-143">Event ID</span></span>|<span data-ttu-id="1f131-144">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-144">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|<span data-ttu-id="1f131-145">141</span><span class="sxs-lookup"><span data-stu-id="1f131-145">141</span></span>|<span data-ttu-id="1f131-146">在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-146">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="1f131-147">動態和泛型的方法並不會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="1f131-147">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="1f131-148">JIT Helper 永遠不會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="1f131-148">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="1f131-149">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-149">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-150">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-150">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-151">`JITKeyword` (0x10) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="1f131-151">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="1f131-152">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-152">Informational (4)</span></span>|
|<span data-ttu-id="1f131-153">`NGenKeyword` (0x20) 執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="1f131-153">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="1f131-154">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-154">Informational (4)</span></span>|

|<span data-ttu-id="1f131-155">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-155">Field name</span></span>|<span data-ttu-id="1f131-156">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-156">Data type</span></span>|<span data-ttu-id="1f131-157">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-157">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-158">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-158">Unique identifier of a method.</span></span> <span data-ttu-id="1f131-159">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-159">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-160">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-160">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-161">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-161">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-162">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="1f131-162">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-163">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-163">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-164">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-164">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-165">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-165">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-166">0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。</span><span class="sxs-lookup"><span data-stu-id="1f131-166">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="1f131-167">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-167">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="1f131-168">方法的 ReJIT 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-168">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-169">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-169">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v1-event"></a><span data-ttu-id="1f131-170">MethodUnLoad_V1 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-170">MethodUnLoad_V1 event</span></span>

|<span data-ttu-id="1f131-171">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-171">Event</span></span>|<span data-ttu-id="1f131-172">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-172">Event ID</span></span>|<span data-ttu-id="1f131-173">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-173">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|<span data-ttu-id="1f131-174">142</span><span class="sxs-lookup"><span data-stu-id="1f131-174">142</span></span>|<span data-ttu-id="1f131-175">在模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-175">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="1f131-176">動態方法永遠不會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="1f131-176">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="1f131-177">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-177">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-178">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-178">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-179">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-179">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="1f131-180">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-180">Informational (4)</span></span>|
|<span data-ttu-id="1f131-181">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-181">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="1f131-182">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-182">Informational (4)</span></span>|

|<span data-ttu-id="1f131-183">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-183">Field name</span></span>|<span data-ttu-id="1f131-184">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-184">Data type</span></span>|<span data-ttu-id="1f131-185">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-185">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-186">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-186">Unique identifier of a method.</span></span> <span data-ttu-id="1f131-187">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-187">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-188">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-188">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-189">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-189">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-190">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="1f131-190">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-191">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-191">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-192">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-192">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-193">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-193">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-194">0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。</span><span class="sxs-lookup"><span data-stu-id="1f131-194">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="1f131-195">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-195">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-196">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-196">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v2-event"></a><span data-ttu-id="1f131-197">MethodUnLoad_V2 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-197">MethodUnLoad_V2 event</span></span>

|<span data-ttu-id="1f131-198">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-198">Event</span></span>|<span data-ttu-id="1f131-199">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-199">Event ID</span></span>|<span data-ttu-id="1f131-200">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-200">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|<span data-ttu-id="1f131-201">142</span><span class="sxs-lookup"><span data-stu-id="1f131-201">142</span></span>|<span data-ttu-id="1f131-202">在模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-202">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="1f131-203">動態方法永遠不會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="1f131-203">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="1f131-204">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-204">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-205">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-205">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-206">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-206">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="1f131-207">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-207">Informational (4)</span></span>|
|<span data-ttu-id="1f131-208">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-208">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="1f131-209">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-209">Informational (4)</span></span>|

|<span data-ttu-id="1f131-210">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-210">Field name</span></span>|<span data-ttu-id="1f131-211">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-211">Data type</span></span>|<span data-ttu-id="1f131-212">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-212">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-213">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-213">Unique identifier of a method.</span></span> <span data-ttu-id="1f131-214">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-214">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-215">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-215">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-216">方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-216">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-217">方法的大小。</span><span class="sxs-lookup"><span data-stu-id="1f131-217">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-218">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-218">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-219">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-219">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-220">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-220">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-221">0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。</span><span class="sxs-lookup"><span data-stu-id="1f131-221">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="1f131-222">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-222">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="1f131-223">方法的 ReJIT 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-223">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-224">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-224">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypoint-event"></a><span data-ttu-id="1f131-225">R2RGetEntryPoint 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-225">R2RGetEntryPoint event</span></span>

|<span data-ttu-id="1f131-226">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-226">Event</span></span>|<span data-ttu-id="1f131-227">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-227">Event ID</span></span>|<span data-ttu-id="1f131-228">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-228">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|<span data-ttu-id="1f131-229">159</span><span class="sxs-lookup"><span data-stu-id="1f131-229">159</span></span>|<span data-ttu-id="1f131-230">在 R2R 進入點查閱結束時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-230">Raised when an R2R entry point lookup ends.</span></span>|

|<span data-ttu-id="1f131-231">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-231">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-232">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-232">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-233">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-233">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-234">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-234">Informational (4)</span></span>|
|<span data-ttu-id="1f131-235">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-235">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-236">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-236">Informational (4)</span></span>|

|<span data-ttu-id="1f131-237">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-237">Field name</span></span>|<span data-ttu-id="1f131-238">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-238">Data type</span></span>|<span data-ttu-id="1f131-239">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-239">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-240">R2R 方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-240">Unique identifier of a R2R method.</span></span>|
|`MethodNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-241">要查閱之方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-241">The namespace of method being looked up.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-242">要查閱之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-242">The name of the method being looked up.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-243">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-243">Signature of the method (comma-separated list of type names).</span></span>|
|`EntryPoint`|`win:UInt64`|<span data-ttu-id="1f131-244">R2R 方法進入點的指標</span><span class="sxs-lookup"><span data-stu-id="1f131-244">The pointer to the entry point of the R2R method</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-245">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-245">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypointstart-event"></a><span data-ttu-id="1f131-246">R2RGetEntryPointStart 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-246">R2RGetEntryPointStart event</span></span>

|<span data-ttu-id="1f131-247">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-247">Event</span></span>|<span data-ttu-id="1f131-248">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-248">Event ID</span></span>|<span data-ttu-id="1f131-249">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-249">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|<span data-ttu-id="1f131-250">160</span><span class="sxs-lookup"><span data-stu-id="1f131-250">160</span></span>|<span data-ttu-id="1f131-251">在 R2R 進入點查閱開始時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-251">Raised when an R2R entry point lookup starts.</span></span>|

|<span data-ttu-id="1f131-252">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-252">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-253">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-253">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-254">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-254">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-255">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-255">Informational (4)</span></span>|
|<span data-ttu-id="1f131-256">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-256">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-257">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-257">Informational (4)</span></span>|

|<span data-ttu-id="1f131-258">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-258">Field name</span></span>|<span data-ttu-id="1f131-259">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-259">Data type</span></span>|<span data-ttu-id="1f131-260">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-260">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-261">R2R 方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-261">Unique identifier of a R2R method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-262">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-262">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v1-event"></a><span data-ttu-id="1f131-263">MethodLoadVerbose_V1 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-263">MethodLoadVerbose_V1 event</span></span>

|<span data-ttu-id="1f131-264">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-264">Event</span></span>|<span data-ttu-id="1f131-265">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-265">Event ID</span></span>|<span data-ttu-id="1f131-266">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-266">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="1f131-267">143</span><span class="sxs-lookup"><span data-stu-id="1f131-267">143</span></span>|<span data-ttu-id="1f131-268">在 JIT 載入方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-268">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="1f131-269">動態和泛型的方法一律會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="1f131-269">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="1f131-270">JIT Helper 一律會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="1f131-270">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="1f131-271">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-271">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-272">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-272">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-273">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-273">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-274">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-274">Informational (4)</span></span>|
|<span data-ttu-id="1f131-275">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-275">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-276">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-276">Informational (4)</span></span>|

|<span data-ttu-id="1f131-277">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-277">Field name</span></span>|<span data-ttu-id="1f131-278">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-278">Data type</span></span>|<span data-ttu-id="1f131-279">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-279">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-280">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="1f131-280">Unique identifier of the method.</span></span> <span data-ttu-id="1f131-281">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-281">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-282">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-282">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-283">起始位址：</span><span class="sxs-lookup"><span data-stu-id="1f131-283">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-284">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="1f131-284">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-285">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-285">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-286">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-286">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-287">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-287">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-288">0x4：JIT 編譯方法 (否則由 NGen.exe 產生)</span><span class="sxs-lookup"><span data-stu-id="1f131-288">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="1f131-289">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-289">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="1f131-290">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-290">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-291">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-291">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-292">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-292">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-293">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-293">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v2-event"></a><span data-ttu-id="1f131-294">MethodLoadVerbose_V2 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-294">MethodLoadVerbose_V2 event</span></span>

|<span data-ttu-id="1f131-295">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-295">Event</span></span>|<span data-ttu-id="1f131-296">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-296">Event ID</span></span>|<span data-ttu-id="1f131-297">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-297">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="1f131-298">143</span><span class="sxs-lookup"><span data-stu-id="1f131-298">143</span></span>|<span data-ttu-id="1f131-299">在 JIT 載入方法或 NGEN 映像載入時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-299">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="1f131-300">動態和泛型的方法一律會使用這個版本的方法載入。</span><span class="sxs-lookup"><span data-stu-id="1f131-300">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="1f131-301">JIT Helper 一律會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="1f131-301">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="1f131-302">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-302">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-303">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-304">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-304">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-305">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-305">Informational (4)</span></span>|
|<span data-ttu-id="1f131-306">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-306">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-307">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-307">Informational (4)</span></span>|

|<span data-ttu-id="1f131-308">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-308">Field name</span></span>|<span data-ttu-id="1f131-309">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-309">Data type</span></span>|<span data-ttu-id="1f131-310">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-310">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-311">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="1f131-311">Unique identifier of the method.</span></span> <span data-ttu-id="1f131-312">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-312">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-313">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-313">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-314">起始位址：</span><span class="sxs-lookup"><span data-stu-id="1f131-314">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-315">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="1f131-315">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-316">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-316">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-317">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-317">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-318">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-318">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-319">0x4：JIT 編譯方法 (否則由 NGen.exe 產生)</span><span class="sxs-lookup"><span data-stu-id="1f131-319">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="1f131-320">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-320">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="1f131-321">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-321">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-322">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-322">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-323">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-323">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="1f131-324">方法的 ReJIT 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-324">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-325">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-325">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v1-event"></a><span data-ttu-id="1f131-326">MethodUnLoadVerbose_V1 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-326">MethodUnLoadVerbose_V1 event</span></span>

|<span data-ttu-id="1f131-327">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-327">Event</span></span>|<span data-ttu-id="1f131-328">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-328">Event ID</span></span>|<span data-ttu-id="1f131-329">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-329">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|<span data-ttu-id="1f131-330">144</span><span class="sxs-lookup"><span data-stu-id="1f131-330">144</span></span>|<span data-ttu-id="1f131-331">在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-331">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="1f131-332">動態方法永遠一律會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="1f131-332">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="1f131-333">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-333">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-334">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-334">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-335">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-335">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-336">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-336">Informational (4)</span></span>|
|<span data-ttu-id="1f131-337">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-337">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-338">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-338">Informational (4)</span></span>|

|<span data-ttu-id="1f131-339">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-339">Field name</span></span>|<span data-ttu-id="1f131-340">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-340">Data type</span></span>|<span data-ttu-id="1f131-341">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-341">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-342">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="1f131-342">Unique identifier of the method.</span></span> <span data-ttu-id="1f131-343">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-343">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-344">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-344">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-345">起始位址：</span><span class="sxs-lookup"><span data-stu-id="1f131-345">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-346">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="1f131-346">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-347">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-347">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-348">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-348">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-349">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-349">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-350">0x4：JIT 編譯方法 (否則由 NGen.exe 產生)</span><span class="sxs-lookup"><span data-stu-id="1f131-350">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="1f131-351">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-351">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="1f131-352">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-352">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-353">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-353">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-354">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-354">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-355">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-355">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v2-event"></a><span data-ttu-id="1f131-356">MethodUnLoadVerbose_V2 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-356">MethodUnLoadVerbose_V2 event</span></span>

|<span data-ttu-id="1f131-357">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-357">Event</span></span>|<span data-ttu-id="1f131-358">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-358">Event ID</span></span>|<span data-ttu-id="1f131-359">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-359">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|<span data-ttu-id="1f131-360">144</span><span class="sxs-lookup"><span data-stu-id="1f131-360">144</span></span>|<span data-ttu-id="1f131-361">在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-361">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="1f131-362">動態方法永遠一律會使用這個版本的方法卸載。</span><span class="sxs-lookup"><span data-stu-id="1f131-362">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="1f131-363">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-363">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-364">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-364">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-365">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-365">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-366">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-366">Informational (4)</span></span>|
|<span data-ttu-id="1f131-367">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-367">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-368">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="1f131-368">Informational (4)</span></span>|

|<span data-ttu-id="1f131-369">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-369">Field name</span></span>|<span data-ttu-id="1f131-370">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-370">Data type</span></span>|<span data-ttu-id="1f131-371">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-371">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-372">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="1f131-372">Unique identifier of the method.</span></span> <span data-ttu-id="1f131-373">若是 JIT Helper 方法，其設為方法的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1f131-373">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-374">這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。</span><span class="sxs-lookup"><span data-stu-id="1f131-374">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="1f131-375">起始位址：</span><span class="sxs-lookup"><span data-stu-id="1f131-375">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="1f131-376">方法的長度。</span><span class="sxs-lookup"><span data-stu-id="1f131-376">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-377">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-377">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="1f131-378">0x1：動態方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-378">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="1f131-379">0x2：泛型方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-379">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="1f131-380">0x4：JIT 編譯方法 (否則由 NGen.exe 產生)</span><span class="sxs-lookup"><span data-stu-id="1f131-380">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="1f131-381">0x8：Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="1f131-381">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="1f131-382">與方法相關聯的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-382">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-383">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-383">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-384">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-384">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="1f131-385">方法的 ReJIT 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-385">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-386">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-386">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittingstarted_v1-event"></a><span data-ttu-id="1f131-387">MethodJittingStarted_V1 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-387">MethodJittingStarted_V1 event</span></span>

<span data-ttu-id="1f131-388">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="1f131-388">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="1f131-389">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-389">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-390">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-390">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-391">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="1f131-391">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="1f131-392">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-392">Verbose (5)</span></span>|
|<span data-ttu-id="1f131-393">`NGenKeyword` (0x20) </span><span class="sxs-lookup"><span data-stu-id="1f131-393">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="1f131-394">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-394">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-395">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-395">Event</span></span>|<span data-ttu-id="1f131-396">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-396">Event ID</span></span>|<span data-ttu-id="1f131-397">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-397">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|<span data-ttu-id="1f131-398">145</span><span class="sxs-lookup"><span data-stu-id="1f131-398">145</span></span>|<span data-ttu-id="1f131-399">當某個方法正在進行 JIT 編譯時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-399">Raised when a method is being JIT-compiled.</span></span>|

|<span data-ttu-id="1f131-400">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-400">Field name</span></span>|<span data-ttu-id="1f131-401">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-401">Data type</span></span>|<span data-ttu-id="1f131-402">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-402">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-403">方法的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="1f131-403">Unique identifier of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="1f131-404">這個方法所屬之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-404">Identifier of the module to which this method belongs.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="1f131-405">0 代表動態方法和 JIT Helper。</span><span class="sxs-lookup"><span data-stu-id="1f131-405">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodILSize`|`win:UInt32`|<span data-ttu-id="1f131-406">針對正在進行 JIT 編譯的方法，一般中繼語言 (CIL) 的大小。</span><span class="sxs-lookup"><span data-stu-id="1f131-406">The size of the Common Intermediate Language (CIL) for the method that is being JIT-compiled.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="1f131-407">與方法相關聯的完整類別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-407">Full class name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="1f131-408">方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-408">Name of the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-409">方法的簽章 (以逗號分隔的類型名稱清單)。</span><span class="sxs-lookup"><span data-stu-id="1f131-409">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-410">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-410">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningsucceeded-event"></a><span data-ttu-id="1f131-411">MethodJitInliningSucceeded 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-411">MethodJitInliningSucceeded event</span></span>

|<span data-ttu-id="1f131-412">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-412">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-413">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-413">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-414">`JITTracingKeyword` (0x1000) </span><span class="sxs-lookup"><span data-stu-id="1f131-414">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="1f131-415">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-415">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-416">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-416">Event</span></span>|<span data-ttu-id="1f131-417">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-417">Event ID</span></span>|<span data-ttu-id="1f131-418">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-418">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|<span data-ttu-id="1f131-419">185</span><span class="sxs-lookup"><span data-stu-id="1f131-419">185</span></span>|<span data-ttu-id="1f131-420">當 JIT 編譯程式成功內嵌方法時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-420">Raised when a method is successfully inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="1f131-421">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-421">Field name</span></span>|<span data-ttu-id="1f131-422">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-422">Data type</span></span>|<span data-ttu-id="1f131-423">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-423">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-424">正在編譯之方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-424">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="1f131-425">正在編譯之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-425">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-426">方法的簽章 () 要編譯之類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-426">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-427">章 ( "parent" ) 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-427">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="1f131-428">章 ( "parent" ) 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-428">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-429">章 ( "parent" ) 方法的簽章 () 類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-429">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-430">內嵌項 ( "child" ) 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-430">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="1f131-431">內嵌項 ( "child" ) 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-431">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-432">內嵌項 ( "child" ) 方法的簽章 () 的類型名稱清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="1f131-432">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-433">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-433">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningfailed-event"></a><span data-ttu-id="1f131-434">MethodJitInliningFailed 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-434">MethodJitInliningFailed event</span></span>

|<span data-ttu-id="1f131-435">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-435">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-436">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-436">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-437">`JITTracingKeyword` (0x1000) </span><span class="sxs-lookup"><span data-stu-id="1f131-437">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="1f131-438">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-438">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-439">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-439">Event</span></span>|<span data-ttu-id="1f131-440">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-440">Event ID</span></span>|<span data-ttu-id="1f131-441">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-441">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|<span data-ttu-id="1f131-442">192</span><span class="sxs-lookup"><span data-stu-id="1f131-442">192</span></span>|<span data-ttu-id="1f131-443">當 JIT 編譯程式無法內嵌方法時引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-443">Raised when a method was failed to be inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="1f131-444">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-444">Field name</span></span>|<span data-ttu-id="1f131-445">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-445">Data type</span></span>|<span data-ttu-id="1f131-446">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-446">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-447">正在編譯之方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-447">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="1f131-448">正在編譯之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-448">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-449">方法的簽章 () 要編譯之類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-449">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-450">章 ( "parent" ) 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-450">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="1f131-451">章 ( "parent" ) 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-451">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-452">章 ( "parent" ) 方法的簽章 () 類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-452">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-453">內嵌項 ( "child" ) 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-453">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="1f131-454">內嵌項 ( "child" ) 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-454">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-455">內嵌項 ( "child" ) 方法的簽章 () 的類型名稱清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="1f131-455">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`FailAlways`|`win:Boolean`|<span data-ttu-id="1f131-456">方法是否標記為非內嵌。</span><span class="sxs-lookup"><span data-stu-id="1f131-456">Whether the method is marked as not inlinable.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="1f131-457">內嵌失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="1f131-457">Reason inlining failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-458">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-458">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallsucceeded-event"></a><span data-ttu-id="1f131-459">MethodJitTailCallSucceeded 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-459">MethodJitTailCallSucceeded event</span></span>

|<span data-ttu-id="1f131-460">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-460">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-461">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-461">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-462">`JITTracingKeyword` (0x1000) </span><span class="sxs-lookup"><span data-stu-id="1f131-462">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="1f131-463">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-463">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-464">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-464">Event</span></span>|<span data-ttu-id="1f131-465">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-465">Event ID</span></span>|<span data-ttu-id="1f131-466">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-466">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|<span data-ttu-id="1f131-467">192</span><span class="sxs-lookup"><span data-stu-id="1f131-467">192</span></span>|<span data-ttu-id="1f131-468">當可以成功呼叫方法時，由 JIT 編譯程式引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-468">Raised by the JIT compiler when a method can be successfully tail called.</span></span>|

|<span data-ttu-id="1f131-469">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-469">Field name</span></span>|<span data-ttu-id="1f131-470">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-470">Data type</span></span>|<span data-ttu-id="1f131-471">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-471">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-472">正在編譯之方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-472">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="1f131-473">正在編譯之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-473">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-474">方法的簽章 () 要編譯之類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-474">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-475">呼叫端方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-475">Namespace of the caller method.</span></span>|
|`CallerName`|`win:UnicodeString`|<span data-ttu-id="1f131-476">呼叫端方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-476">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-477">呼叫端方法的簽章 () 的型別名稱清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="1f131-477">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-478">被呼叫端方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-478">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="1f131-479">被呼叫端方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-479">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-480">被呼叫端方法的簽章 () 類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-480">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="1f131-481">是否為結尾前置詞指令。</span><span class="sxs-lookup"><span data-stu-id="1f131-481">Whether it is a tail prefix instruction.</span></span>|
|`TailCallType`|`win:UInt32`|<span data-ttu-id="1f131-482">Tail 呼叫的類型。</span><span class="sxs-lookup"><span data-stu-id="1f131-482">The type of tail call.</span></span><br/><br/><span data-ttu-id="1f131-483">0：優化的 tail 呼叫 (終解 + jmp) </span><span class="sxs-lookup"><span data-stu-id="1f131-483">0: Optimized tail call (epilog + jmp)</span></span><br/><br/><span data-ttu-id="1f131-484">1：遞迴 tail 呼叫 (方法 tail 呼叫本身) </span><span class="sxs-lookup"><span data-stu-id="1f131-484">1: Recursive tail call (method tail calls itself)</span></span><br/><br/><span data-ttu-id="1f131-485">2： Helper 輔助的 tail 呼叫</span><span class="sxs-lookup"><span data-stu-id="1f131-485">2: Helper assisted tail call</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-486">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-486">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallfailed-event"></a><span data-ttu-id="1f131-487">MethodJitTailCallFailed 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-487">MethodJitTailCallFailed event</span></span>

|<span data-ttu-id="1f131-488">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-488">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-489">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-489">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-490">`JITTracingKeyword` (0x1000) </span><span class="sxs-lookup"><span data-stu-id="1f131-490">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="1f131-491">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-491">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-492">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-492">Event</span></span>|<span data-ttu-id="1f131-493">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-493">Event ID</span></span>|<span data-ttu-id="1f131-494">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-494">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|<span data-ttu-id="1f131-495">191</span><span class="sxs-lookup"><span data-stu-id="1f131-495">191</span></span>|<span data-ttu-id="1f131-496">當方法無法被呼叫時，由 JIT 編譯程式引發。</span><span class="sxs-lookup"><span data-stu-id="1f131-496">Raised by the JIT compiler when a method was failed to be tail called.</span></span>|

|<span data-ttu-id="1f131-497">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-497">Field name</span></span>|<span data-ttu-id="1f131-498">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-498">Data type</span></span>|<span data-ttu-id="1f131-499">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-499">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-500">正在編譯之方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-500">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="1f131-501">正在編譯之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-501">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-502">方法的簽章 () 要編譯之類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-502">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-503">呼叫端方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-503">Namespace of the caller method.</span></span>|
|<span data-ttu-id="1f131-504">`CallerNam`e</span><span class="sxs-lookup"><span data-stu-id="1f131-504">`CallerNam`e</span></span>|`win:UnicodeString`|<span data-ttu-id="1f131-505">呼叫端方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-505">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-506">呼叫端方法的簽章 () 的型別名稱清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="1f131-506">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="1f131-507">被呼叫端方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f131-507">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="1f131-508">被呼叫端方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f131-508">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="1f131-509">被呼叫端方法的簽章 () 類型名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="1f131-509">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="1f131-510">是否為結尾前置詞指令。</span><span class="sxs-lookup"><span data-stu-id="1f131-510">Whether it is a tail prefix instruction.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="1f131-511">Tail 呼叫失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="1f131-511">Reason tail call failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-512">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-512">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodiltonativemap-event"></a><span data-ttu-id="1f131-513">MethodILToNativeMap 事件</span><span class="sxs-lookup"><span data-stu-id="1f131-513">MethodILToNativeMap event</span></span>

|<span data-ttu-id="1f131-514">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f131-514">Keyword for raising the event</span></span>|<span data-ttu-id="1f131-515">層級</span><span class="sxs-lookup"><span data-stu-id="1f131-515">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f131-516">`JittedMethodILToNativeMapKeyword` (0x20000) </span><span class="sxs-lookup"><span data-stu-id="1f131-516">`JittedMethodILToNativeMapKeyword` (0x20000)</span></span> |<span data-ttu-id="1f131-517">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="1f131-517">Verbose (5)</span></span>|

|<span data-ttu-id="1f131-518">事件</span><span class="sxs-lookup"><span data-stu-id="1f131-518">Event</span></span>|<span data-ttu-id="1f131-519">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f131-519">Event ID</span></span>|<span data-ttu-id="1f131-520">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-520">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|<span data-ttu-id="1f131-521">190</span><span class="sxs-lookup"><span data-stu-id="1f131-521">190</span></span>|<span data-ttu-id="1f131-522">對應 JIT 編譯方法的 IL 對原生對應事件。</span><span class="sxs-lookup"><span data-stu-id="1f131-522">Maps the IL-to-native map event for JIT-compiled methods.</span></span>|

|<span data-ttu-id="1f131-523">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-523">Field name</span></span>|<span data-ttu-id="1f131-524">資料類型</span><span class="sxs-lookup"><span data-stu-id="1f131-524">Data type</span></span>|<span data-ttu-id="1f131-525">描述</span><span class="sxs-lookup"><span data-stu-id="1f131-525">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="1f131-526">方法的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-526">Unique identifier of a method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="1f131-527">方法的 ReJIT 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-527">The ReJIT ID of the method.</span></span>|
|`MethodExtent`|`win:UInt8`|<span data-ttu-id="1f131-528">可編譯之方法的範圍。</span><span class="sxs-lookup"><span data-stu-id="1f131-528">The extent for the jitted method.</span></span>|
|`CountOfMapEntries`|`win:UInt8`|<span data-ttu-id="1f131-529">對應專案的數目</span><span class="sxs-lookup"><span data-stu-id="1f131-529">Number of map entries</span></span>|
|`ILOffsets`|`win:UInt32`|<span data-ttu-id="1f131-530">IL 位移。</span><span class="sxs-lookup"><span data-stu-id="1f131-530">The IL offset.</span></span>|
|`NativeOffsets`|`win:UInt32`|<span data-ttu-id="1f131-531">機器碼位移。</span><span class="sxs-lookup"><span data-stu-id="1f131-531">The native code offset.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f131-532">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f131-532">Unique ID for the instance of CoreCLR.</span></span>|
