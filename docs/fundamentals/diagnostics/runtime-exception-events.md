---
title: 例外狀況運行時間事件
description: 請參閱收集例外狀況和例外狀況處理特定診斷資訊的 .NET 運行時間事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586655"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="2cb56-103">.NET 執行時間例外狀況事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-103">.NET runtime exception events</span></span>

<span data-ttu-id="2cb56-104">這些運行時間事件會捕捉擲回之例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="2cb56-105">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="2cb56-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="2cb56-106">ExceptionThrown_V1 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="2cb56-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-107">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-108">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-110">錯誤 (1)</span><span class="sxs-lookup"><span data-stu-id="2cb56-110">Error (1)</span></span>|

 <span data-ttu-id="2cb56-111">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-111">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-112">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-112">Event</span></span>|<span data-ttu-id="2cb56-113">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-113">Event ID</span></span>|<span data-ttu-id="2cb56-114">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="2cb56-115">80</span><span class="sxs-lookup"><span data-stu-id="2cb56-115">80</span></span>|<span data-ttu-id="2cb56-116">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2cb56-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="2cb56-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2cb56-117">Field name</span></span>|<span data-ttu-id="2cb56-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="2cb56-118">Data type</span></span>|<span data-ttu-id="2cb56-119">描述</span><span class="sxs-lookup"><span data-stu-id="2cb56-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="2cb56-120">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="2cb56-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="2cb56-121">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="2cb56-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="2cb56-122">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="2cb56-123">例外狀況 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="2cb56-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="2cb56-124">`0x01`: HasInnerException.</span><span class="sxs-lookup"><span data-stu-id="2cb56-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="2cb56-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="2cb56-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="2cb56-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="2cb56-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="2cb56-127">`0x08`： IsCorruptedStateException (表示進程狀態已損毀;請參閱 [處理損毀狀態例外狀況](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)) 。</span><span class="sxs-lookup"><span data-stu-id="2cb56-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="2cb56-128">`0x10`： IsCLSCompliant (衍生自的例外狀況 <xref:System.Exception> 符合 cls 標準，否則為不符合 cls 標準的) 。</span><span class="sxs-lookup"><span data-stu-id="2cb56-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2cb56-129">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="2cb56-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="2cb56-130">ExceptionCatchStart 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="2cb56-131">當 managed 例外狀況 catch 處理常式開始時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="2cb56-132">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-132">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-133">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-135">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-135">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-136">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-136">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-137">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-137">Event</span></span>|<span data-ttu-id="2cb56-138">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-138">Event ID</span></span>|<span data-ttu-id="2cb56-139">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="2cb56-140">250</span><span class="sxs-lookup"><span data-stu-id="2cb56-140">250</span></span>|<span data-ttu-id="2cb56-141">Managed 例外狀況是由執行時間處理。</span><span class="sxs-lookup"><span data-stu-id="2cb56-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="2cb56-142">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2cb56-142">Field name</span></span>|<span data-ttu-id="2cb56-143">資料類型</span><span class="sxs-lookup"><span data-stu-id="2cb56-143">Data type</span></span>|<span data-ttu-id="2cb56-144">描述</span><span class="sxs-lookup"><span data-stu-id="2cb56-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="2cb56-145">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="2cb56-146">發生例外狀況之方法上的方法描述元指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2cb56-147">發生例外狀況之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cb56-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2cb56-148">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="2cb56-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="2cb56-149">ExceptionCatchStop 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="2cb56-150">當 managed 例外狀況 catch 處理常式結束時，就會發出這個事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="2cb56-151">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-151">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-152">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-154">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-154">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-155">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-155">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-156">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-156">Event</span></span>|<span data-ttu-id="2cb56-157">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-157">Event ID</span></span>|<span data-ttu-id="2cb56-158">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="2cb56-159">251</span><span class="sxs-lookup"><span data-stu-id="2cb56-159">251</span></span>|<span data-ttu-id="2cb56-160">Managed 例外狀況 catch 處理常式已完成。</span><span class="sxs-lookup"><span data-stu-id="2cb56-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="2cb56-161">ExceptionFinallyStart 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="2cb56-162">當 managed 例外狀況的處理常式開始時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="2cb56-163">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-163">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-164">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-166">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-166">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-167">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-167">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-168">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-168">Event</span></span>|<span data-ttu-id="2cb56-169">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-169">Event ID</span></span>|<span data-ttu-id="2cb56-170">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="2cb56-171">252</span><span class="sxs-lookup"><span data-stu-id="2cb56-171">252</span></span>|<span data-ttu-id="2cb56-172">Managed 例外狀況是由執行時間處理。</span><span class="sxs-lookup"><span data-stu-id="2cb56-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="2cb56-173">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2cb56-173">Field name</span></span>|<span data-ttu-id="2cb56-174">資料類型</span><span class="sxs-lookup"><span data-stu-id="2cb56-174">Data type</span></span>|<span data-ttu-id="2cb56-175">描述</span><span class="sxs-lookup"><span data-stu-id="2cb56-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="2cb56-176">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="2cb56-177">發生例外狀況之方法上的方法描述元指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2cb56-178">發生例外狀況之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cb56-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2cb56-179">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="2cb56-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="2cb56-180">ExceptionFinallyStop 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="2cb56-181">當 managed 例外狀況 catch 處理常式結束時，就會發出這個事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="2cb56-182">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-182">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-183">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-185">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-185">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-186">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-186">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-187">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-187">Event</span></span>|<span data-ttu-id="2cb56-188">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-188">Event ID</span></span>|<span data-ttu-id="2cb56-189">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="2cb56-190">253</span><span class="sxs-lookup"><span data-stu-id="2cb56-190">253</span></span>|<span data-ttu-id="2cb56-191">Managed 例外狀況 finally 處理常式已完成。</span><span class="sxs-lookup"><span data-stu-id="2cb56-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="2cb56-192">ExceptionFilterStart 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="2cb56-193">當 managed 例外狀況篩選開始時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="2cb56-194">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-194">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-195">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-197">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-197">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-198">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-198">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-199">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-199">Event</span></span>|<span data-ttu-id="2cb56-200">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-200">Event ID</span></span>|<span data-ttu-id="2cb56-201">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="2cb56-202">254</span><span class="sxs-lookup"><span data-stu-id="2cb56-202">254</span></span>|<span data-ttu-id="2cb56-203">Managed 例外狀況篩選會開始。</span><span class="sxs-lookup"><span data-stu-id="2cb56-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="2cb56-204">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2cb56-204">Field name</span></span>|<span data-ttu-id="2cb56-205">資料類型</span><span class="sxs-lookup"><span data-stu-id="2cb56-205">Data type</span></span>|<span data-ttu-id="2cb56-206">描述</span><span class="sxs-lookup"><span data-stu-id="2cb56-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="2cb56-207">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="2cb56-208">發生例外狀況之方法上的方法描述元指標。</span><span class="sxs-lookup"><span data-stu-id="2cb56-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="2cb56-209">發生例外狀況之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cb56-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2cb56-210">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2cb56-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="2cb56-211">ExceptionFilterStop 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="2cb56-212">Managed 例外狀況篩選結束時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="2cb56-213">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-213">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-214">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-216">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-216">Informational (4)</span></span>|

 <span data-ttu-id="2cb56-217">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-217">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-218">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-218">Event</span></span>|<span data-ttu-id="2cb56-219">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-219">Event ID</span></span>|<span data-ttu-id="2cb56-220">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="2cb56-221">255</span><span class="sxs-lookup"><span data-stu-id="2cb56-221">255</span></span>|<span data-ttu-id="2cb56-222">Managed 例外狀況篩選會結束。</span><span class="sxs-lookup"><span data-stu-id="2cb56-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="2cb56-223">ExceptionThrownStop 事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="2cb56-224">當執行時間完成處理所擲回的 managed 例外狀況時，就會發出這個事件。</span><span class="sxs-lookup"><span data-stu-id="2cb56-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="2cb56-225">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb56-225">Keyword for raising the event</span></span>|<span data-ttu-id="2cb56-226">層級</span><span class="sxs-lookup"><span data-stu-id="2cb56-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2cb56-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="2cb56-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="2cb56-228">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="2cb56-228">Informational (4)</span></span>|
  
 <span data-ttu-id="2cb56-229">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb56-229">The following table shows event information.</span></span>

|<span data-ttu-id="2cb56-230">事件</span><span class="sxs-lookup"><span data-stu-id="2cb56-230">Event</span></span>|<span data-ttu-id="2cb56-231">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2cb56-231">Event ID</span></span>|<span data-ttu-id="2cb56-232">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2cb56-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="2cb56-233">256</span><span class="sxs-lookup"><span data-stu-id="2cb56-233">256</span></span>|<span data-ttu-id="2cb56-234">Managed 例外狀況篩選會結束。</span><span class="sxs-lookup"><span data-stu-id="2cb56-234">A managed exception filtering ends.</span></span>|
