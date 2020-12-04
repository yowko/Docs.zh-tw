---
title: 載入器和系結器運行時間事件
description: 請參閱收集載入器的特定診斷資訊和系結器 ETW 事件的 .NET 運行時間事件，這些事件會收集組件載入器和系結器的相關資訊。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586657"
---
# <a name="net-runtime-loader-and-binder-events"></a><span data-ttu-id="723cd-103">.NET 執行時間載入器和系結器事件</span><span class="sxs-lookup"><span data-stu-id="723cd-103">.NET runtime loader and binder events</span></span>

<span data-ttu-id="723cd-104">這些事件會收集載入和卸載元件和模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="723cd-104">These events collect information relating to loading and unloading assemblies and modules.</span></span> <span data-ttu-id="723cd-105">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="723cd-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

|<span data-ttu-id="723cd-106">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-106">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-107">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-107">Event</span></span>|<span data-ttu-id="723cd-108">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-108">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-109">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-109">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-110">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-110">Informational (4)</span></span>|

|<span data-ttu-id="723cd-111">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-111">Event</span></span>|<span data-ttu-id="723cd-112">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-112">Event ID</span></span>|<span data-ttu-id="723cd-113">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-113">Description</span></span>|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-114">151</span><span class="sxs-lookup"><span data-stu-id="723cd-114">151</span></span>|<span data-ttu-id="723cd-115">針對應用程式定義域載入模組時引發。</span><span class="sxs-lookup"><span data-stu-id="723cd-115">Raised when a module is loaded for an application domain.</span></span>|

## <a name="moduleload_v2-event"></a><span data-ttu-id="723cd-116">ModuleLoad_V2 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-116">ModuleLoad_V2 event</span></span>

|<span data-ttu-id="723cd-117">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-117">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-118">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-118">Event</span></span>|<span data-ttu-id="723cd-119">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-119">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-120">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-120">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-121">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-121">Informational (4)</span></span>|

|<span data-ttu-id="723cd-122">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-122">Event</span></span>|<span data-ttu-id="723cd-123">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-123">Event ID</span></span>|<span data-ttu-id="723cd-124">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-124">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|<span data-ttu-id="723cd-125">152</span><span class="sxs-lookup"><span data-stu-id="723cd-125">152</span></span>|<span data-ttu-id="723cd-126">在處理序的存留期間載入模組時引發。</span><span class="sxs-lookup"><span data-stu-id="723cd-126">Raised when a module is loaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="723cd-127">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-127">Field name</span></span>|<span data-ttu-id="723cd-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-128">Data type</span></span>|<span data-ttu-id="723cd-129">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-129">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="723cd-130">模組的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-130">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-131">這個模組所在之組件的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-131">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="723cd-132">0x1：定義域中性模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-132">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="723cd-133">0x2：模組具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-133">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-134">0x4：動態模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-134">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="723cd-135">0x8：資訊清單模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-135">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="723cd-136">保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="723cd-136">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="723cd-137">模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。</span><span class="sxs-lookup"><span data-stu-id="723cd-137">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="723cd-138">模組原生映像的路徑 (如果存在的話 (以 Null 終止))。</span><span class="sxs-lookup"><span data-stu-id="723cd-138">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-139">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="723cd-140">符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。</span><span class="sxs-lookup"><span data-stu-id="723cd-140">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="723cd-141">寫入至受管理 PDB 並符合此模組的保留時間數值。</span><span class="sxs-lookup"><span data-stu-id="723cd-141">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-142">符合此模組之受管理 PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-142">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="723cd-143">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-143">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="723cd-144">符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-144">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="723cd-145">寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-145">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-146">符合此模組之 NGen PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-146">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="723cd-147">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-147">In some cases, this may just be a file name.</span></span>|

## <a name="moduleunload_v2-event"></a><span data-ttu-id="723cd-148">ModuleUnload_V2 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-148">ModuleUnload_V2 event</span></span>

|<span data-ttu-id="723cd-149">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-149">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-150">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-150">Event</span></span>|<span data-ttu-id="723cd-151">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-151">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-152">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-152">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-153">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-153">Informational (4)</span></span>|

|<span data-ttu-id="723cd-154">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-154">Event</span></span>|<span data-ttu-id="723cd-155">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-155">Event ID</span></span>|<span data-ttu-id="723cd-156">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-156">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|<span data-ttu-id="723cd-157">153</span><span class="sxs-lookup"><span data-stu-id="723cd-157">153</span></span>|<span data-ttu-id="723cd-158">在處理序的存留期間卸載模組時引發。</span><span class="sxs-lookup"><span data-stu-id="723cd-158">Raised when a module is unloaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="723cd-159">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-159">Field name</span></span>|<span data-ttu-id="723cd-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-160">Data type</span></span>|<span data-ttu-id="723cd-161">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-161">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="723cd-162">模組的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-162">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-163">這個模組所在之組件的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-163">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="723cd-164">0x1：定義域中性模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-164">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="723cd-165">0x2：模組具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-165">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-166">0x4：動態模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-166">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="723cd-167">0x8：資訊清單模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-167">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="723cd-168">保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="723cd-168">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="723cd-169">模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。</span><span class="sxs-lookup"><span data-stu-id="723cd-169">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="723cd-170">模組原生映像的路徑 (如果存在的話 (以 Null 終止))。</span><span class="sxs-lookup"><span data-stu-id="723cd-170">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|``win:UInt16``|<span data-ttu-id="723cd-171">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-171">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="723cd-172">符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。</span><span class="sxs-lookup"><span data-stu-id="723cd-172">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="723cd-173">寫入至受管理 PDB 並符合此模組的保留時間數值。</span><span class="sxs-lookup"><span data-stu-id="723cd-173">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-174">符合此模組之受管理 PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-174">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="723cd-175">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-175">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="723cd-176">符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-176">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="723cd-177">寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-177">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-178">符合此模組之 NGen PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-178">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="723cd-179">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-179">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcstart_v2-event"></a><span data-ttu-id="723cd-180">ModuleDCStart_V2 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-180">ModuleDCStart_V2 event</span></span>

|<span data-ttu-id="723cd-181">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-181">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-182">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-182">Event</span></span>|<span data-ttu-id="723cd-183">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-183">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-184">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-184">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-185">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-185">Informational (4)</span></span>

|<span data-ttu-id="723cd-186">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-186">Event</span></span>|<span data-ttu-id="723cd-187">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-187">Event ID</span></span>|<span data-ttu-id="723cd-188">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-188">Description</span></span>
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|<span data-ttu-id="723cd-189">153</span><span class="sxs-lookup"><span data-stu-id="723cd-189">153</span></span>|<span data-ttu-id="723cd-190">在開始取消期間列舉模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-190">Enumerates modules during a start rundown.</span></span>|

|<span data-ttu-id="723cd-191">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-191">Field name</span></span>|<span data-ttu-id="723cd-192">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-192">Data type</span></span>|<span data-ttu-id="723cd-193">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-193">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="723cd-194">模組的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-194">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-195">這個模組所在之組件的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-195">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="723cd-196">0x1：定義域中性模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-196">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="723cd-197">0x2：模組具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-197">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-198">0x4：動態模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-198">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="723cd-199">0x8：資訊清單模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-199">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="723cd-200">保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="723cd-200">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="723cd-201">模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。</span><span class="sxs-lookup"><span data-stu-id="723cd-201">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="723cd-202">模組原生映像的路徑 (如果存在的話 (以 Null 終止))。</span><span class="sxs-lookup"><span data-stu-id="723cd-202">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-203">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="723cd-204">符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。</span><span class="sxs-lookup"><span data-stu-id="723cd-204">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="723cd-205">寫入至受管理 PDB 並符合此模組的保留時間數值。</span><span class="sxs-lookup"><span data-stu-id="723cd-205">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-206">符合此模組之受管理 PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-206">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="723cd-207">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-207">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="723cd-208">符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-208">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="723cd-209">寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-209">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-210">符合此模組之 NGen PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-210">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="723cd-211">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-211">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcend_v2-event"></a><span data-ttu-id="723cd-212">ModuleDCEnd_V2 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-212">ModuleDCEnd_V2 event</span></span>

|<span data-ttu-id="723cd-213">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-213">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-214">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-214">Event</span></span>|<span data-ttu-id="723cd-215">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-215">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-216">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-216">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-217">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-217">Informational (4)</span></span>|

|<span data-ttu-id="723cd-218">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-218">Event</span></span>|<span data-ttu-id="723cd-219">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-219">Event ID</span></span>|<span data-ttu-id="723cd-220">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-220">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|<span data-ttu-id="723cd-221">154</span><span class="sxs-lookup"><span data-stu-id="723cd-221">154</span></span>|<span data-ttu-id="723cd-222">在結束取消期間列舉模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-222">Enumerates modules during an end rundown.</span></span>|

|<span data-ttu-id="723cd-223">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-223">Field name</span></span>|<span data-ttu-id="723cd-224">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-224">Data type</span></span>|<span data-ttu-id="723cd-225">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-225">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="723cd-226">模組的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-226">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-227">這個模組所在之組件的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-227">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="723cd-228">0x1：定義域中性模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-228">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="723cd-229">0x2：模組具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-229">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-230">0x4：動態模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-230">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="723cd-231">0x8：資訊清單模組。</span><span class="sxs-lookup"><span data-stu-id="723cd-231">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="723cd-232">保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="723cd-232">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="723cd-233">模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。</span><span class="sxs-lookup"><span data-stu-id="723cd-233">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="723cd-234">模組原生映像的路徑 (如果存在的話 (以 Null 終止))。</span><span class="sxs-lookup"><span data-stu-id="723cd-234">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-235">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="723cd-236">符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。</span><span class="sxs-lookup"><span data-stu-id="723cd-236">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="723cd-237">寫入至受管理 PDB 並符合此模組的保留時間數值。</span><span class="sxs-lookup"><span data-stu-id="723cd-237">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-238">符合此模組之受管理 PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-238">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="723cd-239">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-239">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="723cd-240">符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-240">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="723cd-241">寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="723cd-241">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="723cd-242">符合此模組之 NGen PDB 建立位置的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-242">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="723cd-243">在某些情況下，這可能只是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-243">In some cases, this may just be a file name.</span></span>|

## <a name="assemblyload_v1-event"></a><span data-ttu-id="723cd-244">AssemblyLoad_V1 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-244">AssemblyLoad_V1 event</span></span>

|<span data-ttu-id="723cd-245">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-245">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-246">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-246">Event</span></span>|<span data-ttu-id="723cd-247">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-247">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-248">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-248">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-249">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-249">Informational (4)</span></span>|

|<span data-ttu-id="723cd-250">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-250">Event</span></span>|<span data-ttu-id="723cd-251">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-251">Event ID</span></span>|<span data-ttu-id="723cd-252">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-252">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|<span data-ttu-id="723cd-253">154</span><span class="sxs-lookup"><span data-stu-id="723cd-253">154</span></span>|<span data-ttu-id="723cd-254">載入組件時引發。</span><span class="sxs-lookup"><span data-stu-id="723cd-254">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="723cd-255">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-255">Field name</span></span>|<span data-ttu-id="723cd-256">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-256">Data type</span></span>|<span data-ttu-id="723cd-257">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-257">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-258">組件的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-258">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="723cd-259">這個組件之定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-259">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="723cd-260">可唯一識別組件繫結的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-260">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="723cd-261">0x1：定義域中性組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-261">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="723cd-262">0x2：動態組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-262">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="723cd-263">0x4：組件具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-263">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-264">0x8：可回收組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-264">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-265">完整的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-265">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-266">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-266">Unique ID for the instance of CoreCLR.</span></span>

## <a name="assemblyunload_v1-event"></a><span data-ttu-id="723cd-267">AssemblyUnload_V1 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-267">AssemblyUnload_V1 event</span></span>

|<span data-ttu-id="723cd-268">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-268">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-269">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-269">Event</span></span>|<span data-ttu-id="723cd-270">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-270">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-271">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-271">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-272">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-272">Informational (4)</span></span>|

|<span data-ttu-id="723cd-273">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-273">Event</span></span>|<span data-ttu-id="723cd-274">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-274">Event ID</span></span>|<span data-ttu-id="723cd-275">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-275">Description</span></span>|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|<span data-ttu-id="723cd-276">155</span><span class="sxs-lookup"><span data-stu-id="723cd-276">155</span></span>|<span data-ttu-id="723cd-277">載入組件時引發。</span><span class="sxs-lookup"><span data-stu-id="723cd-277">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="723cd-278">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-278">Field name</span></span>|<span data-ttu-id="723cd-279">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-279">Data type</span></span>|<span data-ttu-id="723cd-280">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-280">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-281">組件的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-281">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="723cd-282">這個組件之定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-282">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="723cd-283">可唯一識別組件繫結的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-283">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="723cd-284">0x1：定義域中性組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-284">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="723cd-285">0x2：動態組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-285">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="723cd-286">0x4：組件具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-286">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-287">0x8：可回收組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-287">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-288">完整的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-288">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-289">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-289">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblydcstart_v1-event"></a><span data-ttu-id="723cd-290">AssemblyDCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-290">AssemblyDCStart_V1 event</span></span>

|<span data-ttu-id="723cd-291">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-291">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-292">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-292">Event</span></span>|<span data-ttu-id="723cd-293">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-293">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-294">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="723cd-294">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="723cd-295">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-295">Informational (4)</span></span>|

|<span data-ttu-id="723cd-296">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-296">Event</span></span>|<span data-ttu-id="723cd-297">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-297">Event ID</span></span>|<span data-ttu-id="723cd-298">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-298">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|<span data-ttu-id="723cd-299">155</span><span class="sxs-lookup"><span data-stu-id="723cd-299">155</span></span>|<span data-ttu-id="723cd-300">在開始取消期間列舉組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-300">Enumerates assemblies during a start rundown.</span></span>|

|<span data-ttu-id="723cd-301">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-301">Field name</span></span>|<span data-ttu-id="723cd-302">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-302">Data type</span></span>|<span data-ttu-id="723cd-303">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-303">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="723cd-304">組件的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-304">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="723cd-305">這個組件之定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-305">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="723cd-306">可唯一識別組件繫結的 ID。</span><span class="sxs-lookup"><span data-stu-id="723cd-306">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="723cd-307">0x1：定義域中性組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-307">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="723cd-308">0x2：動態組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-308">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="723cd-309">0x4：組件具有原生映像。</span><span class="sxs-lookup"><span data-stu-id="723cd-309">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="723cd-310">0x8：可回收組件。</span><span class="sxs-lookup"><span data-stu-id="723cd-310">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-311">完整的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-311">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-312">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-312">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstart-event"></a><span data-ttu-id="723cd-313">AssemblyLoadStart 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-313">AssemblyLoadStart event</span></span>

|<span data-ttu-id="723cd-314">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-314">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-315">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-315">Event</span></span>|<span data-ttu-id="723cd-316">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-316">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-317">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-317">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="723cd-318">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-318">Informational (4)</span></span>|

|<span data-ttu-id="723cd-319">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-319">Event</span></span>|<span data-ttu-id="723cd-320">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-320">Event ID</span></span>|<span data-ttu-id="723cd-321">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-321">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="723cd-322">290</span><span class="sxs-lookup"><span data-stu-id="723cd-322">290</span></span>|<span data-ttu-id="723cd-323">已要求元件載入。</span><span class="sxs-lookup"><span data-stu-id="723cd-323">An assembly load has been requested.</span></span>

|<span data-ttu-id="723cd-324">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-324">Field name</span></span>|<span data-ttu-id="723cd-325">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-325">Data type</span></span>|<span data-ttu-id="723cd-326">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-326">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-327">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-327">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-328">元件名稱的路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-328">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="723cd-329">要求 ( "parent" ) 元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-329">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-330">載入元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-330">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-331">載入要求 ( "parent" ) 元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-331">Load context of the requesting ("parent") assembly.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-332">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-332">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstop-event"></a><span data-ttu-id="723cd-333">AssemblyLoadStop 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-333">AssemblyLoadStop event</span></span>

|<span data-ttu-id="723cd-334">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-334">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-335">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-335">Event</span></span>|<span data-ttu-id="723cd-336">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-336">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-337">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-337">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="723cd-338">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-338">Informational (4)</span></span>|

|<span data-ttu-id="723cd-339">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-339">Event</span></span>|<span data-ttu-id="723cd-340">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-340">Event ID</span></span>|<span data-ttu-id="723cd-341">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-341">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="723cd-342">291</span><span class="sxs-lookup"><span data-stu-id="723cd-342">291</span></span>|<span data-ttu-id="723cd-343">已要求元件載入。</span><span class="sxs-lookup"><span data-stu-id="723cd-343">An assembly load has been requested.</span></span>

|<span data-ttu-id="723cd-344">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-344">Field name</span></span>|<span data-ttu-id="723cd-345">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-345">Data type</span></span>|<span data-ttu-id="723cd-346">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-346">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-347">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-347">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-348">元件名稱的路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-348">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="723cd-349">要求 ( "parent" ) 元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-349">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-350">載入元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-350">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-351">載入要求 ( "parent" ) 元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-351">Load context of the requesting ("parent") assembly.</span></span>|
|`Success`|`win:Boolean`|<span data-ttu-id="723cd-352">元件載入是否成功。</span><span class="sxs-lookup"><span data-stu-id="723cd-352">Whether the assembly load succeeded.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-353">載入的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-353">The name of assembly that was loaded.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-354">從載入的元件路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-354">The path of the assembly that was loaded from.</span></span>|
|`Cached`|`win:UnicodeString`|<span data-ttu-id="723cd-355">是否快取負載。</span><span class="sxs-lookup"><span data-stu-id="723cd-355">Whether the load was cached.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-356">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-356">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="resolutionattempted-event"></a><span data-ttu-id="723cd-357">ResolutionAttempted 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-357">ResolutionAttempted event</span></span>

|<span data-ttu-id="723cd-358">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-358">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-359">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-359">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-360">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-360">`Binder` (0x4)</span></span>|<span data-ttu-id="723cd-361">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-361">Informational (4)</span></span>|

|<span data-ttu-id="723cd-362">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-362">Event</span></span>|<span data-ttu-id="723cd-363">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-363">Event ID</span></span>|<span data-ttu-id="723cd-364">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-364">Description</span></span>|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|<span data-ttu-id="723cd-365">292</span><span class="sxs-lookup"><span data-stu-id="723cd-365">292</span></span>|<span data-ttu-id="723cd-366">已要求元件載入。</span><span class="sxs-lookup"><span data-stu-id="723cd-366">An assembly load has been requested.</span></span>

|<span data-ttu-id="723cd-367">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-367">Field name</span></span>|<span data-ttu-id="723cd-368">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-368">Data type</span></span>|<span data-ttu-id="723cd-369">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-369">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-370">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-370">Name of assembly name.</span></span>|
|`Stage`|`win:UInt16`|<span data-ttu-id="723cd-371">解決階段。</span><span class="sxs-lookup"><span data-stu-id="723cd-371">The resolution stage.</span></span><br/><br/><span data-ttu-id="723cd-372">0：在載入中尋找。</span><span class="sxs-lookup"><span data-stu-id="723cd-372">0: Find in load.</span></span><br/><br/><span data-ttu-id="723cd-373">1：元件載入內容</span><span class="sxs-lookup"><span data-stu-id="723cd-373">1: Assembly Load Context</span></span></br><br/><span data-ttu-id="723cd-374">2：應用程式元件。</span><span class="sxs-lookup"><span data-stu-id="723cd-374">2: Application assemblies.</span></span><br/><br/><span data-ttu-id="723cd-375">3：預設元件載入內容回退。</span><span class="sxs-lookup"><span data-stu-id="723cd-375">3: Default assembly load context fallback.</span></span> <br/><br/><span data-ttu-id="723cd-376">4：解析附屬元件。</span><span class="sxs-lookup"><span data-stu-id="723cd-376">4: Resolve satellite assembly.</span></span> <br/><br/><span data-ttu-id="723cd-377">5：元件載入內容解析。</span><span class="sxs-lookup"><span data-stu-id="723cd-377">5: Assembly load context resolving.</span></span><br/><br/><span data-ttu-id="723cd-378">6： AppDomain 元件解析。</span><span class="sxs-lookup"><span data-stu-id="723cd-378">6: AppDomain assembly resolving.</span></span>
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-379">載入元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-379">Load context of the assembly.</span></span>|
|`Result`|`win:UInt16`|<span data-ttu-id="723cd-380">解析嘗試的結果。</span><span class="sxs-lookup"><span data-stu-id="723cd-380">The result of resolution attempt.</span></span><br/><br/><span data-ttu-id="723cd-381">0：成功</span><span class="sxs-lookup"><span data-stu-id="723cd-381">0: Success</span></span><br/><br/><span data-ttu-id="723cd-382">1：元件 NotFound</span><span class="sxs-lookup"><span data-stu-id="723cd-382">1: Assembly NotFound</span></span><br/><br/><span data-ttu-id="723cd-383">2：不相容的版本</span><span class="sxs-lookup"><span data-stu-id="723cd-383">2: Incompatible Version</span></span><br/><br/><span data-ttu-id="723cd-384">3：不相符的元件名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-384">3: Mismatched Assembly Name</span></span><br/><br/><span data-ttu-id="723cd-385">4：失敗</span><span class="sxs-lookup"><span data-stu-id="723cd-385">4: Failure</span></span><br/><br/><span data-ttu-id="723cd-386">5：例外狀況</span><span class="sxs-lookup"><span data-stu-id="723cd-386">5: Exception</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-387">已解析的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-387">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-388">從中解析的元件路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-388">The path of the assembly that was resolved from.</span></span>|
|`ErrorMessage`|`win:UnicodeString`|<span data-ttu-id="723cd-389">如果發生例外狀況，則為錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="723cd-389">Error message if there is an exception.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-390">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-390">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a><span data-ttu-id="723cd-391">AssemblyLoadCoNtextResolvingHandlerInvoked 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-391">AssemblyLoadContextResolvingHandlerInvoked event</span></span>

|<span data-ttu-id="723cd-392">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-392">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-393">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-393">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-394">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-394">`Binder` (0x4)</span></span>|<span data-ttu-id="723cd-395">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-395">Informational (4)</span></span>|

|<span data-ttu-id="723cd-396">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-396">Event</span></span>|<span data-ttu-id="723cd-397">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-397">Event ID</span></span>|<span data-ttu-id="723cd-398">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-398">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|<span data-ttu-id="723cd-399">293</span><span class="sxs-lookup"><span data-stu-id="723cd-399">293</span></span>|<span data-ttu-id="723cd-400">已叫用 [AssemblyLoadCoNtext 解析](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) 處理常式。</span><span class="sxs-lookup"><span data-stu-id="723cd-400">An [AssemblyLoadContext.Resolving](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) handler has been invoked.</span></span>|

|<span data-ttu-id="723cd-401">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-401">Field name</span></span>|<span data-ttu-id="723cd-402">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-402">Data type</span></span>|<span data-ttu-id="723cd-403">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-403">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-404">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-404">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="723cd-405">叫用的處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-405">Name of the handler invoked.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="723cd-406">載入元件的內容。</span><span class="sxs-lookup"><span data-stu-id="723cd-406">Load context of the assembly.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-407">已解析的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-407">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-408">從中解析的元件路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-408">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-409">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-409">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a><span data-ttu-id="723cd-410">AppDomainAssemblyResolveHandlerInvoked 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-410">AppDomainAssemblyResolveHandlerInvoked event</span></span>

|<span data-ttu-id="723cd-411">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-411">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-412">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-412">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-413">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-413">`Binder` (0x4)</span></span>|<span data-ttu-id="723cd-414">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-414">Informational (4)</span></span>|

|<span data-ttu-id="723cd-415">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-415">Event</span></span>|<span data-ttu-id="723cd-416">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-416">Event ID</span></span>|<span data-ttu-id="723cd-417">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-417">Description</span></span>|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|<span data-ttu-id="723cd-418">294</span><span class="sxs-lookup"><span data-stu-id="723cd-418">294</span></span>|<span data-ttu-id="723cd-419">已叫用 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 處理常式。</span><span class="sxs-lookup"><span data-stu-id="723cd-419">An <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="723cd-420">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-420">Field name</span></span>|<span data-ttu-id="723cd-421">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-421">Data type</span></span>|<span data-ttu-id="723cd-422">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-422">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-423">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-423">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="723cd-424">叫用的處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-424">Name of the handler invoked.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-425">已解析的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-425">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-426">從中解析的元件路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-426">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-427">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-427">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a><span data-ttu-id="723cd-428">AssemblyLoadFromResolveHandlerInvoked 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-428">AssemblyLoadFromResolveHandlerInvoked event</span></span>

|<span data-ttu-id="723cd-429">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-429">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-430">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-430">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-431">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-431">`Binder` (0x4)</span></span>|<span data-ttu-id="723cd-432">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-432">Informational (4)</span></span>|

|<span data-ttu-id="723cd-433">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-433">Event</span></span>|<span data-ttu-id="723cd-434">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-434">Event ID</span></span>|<span data-ttu-id="723cd-435">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-435">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|<span data-ttu-id="723cd-436">295</span><span class="sxs-lookup"><span data-stu-id="723cd-436">295</span></span>|<span data-ttu-id="723cd-437">已叫用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 處理常式。</span><span class="sxs-lookup"><span data-stu-id="723cd-437">An <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="723cd-438">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-438">Field name</span></span>|<span data-ttu-id="723cd-439">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-439">Data type</span></span>|<span data-ttu-id="723cd-440">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-440">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="723cd-441">元件名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="723cd-441">Name of assembly name.</span></span>|
|`IsTrackedLoad`|`win:Boolean`|<span data-ttu-id="723cd-442">是否追蹤元件載入。</span><span class="sxs-lookup"><span data-stu-id="723cd-442">Whether the assembly load is tracked.</span></span>|
|`RequestingAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-443">要求元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-443">The path of the requesting assembly.</span></span>|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="723cd-444">所要求元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-444">The path of the assembly that was requested.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-445">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-445">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="knownpathprobed-event"></a><span data-ttu-id="723cd-446">KnownPathProbed 事件</span><span class="sxs-lookup"><span data-stu-id="723cd-446">KnownPathProbed event</span></span>

|<span data-ttu-id="723cd-447">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="723cd-447">Keyword for raising the event</span></span>|<span data-ttu-id="723cd-448">層級</span><span class="sxs-lookup"><span data-stu-id="723cd-448">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="723cd-449">`Binder` (0x4) </span><span class="sxs-lookup"><span data-stu-id="723cd-449">`Binder` (0x4)</span></span>|<span data-ttu-id="723cd-450">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="723cd-450">Informational (4)</span></span>|

|<span data-ttu-id="723cd-451">事件</span><span class="sxs-lookup"><span data-stu-id="723cd-451">Event</span></span>|<span data-ttu-id="723cd-452">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="723cd-452">Event ID</span></span>|<span data-ttu-id="723cd-453">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-453">Description</span></span>|
|-----------|--------------|-----------------|
|`KnownPathProbed`|<span data-ttu-id="723cd-454">296</span><span class="sxs-lookup"><span data-stu-id="723cd-454">296</span></span>|<span data-ttu-id="723cd-455">探查元件的已知路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-455">A known path was probed for an assembly.</span></span>|

|<span data-ttu-id="723cd-456">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="723cd-456">Field Name</span></span>|<span data-ttu-id="723cd-457">資料類型</span><span class="sxs-lookup"><span data-stu-id="723cd-457">Data Type</span></span>|<span data-ttu-id="723cd-458">描述</span><span class="sxs-lookup"><span data-stu-id="723cd-458">Description</span></span>|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|<span data-ttu-id="723cd-459">探查的路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-459">Path probed.</span></span>|
|`Source`|`win:UInt16`|<span data-ttu-id="723cd-460">探查之路徑的來源。</span><span class="sxs-lookup"><span data-stu-id="723cd-460">Source of the path probed.</span></span><br/><br/><span data-ttu-id="723cd-461">0x0：應用程式元件。</span><span class="sxs-lookup"><span data-stu-id="723cd-461">0x0:Application Assemblies.</span></span><br/><br/><span data-ttu-id="723cd-462">0x1：應用程式原生映射路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-462">0x1:App native image path.</span></span><br/><br/><span data-ttu-id="723cd-463">0x2：應用程式路徑。</span><span class="sxs-lookup"><span data-stu-id="723cd-463">0x2:App path.</span></span></br><br/><span data-ttu-id="723cd-464">0x3：平臺資源根目錄。</span><span class="sxs-lookup"><span data-stu-id="723cd-464">0x3:Platform resource roots.</span></span><br/><br/><span data-ttu-id="723cd-465">0x4：附屬子目錄。</span><span class="sxs-lookup"><span data-stu-id="723cd-465">0x4:Satellite Subdirectory.</span></span></br>|
|`Result`|`win:UInt32`|<span data-ttu-id="723cd-466">探查的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="723cd-466">HRESULT for the probe.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="723cd-467">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="723cd-467">Unique ID for the instance of CoreCLR.</span></span>|
